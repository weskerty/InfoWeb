<style>
.tdl-toolbar{display:flex;flex-wrap:wrap;gap:10px;align-items:center;margin-bottom:10px}
.tdl-toolbar label{display:flex;align-items:center;gap:6px;font-size:.85em;opacity:.9}
.tdl-input{flex:1;min-width:220px}
.tdl-num{width:4.5em}
.tdl-dir-name{opacity:.8;font-size:.9em}
.tdl-gerr{background:rgba(229,57,53,.15);border:1px solid rgba(229,57,53,.4);border-radius:10px;padding:8px 12px;margin-bottom:10px;font-size:.9em}
.tdl-list{display:flex;flex-direction:column;gap:14px}
.tdl-card{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.15);border-radius:16px;padding:14px 16px;backdrop-filter:blur(12px)}
body.low-perf .tdl-card{backdrop-filter:none!important}
.tdl-head{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-bottom:8px}
.tdl-name{overflow:hidden;text-overflow:ellipsis;white-space:nowrap;flex:1}
.tdl-badge{font-size:.75em;opacity:.7;white-space:nowrap}
.tdl-btns{display:flex;gap:4px}
.tdl-btns button{padding:2px 8px}
.tdl-btns [data-act=pause],.tdl-btns [data-act=resume]{display:none}
.tdl-card[data-status=active] [data-act=pause]{display:inline-block}
.tdl-card[data-status=paused] [data-act=resume],.tdl-card[data-status=error] [data-act=resume]{display:inline-block}
.tdl-bar{height:6px;border-radius:4px;background:rgba(255,255,255,.1);overflow:hidden}
.tdl-bar-f{height:100%;width:0%;background:#1a73e8;transition:width .4s ease}
.tdl-card[data-status=done] .tdl-bar-f{background:#35b44f}
.tdl-card[data-status=error] .tdl-bar-f{background:#e53935}
.tdl-card[data-status=paused] .tdl-bar-f{background:#f2a13a}
.tdl-stats{display:flex;gap:14px;flex-wrap:wrap;font-size:.85em;opacity:.85;margin-top:8px}
.tdl-warn{margin-top:8px;font-size:.85em;color:#f2a13a}
.tdl-files{margin-top:10px;display:flex;flex-direction:column;gap:4px;font-size:.9em}
.tdl-file{display:flex;justify-content:space-between;gap:10px;opacity:.85;flex-wrap:wrap;align-items:center}
.tdl-play{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);color:inherit;border-radius:8px;padding:3px 9px;font-size:.85em;cursor:pointer}
.tdl-play:disabled{opacity:.4;cursor:default}
.tdl-player{width:100%;max-height:60vh;margin-top:6px;border-radius:8px;background:#000}
.tdl-perr{width:100%;font-size:.8em;opacity:.7;margin-top:4px}
.tdl-fsz{opacity:.6;white-space:nowrap}
.tdl-dllink{color:#1a73e8;text-decoration:none;font-size:.9em}
.tdl-dllink:hover{text-decoration:underline}
</style>

<div class="tdl-toolbar">
    <input type="text" class="tdl-input" placeholder="Pega un magnet link">
    <button data-act="add">Agregar</button>
    <label>.torrent<input type="file" accept=".torrent" data-act="file" hidden></label>
    <button data-act="pickdir">Elegir carpeta de descarga</button>
    <span class="tdl-dir-name"></span>
</div>
<div class="tdl-toolbar">
    <label>Simultaneas <input type="number" class="tdl-num" data-act="max" value="2" min="1" max="10"></label>
</div>
<div class="tdl-list"></div>

<script>
!function(){
const CDN="https://cdn.jsdelivr.net/npm/webtorrent@3.0.21/dist/webtorrent.min.js";
const FSA="showDirectoryPicker" in window;
const HASWL="wakeLock" in navigator;
const root=document.getElementById("content");
const list=root.querySelector(".tdl-list");
let WT=null,CL=null,DIR=null,WL=null,MAXACT=2,_uid=0;
let SRV=null,SRVNO=false;
const PLAYABLE=/\.(mp4|webm|m4v|mov|mkv|mp3|m4a|ogg|opus|flac|wav)$/i;
const QUEUE=[],PAUSED=[],ACT=new Map();

function esc(s){return (s||"").replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]))}
function nextId(){return String(++_uid)}
function fmtB(n){
    if(!n)return "0 B";
    const u=["B","KB","MB","GB","TB"];
    const i=Math.min(Math.floor(Math.log(n)/Math.log(1024)),u.length-1);
    return (n/Math.pow(1024,i)).toFixed(i?1:0)+" "+u[i];
}
function fmtT(ms){
    if(!ms||ms===Infinity)return "--";
    const s=Math.floor(ms/1000);
    if(s<60)return s+"s";
    if(s<3600)return Math.floor(s/60)+"m "+(s%60)+"s";
    return Math.floor(s/3600)+"h "+Math.floor((s%3600)/60)+"m";
}
function magnetName(m){
    try{return new URLSearchParams(m.split("?")[1]).get("dn")}catch(e){return null}
}

async function loadWT(){
    if(WT)return WT;
    const m=await import(CDN);
    WT=m.default;
    return WT;
}
async function ensureClient(){
    if(CL)return CL;
    await loadWT();
    CL=new WT();
    CL.on("error",err=>{
        showGlobalError(err);
        CL=null;
    });
    return CL;
}
async function ensureServer(){
    if(SRV)return SRV;
    if(SRVNO)return null;
    try{
        if(!("serviceWorker" in navigator)){SRVNO=true;return null;}
        const reg=await navigator.serviceWorker.ready;
        if(!reg||!reg.active){SRVNO=true;return null;}
        const cl=await ensureClient();
        if(!cl){SRVNO=true;return null;}
        SRV=cl.createServer({controller:reg});
        return SRV;
    }catch(e){SRVNO=true;return null;}
}
function liveFile(ih,name){
    if(!CL)return null;
    const t=(CL.torrents||[]).find(x=>x&&!x.destroyed&&x.infoHash===ih);
    if(!t)return null;
    return (t.files||[]).find(f=>f.name===name)||null;
}
function playNow(getF,d,btn,retry){
    const old=d.querySelector(".tdl-player");
    if(old)old.remove();
    const oe=d.querySelector(".tdl-perr");
    if(oe)oe.remove();
    const say=t=>{
        const w=d.querySelector(".tdl-perr")||document.createElement("div");
        w.className="tdl-perr";
        w.textContent=t;
        d.appendChild(w);
    };
    const f=typeof getF==="function"?getF():getF;
    if(!f){
        say("El torrent no esta activo. Reanudalo para reproducir.");
        if(btn)btn.textContent="▶ Reproducir";
        return;
    }
    const isA=/\.(mp3|m4a|ogg|opus|flac|wav)$/i.test(f.name);
    const el=document.createElement(isA?"audio":"video");
    el.controls=true;
    el.className="tdl-player";
    el.addEventListener("loadeddata",()=>{
        const w=d.querySelector(".tdl-perr");
        if(w)w.remove();
    });
    el.addEventListener("error",()=>{
        const c=el.error?el.error.code:0;
        if(c===4){
            say("El navegador no puede reproducir este formato. Se sigue descargando.");
            el.remove();
            if(btn)btn.textContent="▶ Reproducir";
            return;
        }
        if(!retry){
            say("Buscando el inicio del archivo, reintentando...");
            setTimeout(()=>playNow(getF,d,btn,true),4000);
            return;
        }
        say("Todavia no hay suficiente descargado. Proba de nuevo en un rato.");
        el.remove();
        if(btn)btn.textContent="▶ Reproducir";
    });
    d.appendChild(el);
    try{
        f.streamTo(el);
        if(btn)btn.textContent="▶ Reproduciendo";
    }catch(e){
        el.remove();
        say("No se pudo reproducir: "+(e&&e.message||String(e)));
        if(btn)btn.textContent="▶ Reproducir";
    }
}
async function renderFiles(t,fEl){
    fEl.innerHTML="";
    const srv=await ensureServer();
    t.files.forEach(f=>{
        const d=document.createElement("div");
        d.className="tdl-file";
        const nm=document.createElement("span");
        nm.textContent=f.name;
        const sz=document.createElement("span");
        sz.className="tdl-fsz";
        sz.textContent=fmtB(f.length);
        d.append(nm,sz);
        if(srv&&PLAYABLE.test(f.name)){
            const ih=t.infoHash,nm=f.name;
            const b=document.createElement("button");
            b.className="tdl-play";
            b.textContent="▶ Reproducir";
            b.onclick=()=>playNow(()=>liveFile(ih,nm),d,b);
            d.appendChild(b);
        }
        fEl.appendChild(d);
    });
}
function showGlobalError(err){
    const b=document.createElement("div");
    b.className="tdl-gerr";
    b.textContent="Error cliente: "+esc(err&&err.message||String(err));
    list.before(b);
}

function cardHTML(name){
    return `<div class="tdl-head">
<strong class="tdl-name">${esc(name)}</strong>
<span class="tdl-badge">En cola</span>
<div class="tdl-btns">
<button data-act="pause" title="paus">⏸</button>
<button data-act="resume" title="continua">▶</button>
<button data-act="remove" title="x">✕</button>
</div>
</div>
<div class="tdl-bar"><div class="tdl-bar-f"></div></div>
<div class="tdl-stats">
<span class="tdl-p">0%</span>
<span class="tdl-dl">↓ 0 B/s</span>
<span class="tdl-ul">↑ 0 B/s</span>
<span class="tdl-pe">0 peers</span>
<span class="tdl-eta">--</span>
</div>
<div class="tdl-warn" hidden></div>
<div class="tdl-files"></div>`;
}

async function fallbackLinks(torrent,fEl){
    fEl.innerHTML="";
    for(const f of torrent.files){
        const blob=await f.blob();
        const a=document.createElement("a");
        a.href=URL.createObjectURL(blob);
        a.download=f.name;
        a.textContent="Descargar "+f.name+" ("+fmtB(f.length)+")";
        a.className="tdl-dllink";
        fEl.appendChild(a);
    }
}

function activeDownloading(){
    let n=0;
    for(const {torrent} of ACT.values())if(!torrent.done)n++;
    return n;
}
function promote(){
    while(activeDownloading()<MAXACT && QUEUE.length){
        startActive(QUEUE.shift());
    }
    QUEUE.forEach((e,i)=>{
        e.el.querySelector(".tdl-badge").textContent="En cola #"+(i+1);
    });
}
async function wakeSync(){
    if(!HASWL)return;
    const want=activeDownloading()>0;
    if(want && !WL){
        try{
            WL=await navigator.wakeLock.request("screen");
            WL.addEventListener("release",()=>{WL=null});
        }catch(e){}
    }else if(!want && WL){
        await WL.release().catch(()=>{});
        WL=null;
    }
}
document.addEventListener("visibilitychange",()=>{
    if(document.visibilityState==="visible" && activeDownloading()>0 && !WL)wakeSync();
});

async function startActive(entry){
    entry.el.dataset.status="active";
    entry.el.querySelector(".tdl-badge").textContent="Activo";
    try{
        await ensureClient();
    }catch(e){
        entry.el.dataset.status="error";
        entry.el.querySelector(".tdl-badge").textContent="Error";
        const w=entry.el.querySelector(".tdl-warn");
        w.hidden=false;
        w.textContent="No se pudo cargar el motor: "+esc(e&&e.message||String(e));
        return;
    }
    if(!CL)return;
    const opts={};
    if(DIR)opts.storeOpts={rootDir:DIR};
    const torrent=CL.add(entry.source,opts,t=>{
        entry.el.querySelector(".tdl-name").textContent=t.name;
        renderFiles(t,entry.el.querySelector(".tdl-files"));
    });
    const timers=[];
    timers.push(setTimeout(()=>{
        if(!torrent.ready){
            const w=entry.el.querySelector(".tdl-warn");
            w.hidden=false;
            w.textContent="Sin fuentes WebRTC compatibles";
        }
    },20000));
    timers.push(setTimeout(()=>{
        if(!torrent.ready)pauseEntry(entry.uid,"Pausado Sin compatibles 2.");
    },60000));
    torrent.on("metadata",()=>timers.forEach(clearTimeout));
    torrent.on("done",()=>{
        entry.el.dataset.status="done";
        entry.el.querySelector(".tdl-badge").textContent="Completo";
        if(!DIR)fallbackLinks(torrent,entry.el.querySelector(".tdl-files"));
        promote();
        wakeSync();
    });
    torrent.on("error",err=>{
        timers.forEach(clearTimeout);
        ACT.delete(entry.uid);
        entry.source=torrent.magnetURI;
        entry.el.dataset.status="error";
        entry.el.querySelector(".tdl-badge").textContent="Error";
        const w=entry.el.querySelector(".tdl-warn");
        w.hidden=false;
        w.textContent="Error: "+esc(err.message);
        PAUSED.push(entry);
        promote();
        wakeSync();
    });
    ACT.set(entry.uid,{torrent,entry,timers});
    wakeSync();
}

function pauseEntry(uid,msg){
    const rec=ACT.get(uid);
    if(!rec)return;
    const {torrent,entry,timers}=rec;
    const mag=torrent.magnetURI;
    timers.forEach(clearTimeout);
    torrent.destroy();
    ACT.delete(uid);
    entry.source=mag;
    entry.el.dataset.status="paused";
    entry.el.querySelector(".tdl-badge").textContent="Pausado";
    if(msg){
        const w=entry.el.querySelector(".tdl-warn");
        w.hidden=false;
        w.textContent=msg;
    }
    PAUSED.push(entry);
    wakeSync();
    promote();
}
function resumeEntry(uid){
    const idx=PAUSED.findIndex(e=>e.uid===uid);
    if(idx<0)return;
    const [entry]=PAUSED.splice(idx,1);
    entry.el.querySelector(".tdl-warn").hidden=true;
    entry.el.dataset.status="queued";
    entry.el.querySelector(".tdl-badge").textContent="En cola";
    QUEUE.unshift(entry);
    promote();
}
function removeEntry(uid){
    const rec=ACT.get(uid);
    if(rec){
        rec.timers.forEach(clearTimeout);
        rec.torrent.destroy();
        ACT.delete(uid);
    }else{
        let idx=QUEUE.findIndex(e=>e.uid===uid);
        if(idx>=0)QUEUE.splice(idx,1);
        idx=PAUSED.findIndex(e=>e.uid===uid);
        if(idx>=0)PAUSED.splice(idx,1);
    }
    const el=list.querySelector(`[data-uid="${uid}"]`);
    if(el)el.remove();
    wakeSync();
    promote();
}

function addEntry(source,dn){
    const uid=nextId();
    const el=document.createElement("div");
    el.className="tdl-card";
    el.dataset.uid=uid;
    el.dataset.status="queued";
    el.innerHTML=cardHTML(dn||"Torrent en cola");
    list.appendChild(el);
    QUEUE.push({uid,source,el});
    promote();
}

list.addEventListener("click",e=>{
    const b=e.target.closest("[data-act]");
    if(!b)return;
    const card=b.closest(".tdl-card");
    if(!card)return;
    const uid=card.dataset.uid;
    if(b.dataset.act==="pause")pauseEntry(uid);
    else if(b.dataset.act==="resume")resumeEntry(uid);
    else if(b.dataset.act==="remove")removeEntry(uid);
});

const inp=root.querySelector(".tdl-input");
root.querySelector('[data-act="add"]').addEventListener("click",()=>{
    const v=inp.value.trim();
    if(!v)return;
    addEntry(v,magnetName(v));
    inp.value="";
});
inp.addEventListener("keydown",e=>{if(e.key==="Enter")root.querySelector('[data-act="add"]').click()});

const fileInp=root.querySelector('[data-act="file"]');
fileInp.addEventListener("change",async()=>{
    const f=fileInp.files[0];
    if(!f)return;
    const buf=new Uint8Array(await f.arrayBuffer());
    addEntry(buf,f.name.replace(/\.torrent$/i,""));
    fileInp.value="";
});

const dirBtn=root.querySelector('[data-act="pickdir"]');
const dirName=root.querySelector(".tdl-dir-name");
if(!FSA){
    dirBtn.disabled=true;
    dirBtn.textContent="no work";
}
dirBtn.addEventListener("click",async()=>{
    if(!FSA)return;
    try{
        DIR=await window.showDirectoryPicker({mode:"readwrite"});
        dirName.textContent="📁 "+DIR.name;
    }catch(e){if(e.name!=="AbortError")console.error("TorrentDL dir",e)}
});

const maxInp=root.querySelector('[data-act="max"]');
maxInp.addEventListener("change",()=>{
    const v=parseInt(maxInp.value,10);
    MAXACT=v>0?v:1;
    promote();
});
const TICK=setInterval(()=>{
    for(const {torrent,entry} of ACT.values()){
        const c=entry.el;
        c.querySelector(".tdl-bar-f").style.width=(torrent.progress*100).toFixed(1)+"%";
        c.querySelector(".tdl-p").textContent=(torrent.progress*100).toFixed(1)+"%";
        c.querySelector(".tdl-dl").textContent="↓ "+fmtB(torrent.downloadSpeed)+"/s";
        c.querySelector(".tdl-ul").textContent="↑ "+fmtB(torrent.uploadSpeed)+"/s";
        c.querySelector(".tdl-pe").textContent=torrent.numPeers+" peers";
        c.querySelector(".tdl-eta").textContent=torrent.done?"Listo":fmtT(torrent.timeRemaining);
    }
},600);

function cleanup(){
    clearInterval(TICK);
    if(CL){CL.destroy();CL=null}
    SRV=null;SRVNO=false;
    if(WL){WL.release().catch(()=>{});WL=null}
    QUEUE.length=0;PAUSED.length=0;ACT.clear();
}
root.addEventListener("contentUnload",cleanup,{once:true});
window.addEventListener("beforeunload",cleanup);
}();
</script>