## Reproductor

<style>
#ctw{--ct-r:var(--r-md,16px);display:flex;flex-direction:column;gap:12px;position:relative}
#ctw *{box-sizing:border-box}
#ctw button{cursor:pointer;font-family:inherit}
.ct-card{border:1px solid rgba(255,255,255,.1);border-radius:var(--ct-r);padding:14px}
.ct-h{display:flex;align-items:center;gap:10px;margin-bottom:10px}
.ct-h h3{margin:0;border:none!important;font-size:1rem;flex:1}
.ct-b{border:none;border-radius:var(--ct-r);padding:10px 16px;font-size:.85rem;background:rgba(255,255,255,.08);color:#fff}
.ct-b.on{background:var(--accent,#4ade80);color:#000;font-weight:600}
.ct-b:disabled{opacity:.4;cursor:not-allowed}
.ct-b.rec{background:rgba(248,113,113,.4);color:#fff;font-weight:600}
.ct-row{display:flex;gap:8px;flex-wrap:wrap;align-items:center}
#ct-qr{text-align:center}
#ct-code{text-align:center;font-size:1.6rem;font-weight:700;letter-spacing:.09em;margin:10px 0 2px}
#ct-hint{text-align:center;font-size:.76rem;color:rgba(255,255,255,.55);margin-bottom:12px}
#ct-join{flex:1;min-width:150px;padding:10px;border-radius:var(--ct-r);border:1px solid rgba(255,255,255,.15);background:rgba(0,0,0,.25);color:#fff;font-size:.9rem}
.ct-mod{display:none;position:fixed;inset:0;z-index:200;background:rgba(0,0,0,.92);flex-direction:column;align-items:center;justify-content:center;gap:14px;padding:20px}
.ct-mod.on{display:flex}
#ct-reader{width:100%;max-width:360px}
#ct-reader video{width:100%!important;border-radius:var(--ct-r)}
#ct-reader img{display:none!important}
#ct-wait{display:none;text-align:center;padding:20px 10px;font-size:.95rem;color:rgba(255,255,255,.72)}
#ct-wait.on{display:block}
#ct-send.off{display:none}
#ct-main{display:none}
#ct-main.on{display:block}
#ct-main.loc.on{display:flex;flex-direction:column;gap:0}
#ct-main.loc .ct-h{order:0}
#ct-main.loc #ct-video{order:1}
#ct-main.loc #ct-bar{order:2}
#ct-main.loc #ct-stop-w{order:3}
#ct-main.loc #ct-ch{order:4}
#ct-main.loc #ct-ch-g{max-height:34vh}
#ct-main.loc #ct-video.on{margin-bottom:8px}
#ct-pair.off{display:none}
#ct-link{width:100%;padding:10px;border-radius:var(--ct-r);border:1px solid rgba(255,255,255,.15);background:rgba(0,0,0,.25);color:#fff;font-size:.85rem;margin-bottom:8px}
#ct-video{width:100%;max-height:64vh;background:#000;border-radius:var(--ct-r);display:none}
#ct-video.on{display:block}
#ct-msg{font-size:.82rem;padding:9px 12px;border-radius:var(--ct-r);background:rgba(255,255,255,.06);margin-top:8px;display:none}
#ct-msg.on{display:block}
#ct-msg.err{background:rgba(248,113,113,.18);color:#fca5a5}
#ct-bar{height:5px;border-radius:99px;background:rgba(255,255,255,.1);overflow:hidden;margin-top:8px;display:none}
#ct-bar.on{display:block}
#ct-bar i{display:block;height:100%;width:0;background:var(--accent,#4ade80);transition:width .3s}
#ct-stop-w{display:none;margin-top:8px}
#ct-stop-w.on{display:flex}
#ct-rc{display:none;margin-top:10px;padding-top:10px;border-top:1px solid rgba(255,255,255,.1)}
#ct-rc.on{display:block}
#ct-rc-t{font-size:.75rem;color:rgba(255,255,255,.6);white-space:nowrap;margin-left:auto}
#ct-rc-s{width:100%;margin-top:8px;accent-color:var(--accent,#4ade80)}
#ct-rc-d{font-size:.68rem;color:rgba(255,255,255,.45);text-align:center;margin-top:6px;min-height:1em}
#ct-wt{display:none;position:absolute;inset:-8px;z-index:60;background:rgba(12,12,14,.72);flex-direction:column;align-items:center;justify-content:center;gap:12px;border-radius:var(--ct-r);text-align:center;padding:16px}
#ct-wt.on{display:flex}
#ct-wt img{width:56px;height:56px;object-fit:contain}
#ct-wt-t{font-size:.85rem;color:rgba(255,255,255,.85);max-width:80%}
#ct-ch{display:none;margin-top:10px;padding-top:10px;border-top:1px solid rgba(255,255,255,.1)}
#ct-ch.on{display:block}
#ct-ch-h{display:flex;gap:8px;align-items:center;margin-bottom:8px}
#ct-ch-f{flex:1;min-width:0;padding:8px 12px;border-radius:var(--ct-r);border:1px solid rgba(255,255,255,.15);background:rgba(0,0,0,.25);color:#fff;font-size:.85rem}
#ct-ch-n{font-size:.72rem;color:rgba(255,255,255,.55);white-space:nowrap}
#ct-ch-g{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;max-height:48vh;overflow-y:auto;padding:2px}
.ct-hid{display:none}
</style>

<div id="ctw">
<div class="ct-card" id="ct-pair">
<div class="ct-h"><h3>Conectar TV y telefono</h3></div>
<div id="ct-qr"></div>
<div id="ct-code">...</div>
<div id="ct-hint">Escanea este codigo desde el otro dispositivo, o pega un enlace para verlo aca</div>
<div class="ct-row">
<input id="ct-join" placeholder="Codigo, enlace, magnet o lista" autocomplete="off">
<button class="ct-b" id="ct-go">Unirse</button>
<button class="ct-b" id="ct-scan" title="Escanear con la camara">📷</button>
</div>
</div>
<div class="ct-card" id="ct-main">
<div class="ct-h"><h3 id="ct-tt">Conectado</h3></div>
<div id="ct-wait">Esperando contenido del otro dispositivo</div>
<div id="ct-send">
<input id="ct-link" placeholder="Pega un enlace https de video" autocomplete="off">
<div class="ct-row">
<button class="ct-b on" id="ct-send-link">Enviar enlace</button>
<button class="ct-b" id="ct-send-file">Enviar archivo</button>
<button class="ct-b ct-hid" id="ct-send-scr">Espejar pantalla</button>
</div>
<div id="ct-rc">
<div class="ct-row">
<button class="ct-b" id="ct-rc-b" title="Pausa">⏸</button>
<button class="ct-b" id="ct-rc-m" title="Atras 10s">⏪</button>
<button class="ct-b" id="ct-rc-p" title="Adelante 10s">⏩</button>
<span id="ct-rc-t">0:00 / 0:00</span>
</div>
<input type="range" id="ct-rc-s" min="0" max="1000" value="0">
<div id="ct-rc-d"></div>
</div>
</div>
<div class="ct-row" id="ct-stop-w"><button class="ct-b" id="ct-stop">Detener</button><button class="ct-b ct-hid" id="ct-fs">Pantalla Completa</button><button class="ct-b ct-hid" id="ct-rec">⏺ Grabar</button></div>
<div id="ct-ch">
<div id="ct-ch-h">
<input id="ct-ch-f" placeholder="Buscar canal..." autocomplete="off">
<span id="ct-ch-n"></span>
<button class="ct-b" id="ct-ch-x">✕</button>
</div>
<div id="ct-ch-g"></div>
</div>
<input type="file" id="ct-fi" accept="video/*,audio/*" class="ct-hid">
<div id="ct-bar"><i id="ct-bar-i"></i></div>
<video id="ct-video" controls playsinline></video>
</div>
<div id="ct-wt"><img alt=""><div id="ct-wt-t"></div></div>
<div id="ct-msg"></div>
<div class="ct-mod" id="ct-cmod">
<div id="ct-reader"></div>
<button class="ct-b" id="ct-ccl">Cerrar</button>
</div>
</div>

<script>
(function(){
const CTE=document.getElementById('ctw');
if(!CTE)return;
const $=i=>document.getElementById(i);
const CT_RT=20000,CT_MB=209715200;
const M_PEER='https://cdn.jsdelivr.net/npm/peerjs@1.5.5/+esm',M_SL='/web/js/lib/Salas.js';
const M_WT='https://cdn.jsdelivr.net/npm/webtorrent@3.0.21/dist/webtorrent.min.js';
const M_HCS='https://cdn.jsdelivr.net/npm/hybrid-chunk-store@1.2.6/+esm';
const M_H5Q='https://cdn.jsdelivr.net/npm/html5-qrcode@2.3.8/html5-qrcode.min.js';
const M_HLS='https://cdn.jsdelivr.net/npm/hls.js@1.7.1/dist/hls.min.mjs';
const M_DASH='https://cdn.jsdelivr.net/npm/dashjs@5.2.1/dist/modern/esm/dash.all.min.js';
let peer=null,pid=null,room=null,R=null,conns={},wl=null;
let wt=null,HCS=null,curTorrent=null,qrCam=null,scrStream=null,curCall=null;
let dead=false,isHost=true,myCode='',hbIv=null,miss={},seedT=null,linked=false,joinTo=null;
let cSince={},curURL=null,lastProg=-1,hls=null,wasLinked=false,localOn=false;
let stIv=null,rst={p:true,ct:0,d:0},rcDrag=false,dsh=null;
let rec=null,recCh=[],recIv=null,recT0=0;
const PRE=String(window.__AN1||'').trim().toUpperCase();

function msg(t,err){
  const e=$('ct-msg');
  e.textContent=t;
  e.classList.toggle('err',!!err);
  e.classList.toggle('on',!!t);
  const w=$('ct-wt-t');
  if(w)w.textContent=t||'';
}
function wtOn(){
  const w=$('ct-wt'),i=w.querySelector('img');
  if(!i.src)i.src=(window.__CFG&&window.__CFG.waitAnim)||'';
  w.classList.add('on');
}
function wtOff(){$('ct-wt').classList.remove('on');}
const M3U_MAX=8388608,CH_MAX=120;
let chAll=[],shareURL=null;
async function shareGet(){
  if(shareURL)return;
  try{
    const r=await caches.match('/__share_data',{cacheName:'share-pending'});
    if(!r||Date.now()>+r.headers.get('X-Expires'))return;
    const d=await r.json();
    const v=String(d.url||d.text||'').trim();
    if(!v||(!okURL(v)&&!isMag(v)))return;
    shareURL=v;
    if(!$('ct-link').value)$('ct-link').value=v;
    if(!linked)msg('Se enviara al conectar con la TV');
  }catch(e){}
}
async function shareClear(){
  try{await caches.delete('share-pending');}catch(e){}
}
async function shareSend(){
  if(!shareURL||!linked||isHost)return;
  const v=shareURL;
  shareURL=null;
  shareClear();
  if(isMag(v)){
    send({t:'file',magnet:v,name:magName(v)||'torrent',mime:''});
    $('ct-link').value='';
    msg('Torrent compartido enviado');
    return;
  }
  wtOn();
  let lista=false;
  try{lista=await chTry(v);}catch(e){}
  wtOff();
  if(lista){$('ct-link').value='';return;}
  send({t:'link',v});
  $('ct-link').value='';
  msg('Enviado lo compartido');
}
function chParse(txt){
  const out=[];
  let cur=null,skip=false;
  for(const raw of txt.split(/\r?\n/)){
    const l=raw.trim();
    if(!l)continue;
    if(l.slice(0,7)==='#EXTINF'){
      const i=l.indexOf(',');
      cur={
        name:(i>=0?l.slice(i+1):'').trim()||'Canal',
        logo:(l.match(/tvg-logo="([^"]*)"/)||[])[1]||'',
        group:(l.match(/group-title="([^"]*)"/)||[])[1]||''
      };
      skip=false;continue;
    }
    if(l[0]==='#'){
      if(l.startsWith('#KODIPROP')||l.startsWith('#EXTHTTP')||l.startsWith('#EXTVLCOPT'))skip=true;
      continue;
    }
    if(cur&&!skip&&/^https?:\/\//i.test(l)&&/\.(m3u8|mpd|mp4|webm)($|[?#])/i.test(l))out.push({...cur,url:l});
    cur=null;skip=false;
  }
  return out;
}
function chNode(c){
  const a=mkEl('div','gallery-item');
  if(c.logo&&/^https?:\/\//i.test(c.logo)){
    const im=mkEl('img');
    im.loading='lazy';im.alt='';
    im.onerror=()=>{im.remove();a.insertBefore(chIco(),a.firstChild);};
    im.src=c.logo;
    a.appendChild(im);
  }else a.appendChild(chIco());
  const m=mkEl('div','mc'),p=mkEl('p','gi-txt');
  p.textContent=c.name;m.appendChild(p);a.appendChild(m);
  a.onclick=()=>{
    if(localOn){playLink(c.url);return;}
    if(!linked){msg('Conecta la TV primero',true);return;}
    send({t:'link',v:c.url});
    msg('Enviado: '+c.name);
  };
  return a;
}
function chIco(){const d=mkEl('div','gi-navtile-ico');d.textContent='📺';return d;}
function mkEl(t,c){const e=document.createElement(t);if(c)e.className=c;return e;}
function chDraw(list){
  const g=$('ct-ch-g');
  g.innerHTML='';
  list.slice(0,CH_MAX).forEach(c=>g.appendChild(chNode(c)));
  $('ct-ch-n').textContent=list.length+(list.length>CH_MAX?' (+'+CH_MAX+')':'');
}
function chHide(){$('ct-ch').classList.remove('on');$('ct-ch-g').innerHTML='';chAll=[];}
async function chTry(u){
  if(!/\.m3u8?($|[?#])/i.test(u))return false;
  const ac=new AbortController();
  const to=setTimeout(()=>ac.abort(),20000);
  try{
    const r=await fetch(u,{signal:ac.signal});
    if(!r.ok)return false;
    if(Number(r.headers.get('content-length')||0)>M3U_MAX)return false;
    const t=await r.text();
    if(!/^\s*#EXTM3U/.test(t))return false;
    if(/#EXT-X-/.test(t))return false;
    const ch=chParse(t);
    if(!ch.length)return false;
    chAll=ch;
    $('ct-ch-f').value='';
    chDraw(ch);
    $('ct-ch').classList.add('on');
    msg('Lista con '+ch.length+' canales compatibles');
    return true;
  }catch(e){return false;}
  finally{clearTimeout(to);}
}
async function pasteIn(){
  try{
    const el=$('ct-link');
    if(el.value.trim())return;
    if(!navigator.clipboard||!navigator.clipboard.readText)return;
    const t=(await navigator.clipboard.readText()||'').trim();
    if(t&&t.length<2048&&okURL(t))el.value=t;
  }catch(e){}
}
function bar(v){
  const b=$('ct-bar');
  if(v==null){b.classList.remove('on');return;}
  b.classList.add('on');
  $('ct-bar-i').style.width=Math.max(0,Math.min(100,v))+'%';
}
const PIN_A='ABCDEFGHJKMNPQRSTUVWXYZ23456789';
const PIN_RE=/^KD[ABCDEFGHJKMNPQRSTUVWXYZ23456789]{6}$/;
function genCode(){
  const r=crypto.getRandomValues(new Uint32Array(6));
  let s='KD';
  for(let i=0;i<6;i++)s+=PIN_A[r[i]%PIN_A.length];
  return s;
}
function isPin(v){return PIN_RE.test(String(v||'').trim().toUpperCase());}
function okURL(u){
  try{const x=new URL(u,location.href);return x.protocol==='https:'||x.protocol==='http:';}
  catch(e){return false;}
}
const WT_TR=['wss://tracker.webtorrent.dev','wss://tracker.openwebtorrent.com','wss://tracker.btorrent.xyz'];
function isMag(u){return /^magnet:\?/i.test(String(u||'').trim());}
function magName(u){
  try{
    const q=new URLSearchParams(String(u).slice(String(u).indexOf('?')+1));
    return (q.get('dn')||'').trim();
  }catch(e){return '';}
}
const VID_RE=/\.(mp4|webm|m4v|mov|mkv|avi)$/i;
const SUB_RE=/\.(srt|vtt)$/i;
const IMG_RE=/\.(jpg|jpeg|png|webp|avif|gif)$/i;
let srvWT=null,srvNo=false,posterURL=null;
function langScore(l){
  const L=String(l||'').toLowerCase().replace('_','-');
  if(L==='es'||L==='spa'||L==='spanish'||L==='espanol'||L==='español')return 2;
  if(L==='es-es'||L==='spa-es')return 1;
  if(L.indexOf('es-')===0||L.indexOf('spa-')===0)return 3;
  if(/(^|[^a-z])(espanol|español|spanish|latino)([^a-z]|$)/.test(L))return 2;
  return -1;
}
function subLang(n){
  const m=String(n).match(/[.\-_]([a-z]{2,3}(?:-[a-z0-9]{2,4})?)\.(srt|vtt)$/i);
  return m?m[1]:'';
}
function pickVid(files){
  return (files||[]).filter(f=>VID_RE.test(f.name)).sort((a,b)=>b.length-a.length);
}
function pickSub(files){
  const c=(files||[]).filter(f=>SUB_RE.test(f.name)).map(f=>({f,s:langScore(subLang(f.name))})).filter(x=>x.s>=0);
  if(!c.length)return null;
  c.sort((a,b)=>b.s-a.s);
  return c[0].f;
}
function srt2vtt(t){
  return 'WEBVTT\n\n'+String(t).replace(/\r/g,'').replace(/(\d\d:\d\d:\d\d),(\d{1,3})/g,'$1.$2');
}
function clrSubs(){
  const v=$('ct-video');
  v.querySelectorAll('track').forEach(t=>{if(t.src&&t.src.slice(0,5)==='blob:')URL.revokeObjectURL(t.src);t.remove();});
}
function clrPoster(){
  const v=$('ct-video');
  v.removeAttribute('poster');
  if(posterURL){URL.revokeObjectURL(posterURL);posterURL=null;}
}
async function addSub(f){
  try{
    const raw=await f.text?await f.text():await(await f.blob()).text();
    const vtt=/^\s*WEBVTT/.test(raw)?raw:srt2vtt(raw);
    const url=URL.createObjectURL(new Blob([vtt],{type:'text/vtt'}));
    const tr=document.createElement('track');
    tr.kind='subtitles';
    tr.srclang='es';
    tr.label='Espanol';
    tr.default=true;
    tr.src=url;
    $('ct-video').appendChild(tr);
    return true;
  }catch(e){return false;}
}
function subEs(){
  const v=$('ct-video');
  try{
    const tt=v.textTracks;
    let bi=-1,bs=-1;
    for(let i=0;i<tt.length;i++){
      const sc=langScore(tt[i].language||tt[i].label||'');
      if(sc>bs){bs=sc;bi=i;}
    }
    for(let i=0;i<tt.length;i++)tt[i].mode=(i===bi&&bs>=0)?'showing':'disabled';
  }catch(e){}
  try{
    if(hls&&hls.subtitleTracks&&hls.subtitleTracks.length){
      let bi=-1,bs=-1;
      hls.subtitleTracks.forEach((t,i)=>{const sc=langScore(t.lang||t.name);if(sc>bs){bs=sc;bi=i;}});
      hls.subtitleTrack=bs>=0?bi:-1;
    }
  }catch(e){}
  try{
    if(dsh&&dsh.getTracksFor){
      const ts=dsh.getTracksFor('text')||[];
      let best=null,bs=-1;
      ts.forEach(t=>{const sc=langScore(t.lang||t.id);if(sc>bs){bs=sc;best=t;}});
      if(best&&bs>=0){dsh.setCurrentTrack(best);if(dsh.enableText)dsh.enableText(true);}
      else if(dsh.enableText)dsh.enableText(false);
    }
  }catch(e){}
}
async function ensureSrv(){
  if(srvWT)return srvWT;
  if(srvNo)return null;
  try{
    if(!('serviceWorker' in navigator)){srvNo=true;return null;}
    const reg=await navigator.serviceWorker.ready;
    if(!reg||!reg.active){srvNo=true;return null;}
    const c=await getWT();
    if(!c){srvNo=true;return null;}
    srvWT=c.createServer({controller:reg});
    return srvWT;
  }catch(e){srvNo=true;return null;}
}
function isHLS(u){return /\.m3u8($|[?#])/i.test(u);}
function isDASH(u){return /\.mpd($|[?#])/i.test(u);}
function killHLS(){if(hls){try{hls.destroy();}catch(e){}hls=null;}}
function torKill(t){
  return new Promise(r=>{
    if(!t)return r();
    let done=false;
    const fin=()=>{if(!done){done=true;r();}};
    setTimeout(fin,8000);
    try{t.destroy({destroyStore:true},fin);}catch(e){fin();}
  });
}
function killDASH(){if(dsh){try{dsh.destroy();}catch(e){}dsh=null;}}
function dlBlob(blob,name){
  const u=URL.createObjectURL(blob);
  const a=document.createElement('a');
  a.href=u;a.download=name;a.click();
  setTimeout(()=>URL.revokeObjectURL(u),15000);
}
function recMime(){
  if(!window.MediaRecorder)return '';
  const c=['video/webm;codecs=vp9,opus','video/webm;codecs=vp8,opus','video/webm'];
  for(const m of c){try{if(MediaRecorder.isTypeSupported(m))return m;}catch(e){}}
  return '';
}
function recEnd(){
  rec=null;
  if(recIv){clearInterval(recIv);recIv=null;}
  const b=$('ct-rec');
  b.classList.remove('rec');
  b.textContent='⏺ Grabar';
}
function recTick(){
  if(!rec)return;
  $('ct-rec').textContent='⏹ '+fmtT((Date.now()-recT0)/1000);
}
function recStop(){if(rec){try{rec.stop();}catch(e){recEnd();}}}
function recGo(){
  if(rec){recStop();return;}
  const v=$('ct-video');
  if(!v.classList.contains('on')){msg('No hay nada reproduciendose',true);return;}
  const mime=recMime();
  if(!mime){msg('Este navegador no puede grabar',true);return;}
  let st=null,secErr=false;
  try{st=v.captureStream?v.captureStream():(v.mozCaptureStream?v.mozCaptureStream():null);}
  catch(e){secErr=(e&&e.name==='SecurityError');}
  if(!st||!st.getTracks().length){
    msg(secErr?'Esta fuente no permite grabar (protegida por el servidor)':'No se puede grabar esta fuente',true);
    return;
  }
  try{rec=new MediaRecorder(st,{mimeType:mime});}catch(e){rec=null;msg('No se pudo iniciar la grabacion',true);return;}
  recCh=[];
  recT0=Date.now();
  rec.ondataavailable=e=>{if(e.data&&e.data.size)recCh.push(e.data);};
  rec.onerror=()=>{msg('Error al grabar',true);recEnd();};
  rec.onstop=()=>{
    const b=new Blob(recCh,{type:mime});
    recCh=[];
    recEnd();
    if(b.size){dlBlob(b,'grabacion-'+Date.now()+'.webm');msg('Grabacion lista');}
    else msg('No se grabo nada',true);
  };
  try{rec.start(2000);}catch(e){rec=null;msg('No se pudo iniciar la grabacion',true);return;}
  $('ct-rec').classList.add('rec');
  recIv=setInterval(recTick,1000);
  recTick();
}
const fmtT=s=>{s=Math.max(0,Math.floor(s||0));return Math.floor(s/60)+':'+String(s%60).padStart(2,'0');};
function vDiag(v){
  let buf=0;
  try{
    const b=v.buffered,t=v.currentTime||0;
    for(let i=0;i<b.length;i++){if(t>=b.start(i)&&t<=b.end(i)){buf=b.end(i)-t;break;}}
  }catch(e){}
  let dr=0;
  try{
    const q=v.getVideoPlaybackQuality?v.getVideoPlaybackQuality():null;
    dr=q?(q.droppedVideoFrames||0):(v.webkitDroppedFrameCount||0);
  }catch(e){}
  return{w:v.videoWidth||0,h:v.videoHeight||0,bf:Math.round(buf*10)/10,df:dr};
}
function stSend(){
  const v=$('ct-video');
  if(!v.classList.contains('on'))return;
  send({t:'st',p:v.paused,ct:v.currentTime||0,d:isFinite(v.duration)?v.duration:0,...vDiag(v)});
}
function stStart(){if(!stIv)stIv=setInterval(stSend,1000);}
function stStop(){if(stIv){clearInterval(stIv);stIv=null;}}
function rcShow(d){
  rst=d;
  $('ct-rc').classList.add('on');
  $('ct-rc-b').textContent=d.p?'▶':'⏸';
  $('ct-rc-t').textContent=fmtT(d.ct)+' / '+(d.d?fmtT(d.d):'--:--');
  const sl=$('ct-rc-s');
  sl.disabled=!d.d;
  if(!rcDrag&&d.d>0)sl.value=Math.round(d.ct/d.d*1000);
  const p=[];
  if(d.w)p.push(d.w+'x'+d.h);
  if(d.bf!=null)p.push('buffer '+d.bf+'s');
  if(d.df)p.push(d.df+' frames perdidos');
  $('ct-rc-d').textContent=p.join('  ·  ');
}
function rcHide(){
  $('ct-rc').classList.remove('on');
  $('ct-rc-d').textContent='';
  rst={p:true,ct:0,d:0};rcDrag=false;
}
function vLive(){
  const v=$('ct-video');
  return v.classList.contains('on')&&!v.ended&&!!(v.currentSrc||v.srcObject);
}

async function wlGet(){
  if(!('wakeLock' in navigator)||wl||dead)return;
  try{wl=await navigator.wakeLock.request('screen');wl.addEventListener('release',()=>{wl=null;});}catch(e){}
}
async function wlDrop(){
  if(wl){await wl.release().catch(()=>{});wl=null;}
}
function onVis(){
  if(document.visibilityState!=='visible'||dead)return;
  wlGet();
  chkConn();
  shareGet().then(shareSend);
}
function chkConn(){
  if(dead)return;
  Object.keys(conns).forEach(p=>{
    const c=conns[p];
    if(c&&c.open)return;
    if(c){try{c.close();}catch(e){}}
    delete conns[p];delete miss[p];
  });
  if(Object.keys(conns).length||!wasLinked)return;
  if(linked)loseLink('Se desconecto el otro dispositivo');
  rejoin();
}
async function rejoin(){
  if(dead||!room||linked)return;
  msg('Reconectando...');
  cSince={};
  await joinRoom(room);
}

async function initPeer(){
  if(peer&&!peer.destroyed&&pid)return;
  const [pm,sm]=await Promise.all([import(M_PEER),import(M_SL)]);
  const Peer=pm.Peer||pm.default;
  await new Promise((res,rej)=>{
    peer=new Peer({config:sm.SL_ICE1});
    peer.on('error',e=>{
      const t=e&&e.type;
      if(t==='peer-unavailable')return;
      if(!pid){rej(e);return;}
      if(!dead)msg('Error Conexion '+(t||''),true);
    });
    peer.once('open',id=>{
      pid=id;
      peer.on('connection',async c=>{
        const b=R&&await R.acc(c);
        if(!b)return;
        hookConn(c);
        b.forEach(d=>onData(d,c.peer));
      });
      peer.on('call',async call=>{
        if(!R||!await R.ok(call.peer)){try{call.close();}catch(e){}return;}
        call.answer();
        call.on('stream',s=>playStream(s));
        curCall=call;
      });
      peer.on('disconnected',()=>{if(room&&!dead)peer.reconnect();});
      res();
    });
  });
}

function hookConn(c){
  conns[c.peer]=c;
  miss[c.peer]=0;
  const op=()=>{
    linked=true;wasLinked=true;
    delete cSince[c.peer];
    clearTimeout(joinTo);
    msg('');
    $('ct-pair').classList.add('off');
    $('ct-main').classList.add('on');
    $('ct-tt').textContent=isHost?'Modo TV':'Enviar a la TV';
    $('ct-wait').classList.toggle('on',isHost);
    $('ct-send').classList.toggle('off',isHost);
    $('ct-stop-w').classList.add('on');
    wtOff();
    if(!isHost){shareSend();pasteIn();}
    startHB();
  };
  if(c.open)op();else c.on('open',op);
  c.on('data',d=>onData(d,c.peer));
  c.on('close',()=>dropPeer(c.peer));
  c.on('error',()=>dropPeer(c.peer));
}
function dropPeer(p){
  const c=conns[p];
  if(c){try{c.close();}catch(e){}}
  delete conns[p];delete miss[p];
  if(Object.keys(conns).length||!linked)return;
  loseLink('Se desconecto el otro dispositivo');
}
function loseLink(txt){
  linked=false;
  stopHB();
  rcHide();
  msg(txt,true);
  if(vLive())return;
  $('ct-main').classList.remove('on');
  $('ct-pair').classList.remove('off');
  $('ct-stop-w').classList.remove('on');
}
function send(d){
  Object.values(conns).forEach(c=>{if(c.open)try{c.send(d);}catch(e){}});
}
function startHB(){
  if(hbIv)return;
  hbIv=setInterval(()=>{
    Object.keys(conns).forEach(p=>{
      const c=conns[p];
      if(!c||!c.open){dropPeer(p);return;}
      miss[p]=(miss[p]||0)+1;
      if(miss[p]>3){dropPeer(p);return;}
      try{c.send({t:'ping'});}catch(e){dropPeer(p);}
    });
  },5000);
}
function stopHB(){if(hbIv){clearInterval(hbIv);hbIv=null;}}
async function resetPair(txt){
  linked=false;wasLinked=false;
  clearTimeout(joinTo);
  stopHB();
  stopAll(false);
  cSince={};
  $('ct-stop-w').classList.remove('on');
  chHide();
  $('ct-main').classList.remove('on');
  $('ct-pair').classList.remove('off');
  msg(txt||'',!!txt);
  if(dead)return;
  leaveRoom();
  isHost=true;
  await newRoom();
  showQR(myCode);
}

async function joinRoom(rid,noConn){
  await initPeer();
  if(!R)R=(await import(M_SL)).SL1({nick:'cast',on:connectMissing});
  let d;
  try{d=await R.join(rid,pid);}
  catch(e){msg(e.status===429?'Demasiados intentos, espera un rato':'Error al unirse',true);return false;}
  room=rid;
  if(!noConn)connectMissing(d.peers);
  return d;
}
async function newRoom(){
  for(let i=0;i<4;i++){
    if(!myCode||i>0)myCode=genCode();
    const d=await joinRoom('cast-'+myCode,true);
    if(!d)return false;
    if(!d.peers||!d.peers.length)return d;
    leaveRoom();
  }
  return false;
}
function connectMissing(peers){
  if(!peer||peer.destroyed)return;
  (peers||[]).forEach(p=>{
    if(p.pid===pid)return;
    const c=conns[p.pid];
    if(c&&c.open)return;
    if(cSince[p.pid]&&Date.now()-cSince[p.pid]<CT_RT)return;
    if(c){try{c.close();}catch(e){}delete conns[p.pid];delete miss[p.pid];}
    cSince[p.pid]=Date.now();
    const nc=peer.connect(p.pid,{reliable:true});
    if(nc)hookConn(nc);
  });
}
function leaveRoom(){
  if(R)R.leave();
  room=null;
}

async function showQR(code){
  $('ct-code').textContent=code;
  try{await (await import(M_SL)).SL_Q1($('ct-qr'),code,174);}
  catch(e){$('ct-qr').textContent='QR no disponible';}
}

function loadJS(u){
  return new Promise((res,rej)=>{
    const s=document.createElement('script');
    s.src=u;s.onload=res;s.onerror=rej;
    document.head.appendChild(s);
  });
}
async function scan(){
  if(qrCam)return;
  $('ct-cmod').classList.add('on');
  msg('Iniciando camara...');
  try{
    if(!window.Html5Qrcode)await loadJS(M_H5Q);
    $('ct-reader').innerHTML='';
    const inst=new Html5Qrcode('ct-reader');
    qrCam=inst;
    await inst.start({facingMode:'environment'},{fps:10,qrbox:{width:240,height:240}},raw=>{
      const s=String(raw||'').trim();
      const code=(s.includes('#')?s.split('#').pop():s).trim().toUpperCase();
      if(!code)return;
      stopScan();
      $('ct-join').value=code;
      doJoin();
    },()=>{});
    if(qrCam!==inst){killScan(inst);return;}
    msg('Apunta al codigo QR');
  }catch(e){
    stopScan();
    msg('Error camara',true);
  }
}
function killScan(c){
  if(!c)return;
  Promise.resolve().then(()=>c.stop()).catch(()=>{}).then(()=>{try{c.clear();}catch(e){}});
}
function stopScan(){
  const c=qrCam;
  qrCam=null;
  killScan(c);
  $('ct-cmod').classList.remove('on');
}

function localMode(on){
  localOn=on;
  $('ct-pair').classList.toggle('off',on);
  $('ct-main').classList.toggle('on',on);
  $('ct-main').classList.toggle('loc',on);
  if(on){
    $('ct-send').classList.add('off');
    $('ct-wait').classList.remove('on');
    $('ct-tt').textContent='Viendo aca';
    $('ct-stop-w').classList.add('on');
  }
}
async function localGo(v){
  localMode(true);
  msg('');
  if(isMag(v)){await recvFile({magnet:v,name:magName(v)||'torrent'});return;}
  wtOn();
  let lista=false;
  try{lista=await chTry(v);}catch(e){}
  wtOff();
  if(lista)return;
  await playLink(v);
}
async function doJoin(){
  let raw=($('ct-join').value||'').trim();
  if(!raw)return;
  if(isPin(raw.split('#').pop()))raw=raw.split('#').pop();
  if(!isPin(raw)){
    if(!okURL(raw)&&!isMag(raw)){msg('No parece un codigo ni un enlace',true);return;}
    $('ct-join').value='';
    return localGo(raw);
  }
  const code=raw.toUpperCase();
  if(code===myCode){msg('Ese es tu propio codigo',true);return;}
  wtOn();
  msg('Conectando...');
  leaveRoom();
  isHost=false;
  const d=await joinRoom('cast-'+code);
  if(!d){wtOff();return;}
  clearTimeout(joinTo);
  joinTo=setTimeout(()=>{
    wtOff();
    if(!linked)resetPair(d.peers&&d.peers.length?'No se pudo conectar':'No se encontro ese codigo');
  },15000);
}

function fsReq(){
  const v=$('ct-video');
  if(v.requestFullscreen)return v.requestFullscreen();
  if(v.webkitRequestFullscreen)return Promise.resolve(v.webkitRequestFullscreen());
  if(v.webkitEnterFullscreen)return Promise.resolve(v.webkitEnterFullscreen());
  return Promise.reject();
}
function exitFS(){
  if(document.fullscreenElement)document.exitFullscreen().catch(()=>{});
  else if(document.webkitFullscreenElement&&document.webkitExitFullscreen)document.webkitExitFullscreen();
}
function vShow(){
  $('ct-video').classList.add('on');
  $('ct-stop-w').classList.add('on');
  $('ct-fs').classList.remove('ct-hid');
  if(recMime())$('ct-rec').classList.remove('ct-hid');
  stStart();
}
function playStream(s){
  const v=$('ct-video');
  vShow();
  v.srcObject=s;
  v.play().catch(()=>{});
}
function playSrc(u){
  const v=$('ct-video');
  killHLS();killDASH();
  clrSubs();
  vShow();
  v.srcObject=null;
  v.src=u;
  if(curURL&&curURL!==u)URL.revokeObjectURL(curURL);
  curURL=u.slice(0,5)==='blob:'?u:null;
  v.play().catch(()=>{});
}

function vWait(ms){
  const v=$('ct-video');
  return new Promise(res=>{
    const done=r=>{clearTimeout(t);v.removeEventListener('error',onE);v.removeEventListener('loadeddata',onL);res(r);};
    const onE=()=>done(false),onL=()=>done(true);
    const t=setTimeout(()=>done(false),ms);
    v.addEventListener('error',onE);
    v.addEventListener('loadeddata',onL);
  });
}
async function tryNat(u,ms){
  const p=vWait(ms||12000);
  playSrc(u);
  return p;
}
async function tryDL(u){
  try{
    const r=await fetch(u);
    if(!r.ok)return false;
    if(Number(r.headers.get('content-length')||0)>CT_MB)return 'big';
    const b=await r.blob();
    const p=vWait(12000);
    playSrc(URL.createObjectURL(b));
    return p;
  }catch(e){return false;}
}
async function tryDLA(u){
  msg('Buscando otra fuente...');
  const ac=new AbortController();
  const to=setTimeout(()=>ac.abort(),45000);
  let d;
  try{
    const r=await fetch('/api/dla',{method:'POST',headers:{'content-type':'application/json'},body:JSON.stringify({url:u,mode:'stream'}),signal:ac.signal});
    if(!r.ok)return false;
    d=await r.json();
  }catch(e){return false;}
  finally{clearTimeout(to);}
  if(!d||!d.url)return false;
  const cand=[d].concat(Array.isArray(d.alts)?d.alts:[])
    .filter(c=>c&&c.url&&okURL(c.url)&&String(c.protocol||'').indexOf('dash')<0)
    .slice(0,4);
  if(!cand.length)return false;
  for(let i=0;i<cand.length;i++){
    const c=cand[i];
    const hls=isHLS(c.url)||String(c.protocol||'').indexOf('m3u8')>=0;
    msg('Cargando enlace...');
    if(await tryNat(c.url,hls?6000:12000))return true;
    if(hls&&await tryHLS(c.url))return true;
  }
  return false;
}
async function tryDASH(u){
  const v=$('ct-video');
  let MP;
  try{
    const m=await import(M_DASH);
    MP=m.MediaPlayer||(m.default&&m.default.MediaPlayer);
  }catch(e){return false;}
  if(!MP)return false;
  killHLS();killDASH();
  vShow();
  v.srcObject=null;
  v.removeAttribute('src');
  if(curURL){URL.revokeObjectURL(curURL);curURL=null;}
  let fin;
  const bad=new Promise(r=>{fin=r;});
  try{
    dsh=MP().create();
    dsh.on('error',()=>fin(false));
    dsh.initialize(v,u,true);
  }catch(e){killDASH();return false;}
  const ok=await Promise.race([vWait(15000),bad]);
  if(!ok)killDASH();
  return ok;
}
async function tryHLS(u){
  const v=$('ct-video');
  let H;
  try{H=(await import(M_HLS)).default;}catch(e){return false;}
  if(!H||!H.isSupported())return false;
  killHLS();killDASH();
  vShow();
  v.srcObject=null;
  v.removeAttribute('src');
  if(curURL){URL.revokeObjectURL(curURL);curURL=null;}
  hls=new H();
  let fin;
  const bad=new Promise(r=>{fin=r;});
  hls.on(H.Events.ERROR,(_,d)=>{if(d&&d.fatal)fin(false);});
  hls.on(H.Events.MANIFEST_PARSED,()=>v.play().catch(()=>{}));
  hls.loadSource(u);
  hls.attachMedia(v);
  const ok=await Promise.race([vWait(15000),bad]);
  if(!ok)killHLS();
  else subEs();
  return ok;
}
async function playLink(u){
  if(!okURL(u)){msg('Enlace no valido',true);return;}
  wtOn();
  try{
    msg('Cargando enlace...');
    if(await tryNat(u)){msg('');return;}
    if(isDASH(u)){
      msg('Probando modo stream...');
      if(await tryDASH(u)){msg('');return;}
    }else{
      if(!isHLS(u)){
        msg('No se pudo reproducir directo, descargando...');
        const r=await tryDL(u);
        if(r===true){msg('');return;}
        if(r==='big'){msg('Enlace muy pesado, usa Enviar archivo',true);return;}
      }
      msg('Probando modo stream...');
      if(await tryHLS(u)){msg('');return;}
    }
    if(await tryDLA(u)){msg('');return;}
    const v=$('ct-video');
    v.removeAttribute('src');v.load();v.classList.remove('on');
    msg('Enlace no compatible',true);
  }finally{wtOff();}
}

async function opfsDir(){
  const root=await navigator.storage.getDirectory();
  const apps=await root.getDirectoryHandle('Apps',{create:true});
  return await apps.getDirectoryHandle('Cast',{create:true});
}
async function opfsGet(name){
  const dir=await opfsDir();
  return await(await dir.getFileHandle(name)).getFile();
}
async function opfsSave(f,name){
  const dir=await opfsDir();
  const fh=await dir.getFileHandle(name,{create:true});
  await f.stream().pipeTo(await fh.createWritable());
  return await fh.getFile();
}
async function opfsClear(){
  try{
    const root=await navigator.storage.getDirectory();
    const apps=await root.getDirectoryHandle('Apps');
    await apps.removeEntry('Cast',{recursive:true});
  }catch(e){}
}

async function getWT(){
  if(wt)return wt;
  const[a,b]=await Promise.all([import(M_WT),import(M_HCS)]);
  HCS=b.default||b;
  wt=new(a.default||a)();
  wt.on('error',e=>msg('Error Archivo '+(e&&e.message?e.message:''),true));
  return wt;
}
async function sendFile(f){
  msg('Preparando archivo...');
  wtOn();
  let c=null;
  try{c=await getWT();}
  catch(e){wtOff();msg('No se pudo preparar el envio',true);return;}
  if(seedT){try{seedT.destroy({destroyStore:true});}catch(e){}seedT=null;}
  try{
  c.seed(f,{name:f.name,store:HCS,destroyStoreOnDestroy:true,announce:WT_TR},t=>{
    seedT=t;
    send({t:'file',magnet:t.magnetURI,name:f.name,mime:f.type||''});
    msg('Esperando que la TV empiece a descargar');
    wtOff();
    bar(0);
  });
  }catch(e){wtOff();msg('No se pudo preparar el envio',true);}
}

async function torStream(f,sub){
  const srv=await ensureSrv();
  if(!srv)return false;
  const v=$('ct-video');
  killHLS();killDASH();
  vShow();
  v.srcObject=null;
  v.removeAttribute('src');
  if(curURL){URL.revokeObjectURL(curURL);curURL=null;}
  clrSubs();
  msg('Preparando reproduccion...');
  const p=vWait(75000);
  try{f.streamTo(v);}catch(e){return false;}
  const ok=await p;
  if(!ok)return false;
  if(sub)await addSub(sub);
  subEs();
  v.play().catch(()=>{});
  return true;
}
async function recvFile(d){
  msg('Descargando, se vera cuando termine');
  wtOn();
  bar(0);
  lastProg=-1;
  let c;
  try{c=await getWT();}catch(e){msg('No se pudo recibir el archivo',true);bar(null);return;}
  if(curTorrent){const old=curTorrent;curTorrent=null;await torKill(old);}
  try{
    const prev=await c.get(d.magnet);
    if(prev)await torKill(prev);
  }catch(e){}
  await opfsClear();
  c.add(d.magnet,{store:HCS,destroyStoreOnDestroy:true,announce:WT_TR},async t=>{
    curTorrent=t;
    const vids=pickVid(t.files);
    const f=vids[0]||t.files[0];
    if(!f){msg('Error Archivo, torrent vacio',true);return;}
    const sub=pickSub(t.files);
    const img=(t.files||[]).find(x=>IMG_RE.test(x.name));
    t.on('download',()=>{
      const p=t.progress*100;
      bar(p);
      if(p-lastProg>=1){lastProg=p;send({t:'prog',v:p});}
    });
    if(img){
      try{img.select(1);}catch(e){}
      img.blob().then(b=>{
        clrPoster();
        posterURL=URL.createObjectURL(b);
        $('ct-video').poster=posterURL;
      }).catch(()=>{});
    }
    const strOk=await torStream(f,sub);
    if(strOk){
      try{t.deselect(0,t.pieces.length-1);}catch(e){}
      try{f.select(1);}catch(e){}
      if(sub)try{sub.select(1);}catch(e){}
      if(img)try{img.select(1);}catch(e){}
      wtOff();
      msg('');
      send({t:'fileok'});
      return;
    }
    msg('Descargando, se vera cuando termine');
    t.once('done',async()=>{
      bar(null);
      send({t:'fileok'});
      try{
        wtOff();
        msg('Guardando...');
        const ext=String(d.name||'').match(/\.[a-zA-Z0-9]{1,8}$/);
        const nm='recibido'+(ext?ext[0]:'');
        await opfsSave(f,nm);
        const sb=sub?await(await sub.blob()).text().catch(()=>null):null;
        curTorrent=null;
        await torKill(t);
        playSrc(URL.createObjectURL(await opfsGet(nm)));
        if(sb){
          const vtt=/^\s*WEBVTT/.test(sb)?sb:srt2vtt(sb);
          const tr=document.createElement('track');
          tr.kind='subtitles';tr.srclang='es';tr.label='Espanol';tr.default=true;
          tr.src=URL.createObjectURL(new Blob([vtt],{type:'text/vtt'}));
          $('ct-video').appendChild(tr);
          subEs();
        }
        msg('');
      }catch(e){msg('Error Archivo, no se pudo abrir',true);}
    });
  });
}

async function shareScreen(){
  if(!navigator.mediaDevices||!navigator.mediaDevices.getDisplayMedia){msg('Este dispositivo no puede compartir pantalla',true);return;}
  try{scrStream=await navigator.mediaDevices.getDisplayMedia({video:{frameRate:30},audio:true});}
  catch(e){return;}
  const to=Object.keys(conns).find(p=>conns[p]&&conns[p].open);
  if(!to){scrStream.getTracks().forEach(t=>t.stop());scrStream=null;msg('Sin conexion',true);return;}
  curCall=peer.call(to,scrStream);
  msg('Compartiendo pantalla');
  scrStream.getVideoTracks()[0].addEventListener('ended',()=>stopAll(true));
}

function stopAll(local){
  if(scrStream){scrStream.getTracks().forEach(t=>t.stop());scrStream=null;}
  if(curCall){try{curCall.close();}catch(e){}curCall=null;}
  if(curTorrent){try{curTorrent.destroy({destroyStore:true});}catch(e){}curTorrent=null;}
  recStop();
  $('ct-rec').classList.add('ct-hid');
  killHLS();killDASH();
  clrSubs();
  clrPoster();
  stStop();
  rcHide();
  wtOff();
  exitFS();
  opfsClear();
  const v=$('ct-video');
  v.pause();v.removeAttribute('src');v.srcObject=null;v.classList.remove('on');v.load();
  $('ct-fs').classList.add('ct-hid');
  if(curURL){URL.revokeObjectURL(curURL);curURL=null;}
  bar(null);msg('');
  if(local)send({t:'stop'});
}

function onData(d,from){
  if(!d||!d.t)return;
  if(from)miss[from]=0;
  if(d.t==='ping'){const c=conns[from];if(c&&c.open)try{c.send({t:'pong'});}catch(e){}return;}
  if(d.t==='pong')return;
  if(d.t==='fileok'){bar(null);msg('Enviado');return;}
  if(d.t==='prog'){bar(d.v);msg('Enviando archivo');return;}
  if(d.t==='st'){rcShow(d);return;}
  if(d.t==='ctl'){
    const v=$('ct-video');
    if(!v.classList.contains('on'))return;
    if(d.a==='play')v.play().catch(()=>{});
    else if(d.a==='pause')v.pause();
    else if(d.a==='seek'&&isFinite(d.v))v.currentTime=Math.max(0,d.v);
    stSend();
    return;
  }
  if(d.t==='link')playLink(d.v);
  else if(d.t==='file')recvFile(d);
  else if(d.t==='stop')stopAll(false);
}

$('ct-fs').onclick=()=>{fsReq().catch(()=>{});};
$('ct-rec').onclick=recGo;
$('ct-video').addEventListener('play',stSend);
$('ct-video').addEventListener('pause',stSend);
$('ct-video').addEventListener('seeked',stSend);
$('ct-rc-b').onclick=()=>send({t:'ctl',a:rst.p?'play':'pause'});
$('ct-rc-m').onclick=()=>send({t:'ctl',a:'seek',v:Math.max(0,rst.ct-10)});
$('ct-rc-p').onclick=()=>send({t:'ctl',a:'seek',v:rst.ct+10});
$('ct-rc-s').addEventListener('pointerdown',()=>{rcDrag=true;});
$('ct-rc-s').addEventListener('input',()=>{
  if(!rst.d)return;
  $('ct-rc-t').textContent=fmtT($('ct-rc-s').value/1000*rst.d)+' / '+fmtT(rst.d);
});
$('ct-rc-s').addEventListener('change',()=>{
  rcDrag=false;
  if(rst.d)send({t:'ctl',a:'seek',v:$('ct-rc-s').value/1000*rst.d});
});
$('ct-go').onclick=doJoin;
$('ct-scan').onclick=scan;
$('ct-ccl').onclick=stopScan;
$('ct-join').addEventListener('keydown',e=>{if(e.key==='Enter')doJoin();});
$('ct-send-link').onclick=async()=>{
  const u=($('ct-link').value||'').trim();
  if(!u)return;
  if(isMag(u)){
    send({t:'file',magnet:u,name:magName(u)||'torrent',mime:''});
    $('ct-link').value='';
    msg('Torrent enviado');
    wtOn();
    setTimeout(wtOff,6000);
    return;
  }
  if(!okURL(u)){msg('Enlace no valido',true);return;}
  wtOn();
  let esLista=false;
  try{esLista=await chTry(u);}catch(e){}
  wtOff();
  if(esLista){$('ct-link').value='';return;}
  send({t:'link',v:u});
  $('ct-link').value='';
  msg('Enlace enviado');
  wtOn();
  setTimeout(wtOff,6000);
};
$('ct-ch-x').onclick=chHide;
$('ct-ch-f').addEventListener('input',()=>{
  const q=$('ct-ch-f').value.trim().toLowerCase();
  chDraw(q?chAll.filter(c=>(c.name+' '+c.group).toLowerCase().includes(q)):chAll);
});
$('ct-link').addEventListener('focus',pasteIn);
$('ct-send-file').onclick=()=>$('ct-fi').click();
$('ct-fi').onchange=e=>{const f=e.target.files[0];e.target.value='';if(f)sendFile(f);};
$('ct-send-scr').onclick=shareScreen;
$('ct-stop').onclick=()=>{
  stopAll(true);
  if(localOn){localMode(false);chHide();msg('');return;}
  if(!linked&&!dead)resetPair();
};

if(navigator.mediaDevices&&navigator.mediaDevices.getDisplayMedia)$('ct-send-scr').classList.remove('ct-hid');

function teardown(){
  dead=true;
  stopScan();
  stopHB();
  stopAll(false);
  leaveRoom();
  Object.values(conns).forEach(c=>{try{c.close();}catch(e){}});
  conns={};
  if(seedT){try{seedT.destroy({destroyStore:true});}catch(e){}seedT=null;}
  if(wt){try{wt.destroy();}catch(e){}wt=null;}
  opfsClear();
  if(peer&&!peer.destroyed){try{peer.destroy();}catch(e){}}
  peer=null;pid=null;
  if(curURL){URL.revokeObjectURL(curURL);curURL=null;}
  wlDrop();
  document.removeEventListener('visibilitychange',onVis);
  window.removeEventListener('online',chkConn);
  window.removeEventListener('beforeunload',teardown);
}
document.addEventListener('visibilitychange',onVis);
window.addEventListener('online',chkConn);
window.addEventListener('beforeunload',teardown);
const cEl=document.getElementById('content');
if(cEl)cEl.addEventListener('contentUnload',teardown,{once:true});

(async function(){
  wlGet();
  shareGet();
  try{
    await initPeer();
  }catch(e){msg('Error Conexion, no se pudo iniciar',true);return;}
  if(PRE){
    $('ct-join').value=PRE;
    showQR(PRE);
    doJoin();
    return;
  }
  isHost=true;
  await newRoom();
  showQR(myCode);
})();
})();
</script>

<div class="contenedor-imagenes-animado" data-title="📺 Lista Canales" data-gallery-key="Television_Online" data-json-path="web/adjuntos/Television_Online/data.json"></div>
