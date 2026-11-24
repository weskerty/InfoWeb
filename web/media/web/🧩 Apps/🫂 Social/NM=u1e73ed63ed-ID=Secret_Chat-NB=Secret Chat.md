<style>
#chatw{--cw-r-lg:var(--r-lg,24px);--cw-r-md:var(--r-md,16px);--cw-r-sm:var(--r-sm,12px);display:flex;flex-direction:column;gap:10px}
#chatw *{box-sizing:border-box}

#cw-lb-h{display:flex;align-items:center;gap:10px;padding:14px 16px}
#cw-lb-h h2{flex:1;margin:0;border:none!important;font-size:1.05rem}
#cw-search{padding:0 16px 4px}
#cw-list{display:flex;flex-direction:column;gap:6px;padding:6px 10px 14px;max-height:62vh;overflow-y:auto}
.cw-room{display:flex;align-items:center;gap:12px;padding:10px 12px;border-radius:var(--cw-r-sm);cursor:pointer;transition:background .15s;border:1px solid rgba(255,255,255,.08)}
.cw-room:hover{background:rgba(255,255,255,.06)}
.cw-room-ic{width:38px;height:38px;border-radius:50%;background:rgba(255,255,255,.07);display:flex;align-items:center;justify-content:center;font-size:1rem;flex-shrink:0}
.cw-room-tx{flex:1;min-width:0}
.cw-room-nm{font-size:.9rem;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.cw-room-sb{font-size:.72rem;color:rgba(255,255,255,.5);margin-top:1px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.cw-room-rm{border:none;background:none;color:rgba(255,255,255,.4);font-size:.85rem;cursor:pointer;padding:4px;flex-shrink:0}
#cw-empty{text-align:center;padding:26px;color:rgba(255,255,255,.5);font-size:.85rem}
#cw-share-banner{display:none;margin:0 16px 8px;padding:9px 14px;border-radius:var(--cw-r-sm);background:rgba(var(--accent-rgb),.18);border:1px solid rgba(var(--accent-rgb),.35);font-size:.82rem;text-align:center}
#cw-share-prompt{display:none;align-items:center;gap:8px;padding:8px 12px;background:rgba(var(--accent-rgb),.15);border-bottom:1px solid rgba(255,255,255,.1)}
#cw-share-prompt-tx{flex:1;font-size:.8rem}
#cw-share-prompt button{border:none;border-radius:var(--cw-r-sm);padding:6px 12px;font-size:.78rem;cursor:pointer}
#cw-share-send{background:var(--accent);color:#fff}
#cw-share-discard{background:rgba(255,255,255,.08);color:#fff}

#cw-chat{display:none;flex-direction:column;overflow:hidden}
#cw-chat.on{display:flex}
#cw-lobby.hid{display:none}
#cw-ch-h{display:flex;align-items:center;gap:10px;padding:10px 12px;border-bottom:1px solid rgba(255,255,255,.1)}
#cw-ch-tx{flex:1;min-width:0}
#cw-ch-nm{font-size:.92rem;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
#cw-ch-sb{font-size:.68rem;color:rgba(255,255,255,.5)}
#cw-vg{display:none;gap:8px;padding:8px;overflow-x:auto;border-bottom:1px solid rgba(255,255,255,.1)}
#cw-vg.on{display:flex}
.cw-vp{flex-shrink:0;position:relative}
.cw-vp video{width:100px;height:75px;border-radius:var(--cw-r-sm);object-fit:cover;background:#000;display:block}
.cw-vp-n{font-size:.6rem;color:rgba(255,255,255,.6);text-align:center;margin-top:2px;max-width:100px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
#cw-msgs{overflow-y:auto;padding:12px 10px;display:flex;flex-direction:column;gap:6px;height:52vh;max-height:52vh}
.cw-msg{display:flex;gap:8px;max-width:82%;align-items:flex-end}
.cw-msg.me{flex-direction:row-reverse;align-self:flex-end}
.cw-msg .cw-avi{width:24px;height:24px;border-radius:50%;background:rgba(255,255,255,.08);display:flex;align-items:center;justify-content:center;font-size:.55rem;font-weight:700;flex-shrink:0;overflow:hidden}
.cw-msg-b{padding:8px 12px;border-radius:16px;font-size:.86rem;line-height:1.4;word-break:break-word;background:rgba(255,255,255,.06)}
.cw-msg.me .cw-msg-b{background:rgba(var(--accent-rgb),.28);border-bottom-right-radius:4px}
.cw-msg:not(.me) .cw-msg-b{border-bottom-left-radius:4px}
.cw-msg-nm{font-size:.62rem;margin-bottom:2px;font-weight:600;color:var(--accent-2,#38bdf8)}
.cw-sys{font-size:.68rem;color:rgba(255,255,255,.45);text-align:center;padding:4px 0}
.cw-flash .cw-msg-b{animation:cw-flash-anim 1s ease}
@keyframes cw-flash-anim{0%,100%{box-shadow:none}30%{box-shadow:0 0 0 2px rgba(var(--accent-rgb),.7)}}
body.low-perf .cw-flash .cw-msg-b{animation:none}
.cw-stk{width:120px;height:120px;display:block;border-radius:var(--cw-r-sm);object-fit:contain;background:rgba(255,255,255,.04)}
.cw-dl{display:inline-flex;align-items:center;gap:6px;padding:6px 11px;background:rgba(255,255,255,.07);border:1px solid rgba(255,255,255,.14);border-radius:var(--cw-r-sm);font-size:.76rem;cursor:pointer;margin-top:3px}
.cw-dl:hover{background:rgba(255,255,255,.13)}
.cw-torrent-pr{font-size:.64rem;color:rgba(255,255,255,.5);margin-top:2px}

#cw-iw{border-top:1px solid rgba(255,255,255,.1)}
#cw-sp{display:none;overflow-y:auto;padding:16px 12px;flex-wrap:wrap;gap:10px;align-content:flex-start;height:52vh;max-height:52vh}
#cw-sp.on{display:flex}
.cw-sp-item{position:relative;width:64px;height:64px;border:none;background:rgba(255,255,255,.05);border-radius:var(--cw-r-sm);cursor:pointer;padding:0;overflow:hidden;flex-shrink:0}
.cw-sp-item img{width:100%;height:100%;object-fit:contain}
.cw-sp-add{width:64px;height:64px;border:1px dashed rgba(255,255,255,.3);background:none;border-radius:var(--cw-r-sm);color:#fff;font-size:1.5rem;cursor:pointer;flex-shrink:0}
#cw-ib{display:flex;align-items:flex-end;gap:6px;padding:8px 10px}
#cw-mi{flex:1;padding:9px 13px;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.15);border-radius:18px;color:#fff;font-size:.88rem;outline:none;resize:none;max-height:110px;line-height:1.4}
.cw-ibtn{border:none;background:rgba(255,255,255,.07);color:#fff;width:36px;height:36px;border-radius:50%;cursor:pointer;font-size:1rem;flex-shrink:0;display:flex;align-items:center;justify-content:center}
.cw-ibtn.send{background:var(--accent);color:#fff}

#cw-participants{display:none;overflow-y:auto;padding:16px 12px;flex-wrap:wrap;gap:16px;align-content:flex-start;height:52vh;max-height:52vh}
#cw-participants.on{display:flex}
#cw-msgs.hid{display:none}
#cw-wait{display:none;flex-direction:column;align-items:center;justify-content:center;gap:10px;height:52vh;max-height:52vh}
#cw-wait.on{display:flex}
#cw-wait-img{width:64px;height:64px;object-fit:contain;opacity:.85}
#cw-wq:not(:empty)~#cw-wait-img{width:28px;height:28px}
#cw-wait-tx{font-size:.78rem;color:rgba(255,255,255,.55)}
.cw-ibtn:disabled,#cw-mi:disabled{opacity:.4;cursor:default}
.cw-bubble{display:flex;flex-direction:column;align-items:center;gap:6px;width:76px;cursor:pointer;background:none;border:none;font-family:inherit}
.cw-bubble:disabled{cursor:default}
.cw-bubble-c{width:52px;height:52px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:1rem;color:#fff}
.cw-bubble-n{font-size:.7rem;text-align:center;color:#fff;max-width:76px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}

#cw-qb{display:none;align-items:center;gap:8px;padding:6px 12px;background:rgba(255,255,255,.05);border-top:1px solid rgba(255,255,255,.08)}
#cw-qb.on{display:flex}
#cw-qb-info{flex:1;min-width:0;border-left:3px solid var(--accent);padding-left:8px}
#cw-qb-nm{font-size:.68rem;color:var(--accent-2,#38bdf8);font-weight:600}
#cw-qb-tx{font-size:.75rem;color:rgba(255,255,255,.6);overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
#cw-qb-x{border:none;background:none;color:rgba(255,255,255,.6);font-size:.9rem;cursor:pointer;padding:4px}
.cw-quote{border-left:3px solid var(--accent);padding:3px 8px;margin-bottom:4px;border-radius:6px;background:rgba(255,255,255,.06)}
.cw-quote-nm{font-size:.62rem;color:var(--accent-2,#38bdf8);font-weight:600}
.cw-quote-tx{font-size:.72rem;color:rgba(255,255,255,.55);overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.cw-msg-b.cw-sticker-msg{background:transparent;padding:0}
.cw-sticker-msg .cw-stk{background:transparent}

dialog.cw-dlg{max-width:min(360px,calc(100vw - 40px))}
dialog.cw-dlg[open]{display:flex;flex-direction:column;gap:10px}
dialog.cw-dlg h3{margin:0 0 4px;font-size:1rem;border:none!important}
.cw-lbl{font-size:.7rem;color:rgba(255,255,255,.5);letter-spacing:.05em;text-transform:uppercase;margin-bottom:3px}
.cw-row{display:flex;gap:8px}
.cw-row .Bp{flex:1}

#cw-near-list{display:none;flex-direction:column;gap:6px;padding:6px 10px 14px;max-height:62vh;overflow-y:auto}
#cw-near-list.on{display:flex}
.cw-room-in{border-color:rgba(var(--accent-rgb),.5);background:rgba(var(--accent-rgb),.08)}

#cw-ia{display:none;flex-direction:column;gap:6px;padding:10px 12px;border-bottom:1px solid rgba(255,255,255,.1)}
#cw-ia.on{display:flex}
#cw-ia textarea{width:100%;font-family:inherit;font-size:.86em}
#cw-ia-st{font-size:.75rem;color:rgba(255,255,255,.7)}
#cw-iaw{display:none}
#cw-iv{display:none;padding:10px 12px;border-bottom:1px solid rgba(255,255,255,.1)}
#cw-iv.on{display:block}
#cw-sc{position:fixed;inset:0;background:rgba(0,0,0,.92);z-index:998;display:none;flex-direction:column;align-items:center;justify-content:center;gap:14px;padding:20px}
#cw-sc.on{display:flex}
#cw-rd{width:100%;max-width:360px}
#cw-rd video{width:100%!important;border-radius:var(--cw-r-sm)}
#cw-rd img{display:none!important}

#cw-toast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(20px);background:rgba(30,30,30,.97);border:1px solid rgba(255,255,255,.15);color:#fff;padding:10px 22px;border-radius:12px;font-size:.85em;opacity:0;pointer-events:none;transition:opacity .25s,transform .25s;z-index:999;max-width:80vw;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;cursor:pointer}
#cw-toast.show{opacity:1;transform:translateX(-50%) translateY(0);pointer-events:auto}
</style>

<div id="chatw">
  <div id="cw-lobby">
    <div id="cw-lb-h">
      <h2>Chats</h2>
      <button class="B Bi" id="cw-near" title="Cerca de mi" style="background:rgba(255,255,255,.08);border:none;color:#fff;width:38px;height:38px;border-radius:50%;cursor:pointer">🗺️</button>
      <button class="B Bi" id="cw-qr" title="Escanear QR" style="background:rgba(255,255,255,.08);border:none;color:#fff;width:38px;height:38px;border-radius:50%;cursor:pointer">📷</button>
      <button class="B Bi" id="cw-new" title="Agregar chat" style="background:rgba(255,255,255,.08);border:none;color:#fff;width:38px;height:38px;border-radius:50%;cursor:pointer">+</button>
    </div>
    <div id="cw-share-banner">Seleccionar chat para enviar</div>
    <div id="cw-search">
      <input id="cw-si" placeholder="Buscar chats..." type="search" autocomplete="off">
    </div>
    <div id="cw-list"><div id="cw-empty">Sin chats guardados. Toca + para agregar uno.</div></div>
    <div id="cw-near-list"></div>
  </div>

  <div id="cw-chat">
    <div id="cw-share-prompt">
      <span id="cw-share-prompt-tx"></span>
      <button id="cw-share-send">Enviar</button>
      <button id="cw-share-discard">Descartar</button>
    </div>
    <div id="cw-ch-h">
      <button class="cw-ibtn" id="cw-bk">←</button>
      <div id="cw-ch-tx">
        <div id="cw-ch-nm"></div>
        <div id="cw-ch-sb"></div>
      </div>
      <button class="cw-ibtn" id="cw-ch-inv" title="Invitar" style="display:none">🔗</button>
      <button class="cw-ibtn" id="cw-bs" title="Voz de la IA" style="display:none">🔊</button>
      <button class="cw-ibtn" id="cw-bi" title="IA" style="display:none">🧠</button>
      <button class="cw-ibtn" id="cw-bm" title="Microfono">🎤</button>
      <button class="cw-ibtn" id="cw-bv" title="Camara">📷</button>
      <button class="cw-ibtn" id="cw-bp" title="Participantes">👥</button>
    </div>
    <div id="cw-ia">
      <div id="cw-ia-st"></div>
      <button class="B" id="cw-ia-on">Prestar mi IA</button>
      <div class="cw-lbl">Instrucciones</div>
      <textarea class="MI" id="cw-ia-sy" rows="3" maxlength="2000"></textarea>
      <button class="B" id="cw-ia-ap">Aplicar</button>
    </div>
    <div id="cw-iv"></div>
    <div id="cw-vg"><div id="cw-vl" style="display:flex;gap:8px"></div></div>
    <div id="cw-msgs"></div>
    <div class="cw-sys" id="cw-iaw">IA escribiendo...</div>
    <div id="cw-participants"></div>
    <div id="cw-sp"></div>
    <div id="cw-wait"><div id="cw-wq"></div><img id="cw-wait-img" alt=""><div id="cw-wait-tx">Conectando...</div></div>
    <input type="file" id="cw-sp-file" accept="image/webp,image/avif,image/*" style="display:none">
    <div id="cw-iw">
      <div id="cw-qb">
        <div id="cw-qb-info"><div id="cw-qb-nm"></div><div id="cw-qb-tx"></div></div>
        <button id="cw-qb-x">✕</button>
      </div>
      <div id="cw-ib">
        <button class="cw-ibtn" id="cw-be">🏷️</button>
        <textarea id="cw-mi" rows="1" placeholder="Mensaje..." maxlength="4000"></textarea>
        <label class="cw-ibtn" style="cursor:pointer" title="Archivo (se comparte P2P via torrent)">📎<input type="file" id="cw-fl" style="display:none"></label>
        <button class="cw-ibtn send" id="cw-sn">➤</button>
      </div>
    </div>
  </div>
</div>

<div id="cw-toast"></div>
<div id="cw-sc"><div id="cw-rd"></div><button class="B" id="cw-sx">Cancelar</button></div>

<dialog class="cw-dlg" id="cw-m-perfil">
  <h3>Tu nombre</h3>
  <div>
    <div class="cw-lbl">Como te ven los demas</div>
    <input class="MI" id="cw-pf-nk" placeholder="Tu nombre..." maxlength="24" autocomplete="off">
  </div>
  <div class="cw-row">
    <button class="B Bp Bac view-all-button" id="cw-pf-ok">Continuar</button>
    <button class="B Bp Bs back-button" id="cw-pf-cx">Cancelar</button>
  </div>
</dialog>

<dialog class="cw-dlg" id="cw-m-add">
  <h3>Agregar chat</h3>
  <div class="cw-row">
    <div style="flex:1">
      <div class="cw-lbl">ID de sala (compartila para invitar)</div>
      <input class="MI" id="cw-ad-rid" placeholder="sala-xxxxxxxx" autocomplete="off">
    </div>
    <button class="B Bi" id="cw-ad-rid-gen" title="Generar ID nueva" style="align-self:flex-end;background:rgba(255,255,255,.08);border:none;color:#fff;width:38px;height:38px;border-radius:50%;cursor:pointer">🎲</button>
    <button class="B Bi" id="cw-ad-sc" title="Escanear QR" style="align-self:flex-end;background:rgba(255,255,255,.08);border:none;color:#fff;width:38px;height:38px;border-radius:50%;cursor:pointer">📷</button>
  </div>
  <div>
    <div class="cw-lbl">Contrasena (opcional)</div>
    <input class="MI" id="cw-ad-rpw" type="password" placeholder="..." autocomplete="new-password">
  </div>

  <div class="cw-row">
    <button class="B Bp Bac view-all-button" id="cw-ad-ok">Guardar</button>
    <button class="B Bp Bs back-button" id="cw-ad-cx">Cancelar</button>
  </div>
</dialog>

<script>
!function(){
const HIST=200,DOM=80,IM_STK=524288,AUTO_DL_MAX=1048576,MSG_MAX=4000,IA_COL='#38bdf8';
const $=id=>document.getElementById(id);
const esc=s=>String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
const mk=(tag,cls)=>{const e=document.createElement(tag);if(cls)e.className=cls;return e;};
const imgB=(blob,cls)=>{const i=mk('img',cls),u=URL.createObjectURL(blob);i.onload=()=>URL.revokeObjectURL(u);i.onerror=()=>URL.revokeObjectURL(u);i.src=u;return i;};
const COLS=['#e8a0a0','#e8c4a0','#a8d8a0','#a0c4e8','#c4a8e8','#e8a8d0','#a8dede','#e8e0a0'];
const uC={};let cI=0;
const gUC=pid=>{if(!uC[pid])uC[pid]=COLS[(cI++)%COLS.length];return uC[pid];};
const fSz=b=>b>1048576?(b/1048576).toFixed(1)+'MB':(b/1024).toFixed(0)+'KB';
const cut=v=>String(v==null?'':v).slice(0,MSG_MAX);
function dlBlob(blob,name){
  const u=URL.createObjectURL(blob);
  const a=mk('a');a.href=u;a.download=name;a.click();
  setTimeout(()=>URL.revokeObjectURL(u),15000);
}

const disqusEl=document.getElementById('disqus-container');
const disqusPrevDisplay=disqusEl?disqusEl.style.display:null;
if(disqusEl)disqusEl.style.display='none';


function LS1(k){try{return localStorage.getItem(k);}catch(e){return null;}}
function LS2(k,v){try{localStorage.setItem(k,v);}catch(e){}}
function ckGet(k){const m=document.cookie.match(new RegExp('(?:^|; )'+k+'=([^;]*)'));return m?decodeURIComponent(m[1]):null;}
function ckSet(k,v){const sec=location.protocol==='https:'?';Secure':'';document.cookie=`${k}=${encodeURIComponent(v)};path=/;max-age=31536000;SameSite=Strict${sec}`;}
let nick=ckGet('cw_nick')||'';
function saveNick(n){
  nick=n;ckSet('cw_nick',n);
  if(geoWatchId!=null)geoPing();
}
function NK1(fn){
  if(nick)return fn();
  $('cw-pf-nk').value='';showModal('cw-m-perfil');
  $('cw-pf-ok').onclick=()=>{const n=$('cw-pf-nk').value.trim();if(!n)return;saveNick(n);hideModal('cw-m-perfil');fn();};
}

let peerP=null;
function loadPeerJS(){if(!peerP)peerP=import('https://cdn.jsdelivr.net/npm/peerjs@1.5.5/+esm').then(m=>m.Peer||m.default);return peerP;}

const PING=10000,SL_O={on:SL_O1};
let SLC1=null,SL_A=null,SLM=null;
async function SL_L1(){
  if(!SLC1){const m=await import('/web/js/lib/Salas.js');SLM=m;SL_A=m.SL_A1;SLC1=m.SL1(SL_O);}
  return SLC1;
}
const api=(m,p,b)=>SL_L1().then(()=>SL_A(m,p,b));

let peer=null,pid=null,curCfg=null,curRoom=null,pingIv=null;
let conns={},pNk={},pAu={},pVStr={},pMu={},connectingSince={},pingMisses={};
let aStream=null,vStream=null,muted=false,vidOn=false,pCalls={};
let hist=[],domCount=0,torrentClient=null,torrentStore=null;
function inAnyChat(){return!!curRoom||!!curDM;}

// --- DM directo (Cerca de mi): conexion P2P sin sala, sin bcrypt, reusa el reloj de espera de las salas ---
let curDM=null,dmReconnectTries={},pendingDM={};

// --- geolocalizacion: se comparte apenas se abre el chat, igual que clima.md ---
const GEO_PING_MS=15000;
let geoToken=null,geoWatchId=null,geoPingTimer=null,myGeoPos=null,nearShown=false;
let NR1={l:[],k:[],a:[]},NR_S1=new Set(),DMOK1=new Set(),NR_PP=null;

let _toastTimer=null,_toastAction=null;
function showToast(msg,action){
  const t=$('cw-toast');
  t.textContent=msg;
  _toastAction=action||null;
  t.classList.add('show');
  clearTimeout(_toastTimer);
  _toastTimer=setTimeout(()=>t.classList.remove('show'),4000);
}
$('cw-toast').onclick=()=>{if(_toastAction)_toastAction();$('cw-toast').classList.remove('show');};

let chatList=[];
const LK1=String(window.__AN1||'').trim();
function loadChatList(){try{return JSON.parse(localStorage.getItem('cw_chats')||'[]');}catch{return[];}}
function saveChatList(){try{localStorage.setItem('cw_chats',JSON.stringify(chatList));}catch{}}
chatList=loadChatList().filter(c=>c.kind!=='irc');

const HASWL='wakeLock' in navigator;
let wakeLock=null;
async function wakeAcquire(){
  if(!HASWL||wakeLock||!inAnyChat())return;
  try{wakeLock=await navigator.wakeLock.request('screen');wakeLock.addEventListener('release',()=>{wakeLock=null;});}catch(e){}
}
async function wakeRelease(){
  if(wakeLock){await wakeLock.release().catch(()=>{});wakeLock=null;}
}
function onVisChange(){
  if(document.visibilityState==='visible'&&inAnyChat()&&!wakeLock)wakeAcquire();
}
document.addEventListener('visibilitychange',onVisChange);

function showModal(id){$(id).showModal();document.body.style.overflow='hidden';}
function hideModal(id){$(id).close();}
document.querySelectorAll('dialog.cw-dlg').forEach(dlg=>{
  dlg.addEventListener('close',()=>{document.body.style.overflow='';});
});

function genRoomId(){const r=crypto.getRandomValues(new Uint32Array(8));let s='sala-';for(const x of r)s+='abcdefghjkmnpqrstuvwxyz23456789'[x%31];return s;}

function renderChatList(){
  const fv=$('cw-si').value.trim().toLowerCase();
  const arr=chatList.filter(c=>!fv||(c.label||'').toLowerCase().includes(fv));
  const incoming=Object.entries(pendingDM);
  const lb=$('cw-list');
  if(!incoming.length&&!arr.length&&!NR1.k.length){lb.innerHTML='<div id="cw-empty">Sin chats guardados. Toca + para agregar uno.</div>';return;}
  lb.innerHTML='';
  incoming.forEach(([fromPid,p])=>{
    const d=mk('div','cw-room cw-room-in');
    const ic=mk('div','cw-room-ic');ic.textContent='💬';
    const tx=mk('div','cw-room-tx');
    const nm=mk('div','cw-room-nm');nm.textContent=p.nick;
    const sb=mk('div','cw-room-sb');sb.textContent='Quiere chatear con vos';
    tx.append(nm,sb);
    d.append(ic,tx);
    d.onclick=()=>openIncomingDM(fromPid);
    lb.appendChild(d);
  });
  NR1.k.forEach(k=>{
    const d=mk('div','cw-room cw-room-in');
    const ic=mk('div','cw-room-ic');ic.textContent='👋';
    const tx=mk('div','cw-room-tx');
    const nm=mk('div','cw-room-nm');nm.textContent=k.n;
    const sb=mk('div','cw-room-sb');sb.textContent='Quiere chatear con vos';
    tx.append(nm,sb);
    const rm=mk('button','cw-room-rm');rm.textContent='✕';rm.title='Bloquear';
    rm.onclick=e=>{e.stopPropagation();NR_B1(k.h);};
    d.append(ic,tx,rm);
    d.onclick=()=>NR_A1(k.h,k.n);
    lb.appendChild(d);
  });
  arr.forEach(c=>{
    const d=mk('div','cw-room');
    const ic=mk('div','cw-room-ic');ic.textContent=c.roomPw?'🔒':'🔗';
    const tx=mk('div','cw-room-tx');
    const nm=mk('div','cw-room-nm');nm.textContent=c.label;
    const sb=mk('div','cw-room-sb');sb.textContent='Sala: '+c.roomId;
    tx.append(nm,sb);
    const rm=mk('button','cw-room-rm');rm.textContent='✕';rm.title='Quitar';
    rm.onclick=e=>{e.stopPropagation();chatList=chatList.filter(x=>x.id!==c.id);saveChatList();renderChatList();};
    d.append(ic,tx,rm);
    d.onclick=()=>clickChat(c);
    lb.appendChild(d);
  });
}
$('cw-si').oninput=renderChatList;

function renderNearby(){
  const wrap=$('cw-near-list');
  wrap.innerHTML='';
  const vis=geoWatchId!=null;
  const tg=mk('button','B');tg.textContent=vis?'Ocultarme':'Hacerme visible';
  tg.onclick=()=>vis?stopGeoShare():NK1(startGeoShare);
  wrap.appendChild(tg);
  if(!vis)return;
  if(!NR1.l.length){const e=mk('div');e.style.cssText='text-align:center;padding:26px;color:rgba(255,255,255,.5);font-size:.85rem';e.textContent=myGeoPos?'Nadie cerca por ahora':'Buscando ubicacion...';wrap.appendChild(e);return;}
  NR1.l.forEach(p=>{
    const d=mk('div','cw-room');
    const ic=mk('div','cw-room-ic');ic.textContent='🧑';
    const tx=mk('div','cw-room-tx');
    const nm=mk('div','cw-room-nm');nm.textContent=p.n;
    const sb=mk('div','cw-room-sb');sb.textContent=p.b+(NR_S1.has(p.h)?' · pedido enviado':'');
    tx.append(nm,sb);
    d.append(ic,tx);
    d.onclick=()=>NR_K1(p.h);
    wrap.appendChild(d);
  });
}

$('cw-near').onclick=()=>{
  nearShown=!nearShown;
  $('cw-list').style.display=nearShown?'none':'';
  $('cw-near-list').classList.toggle('on',nearShown);
  $('cw-near').style.background=nearShown?'rgba(74,222,128,.25)':'rgba(255,255,255,.08)';
  if(nearShown)renderNearby();
};

async function geoPing(){
  if(!myGeoPos)return;
  try{
    await initPeer();
    const d=await api('POST','/ping',{pid,token:geoToken,nick:nick||'Anonimo',lat:myGeoPos.lat,lon:myGeoPos.lon});
    geoToken=d.token;
  }catch(e){if(e.status===401)geoToken=null;}
  await fetchNearby();
}

function fetchNearby(){
  if(!geoToken)return Promise.resolve();
  return NR_PP||(NR_PP=api('POST','/near',{pid,token:geoToken}).then(d=>{
    const old=new Set(NR1.k.map(x=>x.h));
    NR1={l:d.l||[],k:d.k||[],a:d.a||[]};
    NR1.a.forEach(x=>DMOK1.add(x.p));
    NR1.k.filter(x=>!old.has(x.h)).forEach(x=>showToast(x.n+' quiere chatear con vos',()=>NR_A1(x.h,x.n)));
    renderChatList();
    if(nearShown)renderNearby();
  }).catch(()=>{}).finally(()=>{NR_PP=null;}));
}

function startGeoShare(){
  if(geoWatchId!=null)return;
  if(!navigator.geolocation){showToast('Sin acceso a la ubicacion');return;}
  geoWatchId=navigator.geolocation.watchPosition(p=>{
    const f=!myGeoPos;
    myGeoPos={lat:p.coords.latitude,lon:p.coords.longitude};
    if(f)geoPing();
  },()=>{showToast('Sin acceso a la ubicacion');stopGeoShare();},{enableHighAccuracy:false,maximumAge:30000,timeout:15000});
  geoPingTimer=setInterval(geoPing,GEO_PING_MS);
  LS2('UBI','1');
  if(nearShown)renderNearby();
}

function stopGeoShare(){
  if(geoWatchId!=null){navigator.geolocation.clearWatch(geoWatchId);geoWatchId=null;}
  if(geoPingTimer){clearInterval(geoPingTimer);geoPingTimer=null;}
  if(geoToken&&pid)api('DELETE','/leave',{pid,token:geoToken}).catch(()=>{});
  geoToken=null;myGeoPos=null;NR1={l:[],k:[],a:[]};NR_S1.clear();
  renderChatList();
  if(nearShown)renderNearby();
}

async function NR_K1(h){
  if(NR_S1.has(h))return;
  try{await api('POST','/knock',{pid,token:geoToken,h});NR_S1.add(h);showToast('Pedido enviado');renderNearby();}
  catch(e){showToast('Error Cerca de mi');}
}
async function NR_A1(h,n){
  let d;
  try{d=await api('POST','/accept',{pid,token:geoToken,h});}
  catch(e){showToast('Ya no esta disponible');NR1.k=NR1.k.filter(x=>x.h!==h);renderChatList();return;}
  DMOK1.add(d.p);
  NR1.k=NR1.k.filter(x=>x.h!==h);renderChatList();
  startDM(d.p,n);
}
function NR_B1(h){
  api('POST','/block',{pid,token:geoToken,h}).catch(()=>{});
  NR1.k=NR1.k.filter(x=>x.h!==h);renderChatList();
}

function clickChat(c){NK1(()=>enterRoom(c));}
$('cw-pf-cx').onclick=()=>hideModal('cw-m-perfil');

$('cw-new').onclick=()=>{
  $('cw-ad-rid').value=genRoomId();$('cw-ad-rpw').value='';
  showModal('cw-m-add');setTimeout(()=>$('cw-ad-rid').focus(),80);
};
$('cw-qr').onclick=()=>{$('cw-new').onclick();$('cw-ad-sc').onclick();};
$('cw-ad-rid-gen').onclick=()=>{$('cw-ad-rid').value=genRoomId();};
$('cw-ad-cx').onclick=()=>hideModal('cw-m-add');
$('cw-ad-ok').onclick=()=>{
  const rid=$('cw-ad-rid').value.trim();
  if(!/^[A-Za-z0-9_-]{1,64}$/.test(rid)){showToast('ID invalido');return;}
  const id=Date.now().toString(36)+Math.random().toString(36).slice(2,7);
  const ex=LK1===rid&&chatList.find(x=>x.roomId===rid);
  const c=ex||{id,kind:'room',label:rid,roomId:rid,roomPw:$('cw-ad-rpw').value||''};
  if(!ex){chatList.push(c);saveChatList();renderChatList();}
  hideModal('cw-m-add');
  if(LK1===rid)clickChat(c);
};

let QR_C=null;
function QR_K1(c){if(c)Promise.resolve().then(()=>c.stop()).catch(()=>{}).then(()=>{try{c.clear();}catch(e){}});}
function QR_X1(){const c=QR_C;QR_C=null;QR_K1(c);if($('cw-sc').classList.contains('on')){$('cw-sc').classList.remove('on');showModal('cw-m-add');}}
$('cw-sx').onclick=QR_X1;
$('cw-ad-sc').onclick=async()=>{
  if(QR_C)return;
  hideModal('cw-m-add');$('cw-sc').classList.add('on');
  try{
    if(!self.Html5Qrcode)await new Promise((ok,ko)=>{const e=mk('script');e.src='web/js/lib/Html5Qrcode/html5-qrcode.min.js';e.onload=ok;e.onerror=ko;document.head.appendChild(e);});
    $('cw-rd').innerHTML='';
    const i=new Html5Qrcode('cw-rd');QR_C=i;
    await i.start({facingMode:'environment'},{fps:10,qrbox:{width:240,height:240}},raw=>{
      const t=String(raw||'').trim().split('#').pop();
      if(!/^[A-Za-z0-9_-]{1,64}$/.test(t))return;
      $('cw-ad-rid').value=t;QR_X1();
    },()=>{});
    if(QR_C!==i)QR_K1(i);
  }catch(e){QR_X1();showToast('Error camara');}
};
async function QR_D1(box){
  const r=curCfg&&curCfg.roomId;
  if(!r){box.replaceChildren();return;}
  try{await SL_L1();SLM.SL_Q1(box,r,150);}catch(e){box.textContent='QR no disponible';}
}

function meta(){return{nick};}
function dmMeta(){return{nick,dm:true};}

function initPeer(){
  return new Promise((res,rej)=>{
    if(peer&&!peer.destroyed&&pid){res();return;}
    if(peer&&!peer.destroyed)peer.destroy();
    Promise.all([loadPeerJS(),SL_L1()]).then(([Peer])=>{
      peer=new Peer({config:SLM.SL_ICE1});
      peer.on('error',e=>{
        const t=e&&e.type;
        if(t==='peer-unavailable')return;
        if(!pid){rej(e);return;}
        if(inAnyChat())addSys('Error de conexion '+(t||''));
      });
      peer.once('open',id=>{
        pid=id;
        peer.on('connection',async conn=>{
          if(conn.metadata&&conn.metadata.dm)return onIncomingDM(conn);
          const b=SLC1&&SLC1.room&&await SLC1.acc(conn);
          if(!b)return;
          onConn(conn);
          b.forEach(d=>onData(d,conn.peer));
        });
        peer.on('call',async call=>{
          if(!await(curDM?curDM===call.peer&&DMOK1.has(call.peer):SLC1&&SLC1.ok(call.peer))){try{call.close();}catch(e){}return;}
          const s=new MediaStream();
          if(aStream)aStream.getTracks().forEach(t=>s.addTrack(t));
          if(vStream)vStream.getTracks().forEach(t=>s.addTrack(t));
          call.answer(s.getTracks().length?s:new MediaStream());
          hCall(call);
        });
        peer.on('disconnected',()=>{if(curRoom||curDM||geoWatchId!=null)peer.reconnect();});
        res();
      });
    }).catch(rej);
  });
}

function onConn(conn){
  const op=()=>{
    conns[conn.peer]=conn;
    delete connectingSince[conn.peer];
    pingMisses[conn.peer]=0;
    const m=conn.metadata||{};
    pNk[conn.peer]=m.nick||conn.peer.slice(0,8);
    conn.send({t:'meta',v:meta()});
    conn.send({t:'hist',v:hist.slice(-HIST)});
    if(IA1.on)conn.send({t:'ia',v:1});
    addSys((pNk[conn.peer]||conn.peer.slice(0,8))+' se unio');
    renderPeers();updateRoomCount();refreshWaitState();
    callPeer(conn.peer);
  };
  if(conn.open)op();else conn.on('open',op);
  conn.on('data',d=>onData(d,conn.peer));
  conn.on('close',()=>discPeer(conn.peer));
  conn.on('error',()=>discPeer(conn.peer));
}

function wireDMConn(conn,otherPid){
  const onOpen=()=>{
    conns[otherPid]=conn;
    dmReconnectTries[otherPid]=0;
    delete connectingSince[otherPid];
    try{conn.send({t:'meta',v:meta()});}catch(e){}
    try{conn.send({t:'hist',v:hist.slice(-HIST)});}catch(e){}
    if(IA1.on)try{conn.send({t:'ia',v:1});}catch(e){}
    if(curDM===otherPid){
      addSys((pNk[otherPid]||otherPid.slice(0,8))+' se conecto');
      $('cw-ch-sb').textContent='Conectado';
    }
    refreshWaitState();
  };
  if(conn.open)onOpen();else conn.on('open',onOpen);
  conn.on('data',d=>onData(d,otherPid));
  conn.on('close',()=>{discPeer(otherPid);if(curDM===otherPid)scheduleDMReconnect(otherPid);});
  conn.on('error',()=>{discPeer(otherPid);if(curDM===otherPid)scheduleDMReconnect(otherPid);});
}

function scheduleDMReconnect(otherPid){
  const tries=(dmReconnectTries[otherPid]||0)+1;
  if(tries>3)return;
  dmReconnectTries[otherPid]=tries;
  setTimeout(()=>{
    if(curDM!==otherPid||!peer||peer.destroyed)return;
    const conn=peer.connect(otherPid,{metadata:dmMeta(),reliable:true});
    if(!conn)return;
    conns[otherPid]=conn;
    wireDMConn(conn,otherPid);
  },2000*tries);
}

function enterDMUI(otherPid,otherNick){
  $('cw-msgs').innerHTML='';$('cw-vl').innerHTML='';$('cw-vg').classList.remove('on');
  conns={};pAu={};pVStr={};pMu={};pNk={};connectingSince={};pingMisses={};pCalls={};
  hist=[];domCount=0;curCfg=null;curRoom=null;curDM=otherPid;
  pNk[otherPid]=otherNick;
  $('cw-ch-nm').textContent=otherNick.length>26?otherNick.slice(0,26)+'…':otherNick;
  $('cw-ch-sb').textContent='Conectando...';
  $('cw-bm').style.display='';$('cw-bv').style.display='';
  $('cw-ch-inv').style.display='none';
  $('cw-bp').style.display='none';
  $('cw-lobby').classList.add('hid');$('cw-chat').classList.add('on');
}

async function startDM(otherPid,otherNick){
  enterDMUI(otherPid,otherNick);
  setWaiting(true,'Conectando...');
  try{await initPeer();}catch(e){showToast('Error al conectar');return goBack();}
  const conn=peer.connect(otherPid,{metadata:dmMeta(),reliable:true});
  if(!conn){showToast('Error al conectar');return goBack();}
  wireDMConn(conn,otherPid);
  wakeAcquire();
}

async function onIncomingDM(conn){
  const fromPid=conn.peer;
  if(!DMOK1.has(fromPid))await fetchNearby();
  if(!DMOK1.has(fromPid)){try{conn.close();}catch(e){}return;}
  const fromNick=(conn.metadata&&conn.metadata.nick)||fromPid.slice(0,8);
  if(curDM===fromPid){
    conns[fromPid]=conn;
    wireDMConn(conn,fromPid);
    refreshWaitState();
    return;
  }
  pendingDM[fromPid]={conn,nick:fromNick};
  conn.on('close',()=>{if(pendingDM[fromPid]&&pendingDM[fromPid].conn===conn){delete pendingDM[fromPid];renderChatList();}});
  conn.on('error',()=>{if(pendingDM[fromPid]&&pendingDM[fromPid].conn===conn){delete pendingDM[fromPid];renderChatList();}});
  showToast(fromNick+' quiere chatear con vos',()=>openIncomingDM(fromPid));
  renderChatList();
}

function openIncomingDM(fromPid){
  const p=pendingDM[fromPid];
  if(!p)return;
  const proceed=()=>{
    delete pendingDM[fromPid];
    enterDMUI(fromPid,p.nick);
    setWaiting(true,'Conectando...');
    wireDMConn(p.conn,fromPid);
    wakeAcquire();
  };
  NK1(proceed);
}

function callPeer(p){
  const s=new MediaStream();
  if(aStream)aStream.getTracks().forEach(t=>s.addTrack(t));
  if(vStream)vStream.getTracks().forEach(t=>s.addTrack(t));
  if(!s.getTracks().length)return;
  hCall(peer.call(p,s,{metadata:meta()}));
}

function broadcast(data){Object.values(conns).filter(c=>c.open).forEach(c=>{try{c.send(data);}catch(e){}});}

function onData(d,from){
  if(!d||!d.t)return;
  switch(d.t){
    case'msg':{
      const ia=!!d.ia,nm=ia?'IA':(pNk[from]||from.slice(0,8)),col=ia?IA_COL:gUC(from),tx=cut(d.v);
      addMsg(nm,tx,false,col,d.quote,d.mid);
      hist.push({t:'msg',from,nick:nm,v:tx,col,quote:d.quote,mid:d.mid,ia});
      if(hist.length>HIST)hist.shift();
      if(ia)IA_V1(tx);else{checkMention(tx);IA_F1(nm,tx);}
      break;
    }
    case'ia':{
      if(d.v){IAS1.add(from);if(IA1.on&&from<pid)IA_OF1('Ya hay otra IA en la sala');}
      else{IAS1.delete(from);if(IAW1===from)IAW1=null;}
      IA_UI1();
      break;
    }
    case'iw':IAW1=d.v?from:(IAW1===from?null:IAW1);IA_UI1();break;
    case'ir':IA_RS1();break;
    case'meta':pNk[from]=d.v.nick||pNk[from];renderPeers();break;
    case'hist':{
      if(!d.v||!d.v.length)break;
      const known=new Set(hist.map(m=>m.mid).filter(Boolean));
      d.v.slice(-HIST).forEach(m=>{
        if(m.t!=='msg'&&m.t!=='file')return;
        if(m.mid&&known.has(m.mid))return;
        if(m.t==='msg'){
          uC[m.from]=m.col||gUC(m.from);
          m.v=cut(m.v);
          addMsg(m.nick,m.v,false,m.col,m.quote,m.mid);
        }else{
          addFileMsg(m.from,m);
        }
        hist.push(m);
        if(m.mid)known.add(m.mid);
      });
      if(hist.length>HIST)hist.splice(0,hist.length-HIST);
      break;
    }
    case'mute':{
      pMu[from]=d.v;
      if(pAu[from])pAu[from].muted=d.v;
      const el=$('cw-vp-'+from);
      if(el){const n=el.querySelector('.cw-vp-n');if(n)n.textContent=(pNk[from]||from.slice(0,8))+(d.v?' 🔇':'');}
      break;
    }
    case'file':{
      addFileMsg(from,d);
      hist.push({t:'file',from,...d});
      if(hist.length>HIST)hist.shift();
      IA_F1(pNk[from]||from.slice(0,8),STICKER_RE.test(d.name||'')?'(envio un sticker)':'(envio el archivo '+cut(d.name).slice(0,200)+')');
      break;
    }
    case'ping':{const c=conns[from];if(c&&c.open)try{c.send({t:'pong'});}catch(e){}break;}
    case'pong':pingMisses[from]=0;break;
  }
}

function pingConns(){
  Object.keys(conns).forEach(p=>{
    const c=conns[p];
    if(!c||!c.open)return;
    const misses=(pingMisses[p]||0)+1;
    if(misses>2){
      pingMisses[p]=0;
      try{c.close();}catch(e){}
      discPeer(p);
      return;
    }
    pingMisses[p]=misses;
    try{c.send({t:'ping'});}catch(e){
      pingMisses[p]=0;
      try{c.close();}catch(e2){}
      discPeer(p);
    }
  });
}

function hCall(call){
  const cp=call.peer;
  if(pCalls[cp]&&pCalls[cp]!==call){try{pCalls[cp].close();}catch(e){}}
  pCalls[cp]=call;
  call.on('stream',stream=>{
    const p=call.peer;
    if(stream.getVideoTracks().length){pVStr[p]=stream;addVidPeer(p,stream);}
    if(stream.getAudioTracks().length){
      let a=pAu[p];
      if(!a){a=mk('audio');a.autoplay=a.playsInline=1;document.body.appendChild(a);pAu[p]=a;}
      a.srcObject=new MediaStream(stream.getAudioTracks());
      if(pMu[p])a.muted=true;
    }
  });
  call.on('close',()=>{rmVid(cp);if(pCalls[cp]===call)delete pCalls[cp];});
}

function discPeer(p){
  delete connectingSince[p];
  delete pingMisses[p];
  if(pCalls[p]){try{pCalls[p].close();}catch(e){}delete pCalls[p];}
  if(IAS1.delete(p)){if(IAW1===p)IAW1=null;IA_UI1();}
  if(!conns[p]&&!pNk[p])return;
  addSys((pNk[p]||p.slice(0,8))+' salio');
  delete conns[p];delete pNk[p];
  if(pAu[p]){pAu[p].pause();pAu[p].srcObject=null;pAu[p].remove();delete pAu[p];}
  rmVid(p);renderPeers();updateRoomCount();
  refreshWaitState(curDM?'Reconectando...':'Conexion perdida, esperando...');
}

function connectMissing(activePeers){
  if(!peer||peer.destroyed)return;
  (activePeers||[]).forEach(p=>{
    if(p.pid===pid||conns[p.pid])return;
    const since=connectingSince[p.pid];
    if(since&&Date.now()-since.t<20000)return;
    if(since&&since.c){try{since.c.close();}catch(e){}}
    pNk[p.pid]=p.nick||pNk[p.pid]||p.pid.slice(0,8);
    const c=peer.connect(p.pid,{metadata:meta(),reliable:true});
    if(!c){delete connectingSince[p.pid];return;}
    connectingSince[p.pid]={t:Date.now(),c};
    onConn(c);
  });
}

async function enterRoom(cfg){
  $('cw-msgs').innerHTML='';$('cw-vl').innerHTML='';$('cw-vg').classList.remove('on');
  conns={};pAu={};pVStr={};pMu={};pNk={};connectingSince={};pingMisses={};pCalls={};
  hist=[];domCount=0;curCfg=cfg;

  $('cw-ch-nm').textContent=cfg.label.length>26?cfg.label.slice(0,26)+'…':cfg.label;
  $('cw-ch-sb').textContent='Conectando...';
  $('cw-bm').style.display='';$('cw-bv').style.display='';
  $('cw-ch-inv').style.display='';
  $('cw-lobby').classList.add('hid');$('cw-chat').classList.add('on');
  setWaiting(true,'Conectando...');

  try{await initPeer();}catch(e){showToast('Error al conectar');return goBack();}

  let data;
  try{await SL_L1();SL_O.pw=cfg.roomPw||'';SL_O.nick=nick;data=await SLC1.join(cfg.roomId,pid);}
  catch(e){showToast(e.status===403?'Contrasena incorrecta':(e.status===429?'Demasiados intentos, espera un rato':'Error al unirse'));return goBack();}

  curRoom=cfg.roomId;
  wakeAcquire();maybeShowSharePrompt();
  addSys('Uniendose a la sala como '+nick);
  navigator.clipboard.writeText(SLM.SL_U1(cfg.roomId)).then(()=>showToast('Enlace copiado al portapapeles'),()=>{});

  connectMissing(data.peers);
  updateRoomCount();refreshWaitState('Esperando a que alguien mas se conecte...');
  startAudio();
  startPresenceLoop();
}

function startPresenceLoop(){
  stopPresenceLoop();
  pingIv=setInterval(()=>{if(curRoom)pingConns();},PING);
}
function SL_O1(l){
  if(!curRoom)return;
  const active=new Set(l.map(p=>p.pid));
  Object.keys(conns).forEach(p=>{if(!active.has(p))discPeer(p);});
  connectMissing(l);
  updateRoomCount();
}
function stopPresenceLoop(){
  if(pingIv){clearInterval(pingIv);pingIv=null;}
}

function updateRoomCount(){
  if(!curRoom)return;
  const n=Object.keys(conns).length+1;
  $('cw-ch-sb').textContent=(curCfg&&curCfg.roomPw?'🔒 ':'🔗 ')+n+' en sala';
}

async function startAudio(){
  try{
    aStream=await navigator.mediaDevices.getUserMedia({audio:{echoCancellation:true,noiseSuppression:true},video:false});
    Object.keys(conns).forEach(p=>callPeer(p));
  }catch(e){}
}

$('cw-ch-inv').onclick=()=>{
  const p=$('cw-iv');
  if(p.classList.toggle('on'))QR_D1(p);
};

const IA_OP={expectedInputs:[{type:'text',languages:['es']}],expectedOutputs:[{type:'text',languages:['es']}]};
const IA_SC={type:'object',properties:{responder:{type:'boolean'},mensaje:{type:'string'}},required:['responder','mensaje']};
const IA_DEF='Sos un integrante mas de este chat grupal y te llamas IA. Cada mensaje llega como "Nombre: texto". Participa como un integrante mas del grupo, manteniendo la coherencia con todo el contexto de la conversacion.';
let IA1={on:false,s:null,b:false,r:false,q:[],ac:null,nc:false},IAS1=new Set(),IAW1=null,IA_VO=LS1('cw_vo')!=='0',IA_SYS=LS1('cw_ia')||IA_DEF;

function IA_UI1(){
  $('cw-bs').style.display=IAS1.size&&self.speechSynthesis?'':'none';
  $('cw-bs').style.opacity=IA_VO?1:.4;
  $('cw-ia-on').textContent=IA1.on?'Dejar de prestar mi IA':'Prestar mi IA';
  $('cw-iaw').style.display=IAW1?'block':'none';
  if(curView==='participants')renderPeers();
  IA_CX1();
}
function IA_CX1(){
  const s=IA1.s;
  if(IA1.on&&s&&typeof s.contextUsage==='number')$('cw-ia-st').textContent='IA activa · contexto '+s.contextUsage+' / '+s.contextWindow;
}
function IA_V1(t){
  if(!IA_VO||!self.speechSynthesis||!t)return;
  const u=new SpeechSynthesisUtterance(t.replace(/[*_#`>~|]/g,'')),v=speechSynthesis.getVoices().find(x=>/^es/i.test(x.lang));
  if(v)u.voice=v;
  u.lang=(v&&v.lang)||'es';
  speechSynthesis.speak(u);
}
async function IA_MK1(mon){
  const ctx=hist.filter(m=>m.t==='msg').slice(-40).map(m=>m.nick+': '+m.v).join('\n');
  const s=await LanguageModel.create({...IA_OP,initialPrompts:[{role:'system',content:IA_SYS+(ctx?'\n\nConversacion hasta ahora:\n'+ctx:'')}],signal:IA1.ac.signal,...(mon?{monitor:mon}:{})});
  s.addEventListener('contextoverflow',()=>addSys('La IA olvido los mensajes mas viejos'));
  return s;
}
async function IA_ON1(){
  if(IA1.on)return IA_OF1();
  if(!inAnyChat())return;
  if(IAS1.size){showToast('Ya hay una IA en la sala');return;}
  const st=$('cw-ia-st'),bt=$('cw-ia-on');
  let a;
  try{a=await LanguageModel.availability(IA_OP);}catch(e){a='unavailable';}
  if(a==='unavailable'){st.textContent='Este equipo no tiene IA integrada';return;}
  st.textContent=a==='available'?'Iniciando IA...':'Bajando el modelo...';
  bt.disabled=true;
  IA1.ac=new AbortController();
  try{IA1.s=await IA_MK1(m=>m.addEventListener('downloadprogress',e=>{st.textContent='Bajando el modelo '+Math.round((e.loaded||0)*100)+'%';}));}
  catch(e){st.textContent='Error IA '+((e&&e.name)||'');bt.disabled=false;return;}
  bt.disabled=false;
  if(!inAnyChat()){try{IA1.s.destroy();}catch(e){}IA1.s=null;return;}
  IA1.on=true;IA1.nc=false;IAS1.add(pid);
  broadcast({t:'ia',v:1});
  addSys('Prestaste tu IA a la sala');
  IA_UI1();
}
function IA_OF1(why){
  if(!IA1.on&&!IA1.s)return;
  const was=IA1.on;
  IA1.on=false;IA1.q=[];
  try{if(IA1.ac)IA1.ac.abort();}catch(e){}
  try{if(IA1.s)IA1.s.destroy();}catch(e){}
  IA1.s=null;
  if(was){IAS1.delete(pid);broadcast({t:'ia',v:0});if(IAW1===pid){IAW1=null;broadcast({t:'iw',v:0});}}
  $('cw-ia-st').textContent='';
  if(why)showToast(why);
  IA_UI1();
}
function IA_W1(v){IAW1=v?pid:null;broadcast({t:'iw',v});IA_UI1();}
function IA_F1(n,t){
  if(!IA1.on)return;
  IA1.q.push(n+': '+t);
  IA_PU1();
}
async function IA_AS1(t){
  const o={signal:IA1.ac.signal};
  if(!IA1.nc){
    try{const j=JSON.parse(await IA1.s.prompt(t,{...o,responseConstraint:IA_SC}));return j.responder?String(j.mensaje||''):'';}
    catch(e){if(e&&(e.name==='NotSupportedError'||e.name==='TypeError'))IA1.nc=true;else throw e;}
  }
  return IA1.s.prompt(t,o);
}
function IA_SY1(v){
  v=cut(v).trim();
  if(!v||!IA1.on)return;
  const mid=newMsgId();
  broadcast({t:'msg',v,mid,ia:1});
  addMsg('IA',v,false,IA_COL,undefined,mid);
  hist.push({t:'msg',from:pid,nick:'IA',v,col:IA_COL,mid,ia:true});
  if(hist.length>HIST)hist.shift();
  IA_V1(v);
}
async function IA_PU1(){
  if(IA1.b)return;
  IA1.b=true;
  while(IA1.on&&IA1.q.length){
    const t=IA1.q.splice(0).join('\n');
    IA_W1(1);
    try{IA_SY1(await IA_AS1(t));}
    catch(e){
      if(e&&e.name==='QuotaExceededError'&&IA1.on){
        try{IA1.s.destroy();}catch(x){}
        try{IA1.s=await IA_MK1();addSys('La IA arranca de cero');IA_SY1(await IA_AS1(t));}catch(x){addSys('Error IA');}
      }else if(IA1.on&&!(e&&e.name==='AbortError'))addSys('Error IA '+((e&&e.name)||''));
    }
    if(IA1.on)IA_W1(0);
    IA_CX1();
  }
  IA1.b=false;
}
async function IA_RS1(){
  if(!IA1.on||IA1.r)return;
  IA1.r=true;IA_W1(1);
  let c;
  try{
    const tx=hist.filter(m=>m.t==='msg'&&!m.ia).slice(-80).map(m=>m.nick+': '+m.v).join('\n');
    c=await LanguageModel.create({...IA_OP,signal:IA1.ac.signal});
    IA_SY1(await c.prompt('Resume esta conversacion con una linea por participante: su postura o sus aportes principales.\n\n'+tx,{signal:IA1.ac.signal}));
  }catch(e){if(IA1.on)addSys('Error IA');}
  try{if(c)c.destroy();}catch(x){}
  IA1.r=false;
  if(IA1.on)IA_W1(0);
}
function IA_RQ1(){
  const h=[...IAS1][0];
  if(!h)return;
  if(h===pid)IA_RS1();
  else{const c=conns[h];if(c&&c.open)try{c.send({t:'ir'});}catch(e){}}
}
$('cw-bi').style.display=self.LanguageModel?'':'none';
$('cw-bi').onclick=()=>{
  const p=$('cw-ia');
  p.classList.toggle('on');
  if(p.classList.contains('on')){$('cw-ia-sy').value=IA_SYS;IA_CX1();}
};
$('cw-ia-on').onclick=IA_ON1;
$('cw-ia-ap').onclick=async()=>{
  IA_SYS=cut($('cw-ia-sy').value).trim()||IA_DEF;
  if(IA_SYS===IA_DEF)try{localStorage.removeItem('cw_ia');}catch(e){}else LS2('cw_ia',IA_SYS);
  $('cw-ia').classList.remove('on');
  if(!IA1.on)return;
  try{IA1.s.destroy();}catch(e){}
  try{IA1.s=await IA_MK1();addSys('La IA arranca de cero');}catch(e){IA_OF1('Error IA');}
};
$('cw-bs').onclick=()=>{
  IA_VO=!IA_VO;LS2('cw_vo',IA_VO?'1':'0');
  if(!IA_VO&&self.speechSynthesis)speechSynthesis.cancel();
  IA_UI1();
};

function goBack(){
  IA_OF1();IAS1.clear();IAW1=null;
  if(self.speechSynthesis)speechSynthesis.cancel();
  $('cw-ia').classList.remove('on');$('cw-iv').classList.remove('on');
  wakeRelease();
  stopPresenceLoop();
  if(curRoom){
    if(SLC1)SLC1.leave();
    Object.values(conns).forEach(c=>{try{c.close();}catch(e){}});
    conns={};pNk={};connectingSince={};pingMisses={};curCfg=null;curRoom=null;
  }else if(curDM){
    const c=conns[curDM];
    if(c){try{c.close();}catch(e){}}
    delete dmReconnectTries[curDM];
    conns={};pNk={};connectingSince={};pingMisses={};curDM=null;
  }
  Object.values(pCalls).forEach(c=>{try{c.close();}catch(e){}});
  pCalls={};
  if(aStream){aStream.getTracks().forEach(t=>t.stop());aStream=null;}
  if(vStream){vStream.getTracks().forEach(t=>t.stop());vStream=null;}
  Object.values(pAu).forEach(a=>{a.pause();a.srcObject=null;a.remove();});
  pAu={};pVStr={};pMu={};muted=false;vidOn=false;
  $('cw-msgs').innerHTML='';$('cw-vl').innerHTML='';$('cw-vg').classList.remove('on');
  domCount=0;hist=[];clearQuote();
  $('cw-bm').textContent='🎤';$('cw-bv').style.opacity='1';
  $('cw-ch-inv').style.display='none';
  $('cw-bp').style.display='';
  waiting=false;
  $('cw-mi').disabled=$('cw-sn').disabled=$('cw-fl').disabled=$('cw-bp').disabled=$('cw-be').disabled=false;
  setView('msgs');
  $('cw-chat').classList.remove('on');$('cw-lobby').classList.remove('hid');
  IA_UI1();
  renderChatList();
}
$('cw-bk').onclick=goBack;

$('cw-bm').onclick=()=>{
  if(!aStream)return;muted=!muted;
  aStream.getAudioTracks().forEach(t=>t.enabled=!muted);
  $('cw-bm').textContent=muted?'🔇':'🎤';
  broadcast({t:'mute',v:muted});
};

$('cw-bv').onclick=async()=>{
  if(!vidOn){
    try{
      vStream=await navigator.mediaDevices.getUserMedia({video:{facingMode:'user',width:{ideal:640},height:{ideal:480},frameRate:{max:24}},audio:false});
      addVidSelf();Object.keys(conns).forEach(p=>callPeer(p));
      $('cw-vg').classList.add('on');vidOn=true;$('cw-bv').style.opacity='.5';
    }catch(e){addSys('Sin acceso a camara');}
  }else{
    if(vStream){vStream.getTracks().forEach(t=>t.stop());vStream=null;}
    rmVid('me');vidOn=false;$('cw-bv').style.opacity='1';
    if(!Object.keys(pVStr).length)$('cw-vg').classList.remove('on');
  }
};

function mkVP(id,label,stream){
  let ve=$('cw-vp-'+id);
  if(!ve){
    ve=mk('div','cw-vp');ve.id='cw-vp-'+id;
    const vid=mk('video');vid.autoplay=vid.playsInline=1;if(id==='me')vid.muted=1;
    const n=mk('div','cw-vp-n');n.textContent=label;
    ve.append(vid,n);$('cw-vl').appendChild(ve);
  }
  ve.querySelector('video').srcObject=stream;
  return ve;
}
function addVidSelf(){mkVP('me',nick+' (vos)',vStream);}
function addVidPeer(p,s){mkVP(p,pNk[p]||p,s);}
function rmVid(p){const v=$('cw-vp-'+p);if(v)v.remove();delete pVStr[p];if(!Object.keys(pVStr).length&&!vidOn)$('cw-vg').classList.remove('on');}

let curView='msgs',waiting=false;
function setView(v){
  curView=v;
  $('cw-participants').classList.toggle('on',!waiting&&v==='participants');
  $('cw-sp').classList.toggle('on',!waiting&&v==='stickers');
  $('cw-msgs').classList.toggle('hid',waiting||v!=='msgs');
  $('cw-wait').classList.toggle('on',waiting);
  if(!waiting&&v==='participants')renderPeers();
  if(!waiting&&v==='stickers')renderStickerPicker();
}
function setWaiting(on,msg){
  if(waiting===on){
    if(on&&msg)$('cw-wait-tx').textContent=msg;
    return;
  }
  waiting=on;
  if(on){
    $('cw-wait-tx').textContent=msg||'Conectando...';
    $('cw-wait-img').src=(window.__CFG&&window.__CFG.waitAnim)||'';
    QR_D1($('cw-wq'));
  }
  setView(curView);
  $('cw-mi').disabled=on;$('cw-sn').disabled=on;$('cw-fl').disabled=on;
  $('cw-bp').disabled=on;$('cw-be').disabled=on;
}
function refreshWaitState(msg){
  if(!curRoom&&!curDM)return;
  const n=Object.keys(conns).length;
  if(n>0)setWaiting(false);
  else setWaiting(true,msg||(curDM?'Reconectando...':'Esperando a que alguien mas se conecte...'));
}
$('cw-bp').onclick=()=>setView(curView==='participants'?'msgs':'participants');
$('cw-be').onclick=()=>setView(curView==='stickers'?'msgs':'stickers');

function mentionUser(nickName){
  const mi=$('cw-mi');
  mi.value=(mi.value&&!mi.value.endsWith(' ')?mi.value+' ':mi.value)+'@'+nickName+' ';
  setView('msgs');
  mi.focus();
}

function renderPeers(){
  const wrap=$('cw-participants');
  wrap.innerHTML='';
  const addBubble=(label,pidLike,isMe)=>{
    const b=mk('button','cw-bubble');
    if(isMe)b.disabled=true;
    const c=mk('div','cw-bubble-c');c.style.background=gUC(pidLike);c.textContent=label.slice(0,2).toUpperCase();
    const n=mk('div','cw-bubble-n');n.textContent=label+(isMe?' (vos)':'');
    b.append(c,n);
    if(!isMe)b.onclick=()=>mentionUser(label.replace(/ 🧠$/,''));
    wrap.appendChild(b);
  };
  if(!curRoom)return;
  addBubble(nick+(IA1.on?' 🧠':''),pid||'me',true);
  Object.keys(conns).forEach(p=>addBubble((pNk[p]||p.slice(0,8))+(IAS1.has(p)?' 🧠':''),p,false));
  if(IAS1.size){const b=mk('button','B');b.style.flex='0 0 100%';b.textContent='📝 Resumen de la IA';b.onclick=()=>{setView('msgs');IA_RQ1();};wrap.appendChild(b);}
}

function trimDom(mg){if(domCount>=DOM){const f=mg.querySelector('.cw-msg,.cw-sys');if(f)f.remove();}else domCount++;}

let msgSeq=0;
function newMsgId(){return(pid||'me')+'_'+Date.now()+'_'+(msgSeq++);}

function mkBubble(nm,col,me,mid,quoteLabel){
  const d=mk('div','cw-msg'+(me?' me':''));
  if(mid)d.dataset.mid=mid;
  const bwrap=mk('div');
  const inner=mk('div','cw-msg-b');
  if(!me){
    const sn=mk('div','cw-msg-nm');sn.textContent=nm;sn.style.color=col;bwrap.appendChild(sn);
    inner.style.background=col+'26';
  }
  bwrap.appendChild(inner);
  if(me){
    d.appendChild(bwrap);
  }else{
    const avd=mk('div','cw-avi');
    avd.textContent=String(nm||'?').slice(0,2).toUpperCase();
    avd.style.background=col;
    d.append(avd,bwrap);
  }
  if(quoteLabel!=null)d.addEventListener('dblclick',()=>setQuote(nm,quoteLabel,mid));
  return{d,inner};
}

let quoting=null;
function setQuote(nickName,txt,mid){
  quoting={nick:nickName,txt:txt.length>80?txt.slice(0,80)+'…':txt,mid};
  $('cw-qb-nm').textContent=nickName;
  $('cw-qb-tx').textContent=quoting.txt;
  $('cw-qb').classList.add('on');
  $('cw-mi').focus();
}
function clearQuote(){quoting=null;$('cw-qb').classList.remove('on');}
$('cw-qb-x').onclick=clearQuote;

function renderQuoteBlock(inner,quote){
  if(!quote)return;
  const q=mk('div','cw-quote');
  const qn=mk('div','cw-quote-nm');qn.textContent=quote.nick;
  const qt=mk('div','cw-quote-tx');qt.textContent=quote.txt;
  q.append(qn,qt);
  if(quote.mid){q.style.cursor='pointer';q.onclick=e=>{e.stopPropagation();scrollToMsg(quote.mid);};}
  inner.appendChild(q);
}

function scrollToMsg(mid){
  if(!mid)return;
  const el=$('cw-msgs').querySelector(`[data-mid="${CSS.escape(mid)}"]`);
  if(!el){addSys('El mensaje original ya no esta disponible');return;}
  const reduce=matchMedia('(prefers-reduced-motion: reduce)').matches||document.body.classList.contains('low-perf');
  el.scrollIntoView({behavior:reduce?'auto':'smooth',block:'center'});
  el.classList.add('cw-flash');
  setTimeout(()=>el.classList.remove('cw-flash'),1200);
}

function addMsg(nm,txt,me,col,quote,mid){
  const mg=$('cw-msgs');
  const atBottom=mg.scrollHeight-mg.scrollTop-mg.clientHeight<80;
  trimDom(mg);
  const{d,inner}=mkBubble(nm,col,me,mid,txt);
  renderQuoteBlock(inner,quote);
  const txtEl=mk('div');txtEl.textContent=txt;inner.appendChild(txtEl);
  mg.appendChild(d);
  if(atBottom||me)mg.scrollTop=mg.scrollHeight;
}
function addSys(t){
  const mg=$('cw-msgs');trimDom(mg);
  const d=mk('div','cw-sys');d.textContent=t;
  mg.appendChild(d);mg.scrollTop=mg.scrollHeight;
}

const NOTIFY_SND=new Audio('web/adjuntos/Secret_Chat/notify.ogg');
function checkMention(text){
  if(!nick||!text)return;
  if(text.toLowerCase().includes('@'+nick.toLowerCase())){
    try{NOTIFY_SND.currentTime=0;NOTIFY_SND.play().catch(()=>{});}catch(e){}
  }
}

function sendMsg(){
  const v=$('cw-mi').value.trim().slice(0,MSG_MAX);if(!v)return;
  if(!curRoom&&!curDM)return;
  const col=gUC(pid||'me');
  const q=quoting?{...quoting}:undefined;
  const mid=newMsgId();
  broadcast({t:'msg',v,quote:q,mid});
  addMsg(nick,v,true,col,q,mid);
  hist.push({t:'msg',from:pid||'me',nick,v,col,quote:q,mid});
  if(hist.length>HIST)hist.shift();
  $('cw-mi').value='';$('cw-mi').style.height='';
  clearQuote();
  IA_F1(nick,v);
}
$('cw-sn').onclick=sendMsg;
$('cw-mi').addEventListener('keydown',e=>{if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();sendMsg();}});
$('cw-mi').addEventListener('input',function(){this.style.height='';this.style.height=Math.min(this.scrollHeight,110)+'px';});


const STICKER_MAX=1024*1024;
const STICKER_RE=/^sticker_([0-9a-f]{64})\.(webp|avif)$/;
let opfsStickersDir=null,stickerMagnetCache={};

async function getStickersDir(){
  if(opfsStickersDir)return opfsStickersDir;
  const root=await navigator.storage.getDirectory();
  const apps=await root.getDirectoryHandle('Apps',{create:true});
  const chat=await apps.getDirectoryHandle('Chat',{create:true});
  opfsStickersDir=await chat.getDirectoryHandle('Stickers',{create:true});
  return opfsStickersDir;
}
async function saveStickerBlob(fname,blob){
  const dir=await getStickersDir();
  const fh=await dir.getFileHandle(fname,{create:true});
  const w=await fh.createWritable();await w.write(blob);await w.close();
}
async function loadStickerBlob(fname){
  const dir=await getStickersDir();
  const fh=await dir.getFileHandle(fname);
  return await fh.getFile();
}
async function listStickers(){
  const dir=await getStickersDir();
  const names=[];
  for await(const[name,handle]of dir.entries()){if(handle.kind==='file')names.push(name);}
  return names;
}
async function hashBlob(blob){
  const buf=await blob.arrayBuffer();
  const h=await crypto.subtle.digest('SHA-256',buf);
  return[...new Uint8Array(h)].map(b=>b.toString(16).padStart(2,'0')).join('');
}
async function processStickerImg(file){
  if(file.type==='image/avif'){
    if(file.size<=STICKER_MAX)return{blob:file,ext:'avif'};
    alert('El sticker debe pesar menos de 1MB');
    return null;
  }
  const url=URL.createObjectURL(file);
  const img=new Image();
  const ok=await new Promise(r=>{img.onload=()=>r(true);img.onerror=()=>r(false);img.src=url;});
  URL.revokeObjectURL(url);
  if(!ok){alert('No se pudo leer la imagen');return null;}
  const cv=mk('canvas');cv.width=256;cv.height=256;
  cv.getContext('2d').drawImage(img,0,0,256,256);
  let q=0.85,blob=null,tries=0;
  do{blob=await new Promise(r=>cv.toBlob(r,'image/webp',q));q=Math.max(0.05,q-0.1);tries++;}
  while(blob&&blob.size>STICKER_MAX&&tries<12);
  return{blob,ext:'webp'};
}
async function createStickerFromFile(file){
  const result=await processStickerImg(file);
  if(!result||!result.blob)return;
  const hash=await hashBlob(result.blob);
  const fname=hash+'.'+result.ext;
  await saveStickerBlob(fname,result.blob);
  renderStickerPicker();
}

function stickerMimeFor(fname){return fname.endsWith('.avif')?'image/avif':'image/webp';}
async function mkStickerThumb(fname){
  const btn=mk('button','cw-sp-item');
  try{
    const blob=await loadStickerBlob(fname);
    btn.appendChild(imgB(blob));
  }catch(e){}
  btn.onclick=()=>{sendSticker(fname);setView('msgs');};
  return btn;
}
async function renderStickerPicker(){
  const grid=$('cw-sp');
  grid.innerHTML='';
  const addBtn=mk('button','cw-sp-add');addBtn.textContent='+';
  addBtn.onclick=()=>$('cw-sp-file').click();
  grid.appendChild(addBtn);
  const all=await listStickers();
  (await Promise.all(all.map(f=>mkStickerThumb(f)))).forEach(b=>grid.appendChild(b));
}
$('cw-sp-file').onchange=function(){
  const f=this.files[0];this.value='';if(!f)return;
  createStickerFromFile(f);
};

async function downloadStickerTorrent(dd,wrap,fname){
  const pr=mk('div','cw-torrent-pr');pr.textContent='Descargando sticker...';
  wrap.innerHTML='';wrap.appendChild(pr);
  try{
    const client=await getTorrentClient();
    client.add(dd.magnet,{store:torrentStore,destroyStoreOnDestroy:true},torrent=>{
      const file=torrent.files[0];
      if(!file||file.length>STICKER_MAX){
        pr.textContent='Sticker invalido (supera 1MB)';
        try{client.remove(torrent);}catch(e){}
        return;
      }
      torrent.on('done',async()=>{
        const blob=await file.blob();
        const realHash=await hashBlob(blob);
        if(realHash!==fname.split('.')[0]){
          pr.textContent='Sticker invalido (no coincide el hash)';
          try{client.remove(torrent);}catch(e){}
          return;
        }
        wrap.innerHTML='';
        wrap.appendChild(imgB(blob,'cw-stk'));
        saveStickerBlob(fname,blob).catch(()=>{});
      });
    });
  }catch(e){pr.textContent='Error al descargar sticker';}
}

async function sendSticker(fname){
  if(!curRoom&&!curDM)return;
  const q=quoting?{...quoting}:undefined;
  try{
    const blob=await loadStickerBlob(fname);
    const mime=stickerMimeFor(fname);
    if(stickerMagnetCache[fname]){sendStickerMsg(fname,stickerMagnetCache[fname],blob.size,q);return;}
    const file=new File([blob],'sticker_'+fname,{type:mime});
    const client=await getTorrentClient();
    client.seed(file,{name:'sticker_'+fname,store:torrentStore,destroyStoreOnDestroy:true},torrent=>{
      stickerMagnetCache[fname]=torrent.magnetURI;
      sendStickerMsg(fname,torrent.magnetURI,blob.size,q);
    });
  }catch(e){addSys('Error al enviar sticker: '+e.message);}
}
function sendStickerMsg(fname,magnet,size,quote){
  const mid=newMsgId();
  const dd={id:fname,mid,magnet,name:'sticker_'+fname,size,mime:stickerMimeFor(fname),w:0,h:0,quote};
  if(!curRoom&&!curDM)return;
  IA_F1(nick,'(envio un sticker)');
  broadcast({t:'file',...dd});
  addOwnStickerMsg(fname,dd);
  hist.push({t:'file',from:pid||'me',...dd});
  if(hist.length>HIST)hist.shift();
  clearQuote();
}
async function addOwnStickerMsg(fname,dd){
  const mg=$('cw-msgs');trimDom(mg);
  const{d,inner}=mkBubble(nick,gUC(pid||'me'),true,dd.mid,'🏷️ sticker');
  inner.classList.add('cw-sticker-msg');
  renderQuoteBlock(inner,dd.quote);
  try{
    const blob=await loadStickerBlob(fname);
    inner.appendChild(imgB(blob,'cw-stk'));
  }catch(e){}
  mg.appendChild(d);mg.scrollTop=mg.scrollHeight;
}

async function cwDlDir(){
  const root=await navigator.storage.getDirectory();
  const apps=await root.getDirectoryHandle('Apps',{create:true});
  const chat=await apps.getDirectoryHandle('Chat',{create:true});
  return await chat.getDirectoryHandle('Descargas',{create:true});
}
async function cwDlSave(file,name){
  const dir=await cwDlDir();
  const fh=await dir.getFileHandle(name,{create:true});
  await file.stream().pipeTo(await fh.createWritable());
  return await fh.getFile();
}
async function cwDlClear(){
  try{
    const root=await navigator.storage.getDirectory();
    const chat=await(await root.getDirectoryHandle('Apps')).getDirectoryHandle('Chat');
    await chat.removeEntry('Descargas',{recursive:true});
  }catch(e){}
}

async function getTorrentClient(){
  if(torrentClient)return torrentClient;
  const[wt,hcs]=await Promise.all([
    import('https://cdn.jsdelivr.net/npm/webtorrent@3.0.21/dist/webtorrent.min.js'),
    import('https://cdn.jsdelivr.net/npm/hybrid-chunk-store@1.2.6/+esm')
  ]);
  torrentStore=hcs.default||hcs;
  torrentClient=new(wt.default||wt)();
  torrentClient.on('error',e=>console.error('[webtorrent]',e.message));
  return torrentClient;
}

async function sendFileP2P(f){
  const q=quoting?{...quoting}:undefined;
  try{
    const client=await getTorrentClient();
    client.seed(f,{name:f.name,store:torrentStore,destroyStoreOnDestroy:true},torrent=>{
      if(!curRoom&&!curDM)return;
      IA_F1(nick,'(envio el archivo '+f.name+')');
      const id=torrent.infoHash,mid=newMsgId();
      let w=0,h=0;
      const dd={id,mid,magnet:torrent.magnetURI,name:f.name,size:f.size,mime:f.type||'application/octet-stream',w,h,quote:q};
      const afterDims=()=>{
        broadcast({t:'file',...dd});
        addOwnFileMsg(f,dd,torrent);
        hist.push({t:'file',from:pid||'me',...dd});
        if(hist.length>HIST)hist.shift();
        clearQuote();
      };
      if(/^image\//.test(f.type)){
        const u=URL.createObjectURL(f),i=new Image();
        i.onload=()=>{dd.w=i.naturalWidth;dd.h=i.naturalHeight;URL.revokeObjectURL(u);afterDims();};
        i.onerror=()=>{URL.revokeObjectURL(u);afterDims();};
        i.src=u;
      }else afterDims();
    });
  }catch(e){addSys('Error al compartir archivo: '+e.message);}
}

$('cw-fl').onchange=function(){
  const f=this.files[0];this.value='';if(!f)return;
  sendFileP2P(f);
};

const isStk=fm=>/^image\/(avif|webp|gif|png|jpeg)$/.test(fm.mime)&&fm.size<=IM_STK&&fm.w>0&&fm.w<=600&&fm.h>0&&fm.h<=600;

function addOwnFileMsg(file,dd,torrent){
  const mg=$('cw-msgs');trimDom(mg);
  const{d,inner}=mkBubble(nick,gUC(pid||'me'),true,dd.mid,'📎 '+dd.name);
  renderQuoteBlock(inner,dd.quote);
  const wrap=mk('div');inner.appendChild(wrap);
  if(isStk(dd)){wrap.appendChild(imgB(file,'cw-stk'));}
  else{
    const btn=mk('div','cw-dl');btn.innerHTML=`⬇ ${esc(dd.name)} <span style="opacity:.6">(${fSz(dd.size)})</span>`;
    btn.onclick=()=>dlBlob(file,dd.name);
    wrap.appendChild(btn);
  }
  mg.appendChild(d);mg.scrollTop=mg.scrollHeight;
}

function downloadTorrent(dd,wrap,auto){
  const pr=mk('div','cw-torrent-pr');pr.textContent='Descargando de la red...';
  wrap.innerHTML='';wrap.appendChild(pr);
  getTorrentClient().then(client=>{
    client.add(dd.magnet,{store:torrentStore,destroyStoreOnDestroy:true},torrent=>{
      const file0=torrent.files[0];
      if(auto&&file0&&file0.length>AUTO_DL_MAX){
        try{client.remove(torrent);}catch(e){}
        renderTorrentCard(dd,wrap);
        return;
      }
      const iv=setInterval(()=>{
        if(!document.body.contains(pr))return clearInterval(iv);
        pr.textContent=`Descargando... ${(torrent.progress*100).toFixed(0)}% (${torrent.numPeers} fuentes)`;
      },500);
      torrent.on('done',async()=>{
        clearInterval(iv);
        const file=torrent.files[0];
        try{
          if(isStk(dd)){
            const blob=await file.blob();
            wrap.innerHTML='';
            wrap.appendChild(imgB(blob,'cw-stk'));
            try{torrent.destroy({destroyStore:true});}catch(e){}
            return;
          }
          pr.textContent='Guardando...';
          const local=await cwDlSave(file,String(dd.id||dd.mid||Date.now()));
          try{torrent.destroy({destroyStore:true});}catch(e){}
          wrap.innerHTML='';
          const btn=mk('div','cw-dl');btn.innerHTML=`✓ ${esc(dd.name)} <span style="opacity:.6">(${fSz(dd.size)})</span>`;
          btn.onclick=()=>dlBlob(local,dd.name);
          wrap.appendChild(btn);
          dlBlob(local,dd.name);
        }catch(e){pr.textContent='Error al guardar: '+e.message;}
      });
    });
  }).catch(e=>{pr.textContent='Error al descargar: '+e.message;});
}

function renderTorrentCard(dd,wrap){
  const card=mk('div','cw-dl');
  const sizeTxt=dd.size?` <span style="opacity:.6">(${fSz(dd.size)})</span>`:'';
  card.innerHTML=`🧲 ${esc(dd.name)}${sizeTxt}`;
  const hint=mk('div','cw-torrent-pr');hint.textContent='Clic para descargar';
  card.onclick=()=>downloadTorrent(dd,wrap);
  wrap.append(card,hint);
}

async function addFileMsg(from,dd){
  const mg=$('cw-msgs');trimDom(mg);
  const nm=pNk[from]||from,col=gUC(from);
  const{d,inner}=mkBubble(nm,col,false,dd.mid,'📎 '+dd.name);
  const sm=dd.name&&dd.name.match(STICKER_RE);
  if(sm)inner.classList.add('cw-sticker-msg');
  renderQuoteBlock(inner,dd.quote);
  const wrap=mk('div');inner.appendChild(wrap);
  mg.appendChild(d);mg.scrollTop=mg.scrollHeight;
  if(sm){
    const fname=sm[1]+'.'+sm[2];
    try{
      const blob=await loadStickerBlob(fname);
      wrap.appendChild(imgB(blob,'cw-stk'));
    }catch(e){downloadStickerTorrent(dd,wrap,fname);}
    return;
  }
  if(dd.size<=AUTO_DL_MAX)downloadTorrent(dd,wrap,true);
  else renderTorrentCard(dd,wrap);
}

let pendingShare=null;

function fileFromShareBlob(b){
  return new File([new Uint8Array(b.data)],b.name,{type:b.type||'application/octet-stream'});
}

async function checkPendingShare(){
  try{
    const r=await fetch('/_share_pending');
    const d=await r.json();
    const has=d&&((d.blobs&&d.blobs.length)||d.text||d.url);
    pendingShare=has?d:null;
    $('cw-share-banner').style.display=has?'':'none';
    if(has)maybeShowSharePrompt();
  }catch(e){}
}

async function clearPendingShare(){
  pendingShare=null;
  $('cw-share-banner').style.display='none';
  $('cw-share-prompt').style.display='none';
  try{await fetch('/_share_clear',{method:'POST'});}catch(e){}
}

function shareLabel(){
  if(!pendingShare)return'';
  const f=(pendingShare.blobs||[])[0];
  return f?f.name:(pendingShare.text||pendingShare.url||'contenido compartido');
}

function maybeShowSharePrompt(){
  if(!pendingShare||!inAnyChat())return;
  $('cw-share-prompt-tx').textContent=`Enviar "${shareLabel()}" compartido a esta sala?`;
  $('cw-share-prompt').style.display='flex';
}

$('cw-share-send').onclick=async()=>{
  if(!pendingShare)return;
  const f=(pendingShare.blobs||[])[0];
  if(f)sendFileP2P(fileFromShareBlob(f));
  else if(pendingShare.text||pendingShare.url){
    $('cw-mi').value=[pendingShare.text,pendingShare.url].filter(Boolean).join(' ');
    sendMsg();
  }
  await clearPendingShare();
};
$('cw-share-discard').onclick=clearPendingShare;

const contentEl=document.getElementById('content');
function teardown(){
  if(inAnyChat())goBack();
  QR_X1();
  stopGeoShare();
  if(peer){try{peer.destroy();}catch(e){}peer=null;pid=null;}
  document.querySelectorAll('dialog.cw-dlg').forEach(dlg=>{if(dlg.open)dlg.close();});
  document.body.style.overflow='';
  document.removeEventListener('visibilitychange',onVisChange);
  if(torrentClient){try{torrentClient.destroy({destroyStore:true});}catch(e){}torrentClient=null;}
  cwDlClear();
  window.removeEventListener('beforeunload',teardown);
  if(disqusEl)disqusEl.style.display=disqusPrevDisplay||'';
}
if(contentEl)contentEl.addEventListener('contentUnload',teardown,{once:true});
window.addEventListener('beforeunload',teardown);

renderChatList();checkPendingShare();cwDlClear();
if(/^[A-Za-z0-9_-]{1,64}$/.test(LK1)){$('cw-ad-rid').value=LK1;$('cw-ad-rpw').value='';showModal('cw-m-add');}
}();
</script>
