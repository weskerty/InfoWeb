<style>
.SK1{--SK_I:120px;text-align:center}
.SK1 [hidden]{display:none!important}
.SK_H{margin:0 0 14px}
.SK_TB,#SK_FT{justify-content:center}
.SK_SB{display:flex;gap:8px;margin:0 0 12px}
.SK_SB input{flex:1;min-width:0}
.SK_TX{color:var(--RD_MF);font-size:.9rem;margin:0 0 12px}
.sk-grid{display:grid;grid-template-columns:repeat(auto-fill,var(--SK_I));grid-auto-flow:dense;gap:8px;justify-content:center;margin-bottom:8px;min-height:40px}
.sk-it{width:var(--SK_I);height:var(--SK_I);padding:0;border-radius:14px;overflow:hidden;cursor:pointer;position:relative;background:var(--RD_M);border:2px solid var(--RD_L);box-sizing:border-box;transition:border-color .15s}
.sk-it img{width:100%;height:100%;object-fit:fill;display:block;pointer-events:none}
.sk-it[aria-pressed=true]{border-color:var(--ok)}
.sk-it[aria-pressed=true]::after{content:'✅';position:absolute;top:4px;right:6px;font-size:1.1em}
@media(hover:hover){.sk-it:hover{border-color:var(--RD_BHB)}}
.sk-ad{grid-column:1/-1;justify-self:center;border:0;color-scheme:light}
.sk-msg{color:var(--RD_MF);font-size:.9em;padding:20px 0;margin:0;grid-column:1/-1}
.sk-searching{display:flex;flex-direction:column;align-items:center;gap:8px;padding:32px 0;grid-column:1/-1;color:var(--RD_MF)}
.SK1 .SK_KL{margin:10px 0 0}
.SK_KL a{display:inline-flex}
.SK1 .SK_NT{margin:4px 0 0;color:var(--RD_MF);font-size:.72rem;opacity:.8}
.SK_PL{display:grid;grid-template-columns:repeat(auto-fill,minmax(250px,1fr));gap:10px;margin-top:14px}
.sc-fr{position:relative;display:flex;align-items:center;gap:10px;padding:8px;border-radius:14px;background:var(--RD_M);border:1px solid var(--RD_L)}
.SK_FI{position:relative;flex:none;width:96px;height:96px;border-radius:10px;overflow:hidden}
.SK_FI>img{width:100%;height:100%;object-fit:fill;display:block}
.sc-rm{position:absolute;top:4px;right:4px;width:28px;height:28px;padding:0;border:0;border-radius:8px;background:rgba(0,0,0,.65);color:var(--RD_F);cursor:pointer;line-height:1}
.SK_BG{position:absolute;top:4px;left:6px;font-size:1.1em}
.SK_TO{flex:1;min-width:0;display:flex;flex-direction:column;gap:6px;margin-right:30px}
.SK_TO button{justify-content:flex-start;padding:6px 12px}
.SK_TR{position:sticky;bottom:8px;z-index:5;width:fit-content;max-width:100%;box-sizing:border-box;margin:16px auto 0;padding:10px;border:1px solid var(--RD_L);border-radius:16px;background:var(--RD_DG);box-shadow:0 8px 30px rgba(0,0,0,.4)}
@media(orientation:portrait){body.NB_V .SK_TR{bottom:84px}}
.SK_TP{display:flex;align-items:center;gap:10px}
.SK_TI{flex:0 1 auto;min-width:0;display:flex;align-items:center;gap:6px;padding:0;border:0;background:none;color:var(--RD_F);cursor:pointer;overflow:hidden;font:inherit}
.SK_TI img{width:40px;height:40px;border-radius:8px;object-fit:fill;flex:none}
.SK_TI b{flex:none;margin:0 4px}
.SK_TE{flex:none;padding:8px 12px;border:1px solid var(--RD_BB);border-radius:10px;background:var(--RD_BT);white-space:nowrap}
#SK_GW{display:inline-flex;align-items:center;gap:8px;margin-bottom:10px}
#SK_GW::before{content:'';width:18px;height:18px;flex-shrink:0;background:var(--LK_C);-webkit-mask:var(--LK_I) center/contain no-repeat;mask:var(--LK_I) center/contain no-repeat}
#SK_WT{margin:0}
#SK_EP{white-space:pre-line}
.SK_DG{width:min(440px,calc(100vw - 32px));text-align:center}
.SK_PD[open]{display:flex;flex-direction:column;align-items:center;gap:12px}
.SK_DG>button[data-x]{margin-bottom:6px}
#SK_EC,#SK_EO,#SK_EM,.SK_DF,#SK_EP{clear:both}
.SK_NB{display:inline-block;min-width:22px;padding:0 6px;border-radius:11px;background:var(--RD_M);font-size:.8rem;line-height:22px}
.SK_VL{position:fixed;z-index:10000;margin:0;border-radius:14px;object-fit:fill;pointer-events:none;filter:drop-shadow(0 4px 12px rgba(0,0,0,.4))}
.SK_DF{display:flex;gap:10px;justify-content:center;margin-top:14px}
.SK_PD{width:min(320px,calc(100vw - 32px));text-align:center}
.sc-crop-wrap{max-width:100%;max-height:55vh;overflow:hidden}
.sc-crop-wrap img{display:block;max-width:100%;max-height:55vh}
.sc-pbar-w{width:min(240px,100%);height:8px;background:var(--RD_M);border-radius:4px;overflow:hidden;margin:0 auto}
.sc-pbar{height:100%;background:var(--ok);width:0%;transition:width .3s}
.sc-lv{display:none;border-radius:10px;width:min(180px,60vw);height:min(180px,60vw)}
.sc-ov-wrap{position:relative;flex-shrink:0}
.sc-ov-wrap canvas{display:block;border-radius:12px;touch-action:none;width:min(256px,78vw);height:min(256px,78vw);background:var(--RD_M)}
.sc-ov-it{position:absolute;touch-action:none;user-select:none;cursor:move}
.sc-ov-it img{display:block;pointer-events:none;border-radius:4px}
.sc-ov-it.ov-sel{outline:2px solid var(--ok);outline-offset:2px;border-radius:4px}
.ov-rm{position:absolute;top:-9px;right:-9px;width:22px;height:22px;padding:0;border:0;border-radius:50%;background:rgba(0,0,0,.85);color:var(--RD_F);font-size:11px;cursor:pointer;z-index:2;line-height:1}
.sc-ov-szrow{display:flex;align-items:center;gap:8px;justify-content:center}
.sc-ov-szrow span{color:var(--RD_MF);font-size:.82em;min-width:52px}
.sc-ov-res{display:flex;flex-wrap:wrap;gap:6px;justify-content:center;max-height:180px;overflow-y:auto}
.ov-it{width:72px;height:72px;padding:0;border-radius:12px;overflow:hidden;cursor:pointer;background:var(--RD_M);border:2px solid var(--RD_L);box-sizing:border-box}
.ov-it img{width:100%;height:100%;object-fit:cover;display:block;pointer-events:none}
#SK_EC,#SK_EO,#SK_EM{display:flex;flex-direction:column;align-items:center;gap:10px;width:100%}
#SK_MC{display:flex;flex-direction:column;align-items:center;gap:8px;width:100%}
#SK_MS{width:min(280px,100%)}
</style>

<div class="SK1" id="SK1">
<h2 class="NB_TT SK_H">🎨 Stickers para WhatsApp</h2>
<div class="BS1 SK_TB" id="SK_TB">
<button type="button" data-t="b" aria-pressed="true">🔍 Buscar</button>
<button type="button" data-t="p" aria-pressed="false">📦 Tu pack <span id="SK_PN" class="SK_NB">0</span></button>
<button type="button" data-t="t" aria-pressed="false">✈️ Telegram</button>
</div>
<section id="SK_B">
<form class="SK_SB" id="SK_SF"><input id="sk-q" type="search" placeholder="Buscar en KLIPY" aria-label="Buscar stickers" enterkeyhint="search"><button id="SK_SBB" aria-label="Buscar">🔍</button></form>
<div class="BS1" id="SK_FT">
<button type="button" data-f="" aria-pressed="true">Todos</button>
<button type="button" data-f="sticker" aria-pressed="false">Stickers</button>
<button type="button" data-f="gif" aria-pressed="false">GIF</button>
<button type="button" data-f="static_meme" aria-pressed="false">Memes</button>
<button type="button" data-f="clip" aria-pressed="false">Clips</button>
</div>
<div id="sk-grid" class="sk-grid"></div>
<div id="sk-pg" class="PG1"></div>
<p class="SK_KL"><a href="https://klipy.com/" target="_blank" rel="noopener"><img src="web/adjuntos/Stickers_para_WhatsApp/KLIPY.svg" width="120" height="20" alt="Powered by KLIPY"></a></p>
<p class="SK_NT">Los stickers pueden tardar hasta 30 minutos en llegar. No repitas el pedido: los repetidos se ignoran.</p>
</section>
<section id="SK_P" hidden>
<p class="SK_TX">Subi fotos, GIF o videos (se usan los primeros 10s) o elegi stickers en Buscar.</p>
<button type="button" id="SK_AD" class="RD_B1">📤 Agregar fotos, GIF o videos</button>
<input type="file" id="sc-in" accept="image/*,video/*" multiple hidden>
<div id="SK_PL" class="SK_PL"></div>
</section>
<section id="SK_T" hidden>
<p class="SK_TX">Pega el enlace de un pack de Telegram (t.me/addstickers/...). Se envian hasta 30 stickers.</p>
<form class="SK_SB" id="SK_TF"><input id="SK_TQ" type="text" inputmode="url" placeholder="https://t.me/addstickers/..." aria-label="Enlace del pack de Telegram"><button>Preparar</button></form>
<div id="SK_TS" role="status"><p id="SK_TL" class="SK_TX"></p><div class="sc-pbar-w" id="SK_TW" hidden><div class="sc-pbar" id="SK_TBR"></div></div></div>
</section>
<div id="SK_TR" class="SK_TR" hidden>
<p id="SK_WT" class="SK_TX" role="status" hidden></p>
<div id="SK_TP" class="SK_TP"><button type="button" id="SK_TV" class="SK_TI"></button><button type="button" id="sk-cf" class="RD_B1 GL_C">Enviar ➤</button></div>
</div>
<dialog id="SK_ER" class="DX1 SK_DG"><button data-x="1" aria-label="Cerrar">✕</button><p id="SK_EP" role="alert"></p></dialog>
<dialog id="SK_GD" class="DX1 SK_DG"><button data-x="1" aria-label="Cerrar">✕</button><p>✅ Listo</p><a id="SK_GW" class="RD_B1 GL_C lk-wa" href="#" target="_blank" rel="noopener">Entrar al Grupo</a><p>y Envia esto:<br><button type="button" id="SK_GC" class="RD_B1"></button></p></dialog>
<dialog id="SK_DG" class="DX1 SK_DG">
<button data-x="1" aria-label="Cancelar">✕</button>
<div id="SK_EC" hidden><div class="sc-crop-wrap"><img id="sc-crop-img" alt=""></div><button type="button" id="SK_CN">Sin recorte</button></div>
<div id="SK_EO" hidden>
<div class="sc-ov-wrap" id="sc-ov-wrap"><canvas id="sc-ov-c" width="256" height="256"></canvas></div>
<div class="sc-ov-szrow"><button type="button" id="ov-sm" aria-label="Achicar">−</button><span id="ov-sz-lbl">64px</span><button type="button" id="ov-lg" aria-label="Agrandar">+</button></div>
<form class="SK_SB" id="sc-ov-f"><input id="sc-ov-q" type="search" placeholder="Buscar en KLIPY" aria-label="Buscar imagen"><button aria-label="Buscar">🔍</button><button type="button" id="sc-ov-up" aria-label="Subir imagen">📁</button></form>
<input type="file" id="sc-ov-fi" accept="image/*" hidden>
<div class="sc-ov-res" id="sc-ov-res"></div>
</div>
<div id="SK_EM" hidden>
<div class="BS1" id="SK_MO"><button type="button" id="SK_M0" aria-pressed="true">Sin sonido</button><button type="button" id="SK_MV" aria-pressed="false">🎬 Sonido del video</button><button type="button" id="SK_MB" aria-pressed="false">📁 Elegir audio</button><button type="button" id="SK_MR" aria-pressed="false">🎤 Grabar</button></div>
<input type="file" id="SK_MF" accept="audio/*,video/*" hidden>
<div id="SK_MC" hidden><p id="SK_ML" class="SK_TX"></p><input type="range" id="SK_MS" min="0" max="0" step="0.5" value="0" aria-label="Desde"><button type="button" id="SK_MP">▶️ Escuchar</button></div>
<audio id="SK_AU" preload="metadata" hidden></audio>
<p class="SK_TX">Hasta 10s de sonido. Los stickers con sonido son nuevos en WhatsApp: si el telefono no los muestra, actualiza WhatsApp.</p>
</div>
<div class="SK_DF"><button type="button" id="SK_DC">Cancelar</button><button type="button" id="SK_DK">✅ Listo</button></div>
</dialog>
<dialog id="SK_PD" class="SK_PD"><img id="sc-ck" class="wait-anim" alt=""><canvas id="sc-lv" class="sc-lv" width="256" height="256"></canvas><div id="sc-prog-lbl"></div><div class="sc-pbar-w"><div class="sc-pbar" id="sc-pbar"></div></div></dialog>
</div>

<script>
(function(){
  const ADS=true,MU=true,KY='gCkt49niqCB9S2nlTLshWVfj8DOHunjpQCc8dAhJaxWhWfeZfvKVMmhvA9LeGR4W';
  const SK_MX=10,GAP=8,PG_FALLBACK=6,TG_W=75;
  const ITEM=innerWidth<480?86:120;
  const MAX_SZ=20*1024*1024,DIM=256,TARGET=900*1024,AU_MX=1024*1024,AU_S=10;
  const MAXFR=150,VID_MAX=10,VID_FPS=15,THM=512;
  const ID_OK=typeof ImageDecoder!=='undefined';
  const SD_RX=/^[a-f0-9]{12}$/;
  const $=id=>document.getElementById(id);
  const N3=n=>String(n).padStart(3,'0');
  const WA=window.__CFG?.waitAnim||'';
  let FFP=null,GONE=false,SB=0,TG_B=0,ED=null,ED_W=0,EA={},cropper=null,lastQ=null;
  let R=[],RF=[],PS=[],FT='',pg=0,P=[];
  let ovNS=64,ovSel=-1;
  const HM=new Map();

  const gEl=$('sk-grid'),pgEl=$('sk-pg'),ERD=$('SK_ER'),GD=$('SK_GD'),qEl=$('sk-q'),inEl=$('sc-in');
  const DG=$('SK_DG'),PD=$('SK_PD'),pBar=$('sc-pbar'),pLbl=$('sc-prog-lbl'),cropImg=$('sc-crop-img');
  const TR=$('SK_TR'),AU=$('SK_AU');
  const SN_U='web/recursos/notificaciones/cat.mp3';
  let SN_A=null;
  const ED_S={c:$('SK_EC'),o:$('SK_EO'),m:$('SK_EM')};
  $('SK1').style.setProperty('--SK_I',ITEM+'px');
  $('sc-ck').src=WA;

  let _GF=window.GridFit||null,_GFp=null,SW=null,PG=PG_FALLBACK,_gfRo=null,_gfPending=false;
  function loadGF(){
    if(_GF)return Promise.resolve(_GF);
    if(_GFp)return _GFp;
    _GFp=new Promise(res=>{
      const s=document.createElement('script');
      s.src='web/js/lib/GridFit.js';
      s.onload=()=>{_GF=window.GridFit;res(_GF)};
      s.onerror=()=>res(null);
      document.head.appendChild(s);
    });
    return _GFp;
  }
  if(!document.body.classList.contains('low-perf')){
    loadGF().then(gf=>{
      if(!gf)return;
      const scheduleGF=()=>{
        if(_gfPending)return;_gfPending=true;
        (window.requestIdleCallback||(cb=>setTimeout(cb,1)))(()=>{
          _gfPending=false;
          if(!gEl.clientWidth)return;
          const n=gf.itemsPerPage(gEl,ITEM,ITEM,GAP,140);
          if(n!==PG){PG=n;if(RF.length){PS_1();renderPage(0);}}
        });
      };
      scheduleGF();
      _gfRo=new ResizeObserver(scheduleGF);
      _gfRo.observe(gEl);
    });
  }

  function ER_D1(m){
    if(GONE)return;
    const p=$('SK_EP'),l=ERD.open?p.textContent.split('\n'):[];
    if(!l.includes(m))l.push(m);
    p.textContent=l.join('\n');
    if(!ERD.open)ERD.showModal();
  }
  ERD.querySelector('[data-x]').onclick=()=>ERD.close();
  GD.querySelector('[data-x]').onclick=()=>GD.close();
  function setProg(p,l){pBar.style.width=p+'%';if(l!=null)pLbl.textContent=l;}
  function getCID(){try{let id=localStorage.getItem('sk_cid');if(!id){id=crypto.randomUUID();localStorage.setItem('sk_cid',id);}return id;}catch{return 'anon';}}
  function KN_1(it){
    if(it.type==='ad')return it.content?{type:'ad',content:it.content,width:it.width,height:it.height}:null;
    const f=it.file,url=f&&(typeof f.webp==='string'?f.webp:f.sm?.webp?.url);
    return url?{url,title:it.title||'',type:it.type,blur_preview:it.blur_preview||'',s:it.slug}:null;
  }
  const KT={sticker:'stickers',gif:'gifs',static_meme:'static-memes',clip:'clips'};
  function KH_1(l){if(KY)l.forEach(it=>{if(it.s&&KT[it.t])fetch(`https://api.klipy.com/api/v1/${KY}/${KT[it.t]}/share/${encodeURIComponent(it.s)}`,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({customer_id:getCID(),q:it.q})}).catch(()=>{});});}
  async function KS_1(q,ad){
    if(KY)try{
      const p=new URLSearchParams({page:1,per_page:50,customer_id:getCID(),locale:'PY',content_filter:'off'}),a=ad?'&'+new URLSearchParams({'ad-min-width':50,'ad-max-width':Math.min(400,innerWidth-32),'ad-min-height':50,'ad-max-height':250,'ad-device-w':screen.width,'ad-device-h':screen.height,'ad-pxratio':devicePixelRatio,'ad-language':'ES'}):'';
      if(q)p.set('q',q);
      const rs=await Promise.all(['stickers','gifs','static-memes','clips'].map(e=>fetch(`https://api.klipy.com/api/v1/${KY}/${e}/${q?'search':'trending'}?${p}${e==='stickers'?a:''}`).then(r=>r.json())));
      const data=[];
      for(const r of rs){if(!r.result)throw 0;for(const it of r.data?.data||[]){const n=KN_1(it);if(n)data.push(n);}}
      return {data};
    }catch{}
    const p=new URLSearchParams({cid:getCID()});if(q)p.set('q',q);if(!ad)p.set('ad','0');
    const r=await fetch('/api/stickers?'+p);if(!r.ok)throw new Error(r.status);return r.json();
  }
  function BT_1(t,l,c){const b=document.createElement('button');b.type='button';if(c)b.className=c;b.textContent=t;b.setAttribute('aria-label',l);b.title=l;return b;}
  function LD_1(t){const d=document.createElement('div');d.className='sk-searching';const i=document.createElement('img');i.className='wait-anim';i.src=WA;i.alt='';const s=document.createElement('span');s.textContent=t;d.append(i,s);return d;}
  function MS_1(t){const p=document.createElement('p');p.className='sk-msg';p.textContent=t;return p;}
  function IMG_U1(u){return new Promise((res,rej)=>{const i=new Image();i.onload=()=>res(i);i.onerror=()=>rej(new Error('img'));i.src=u;});}
  async function IMG_L1(b){const u=URL.createObjectURL(b);try{return await IMG_U1(u);}finally{URL.revokeObjectURL(u);}}
  const TG_IP=q=>/(?:t\.me\/addstickers\/|addstickers\/)/.test(q);
  const TG_PN=q=>{const m=q.match(/(?:t\.me\/addstickers\/|addstickers\/)([^/?#\s]+)/);return m?m[1]:q;};

  function TB_1(t){
    document.querySelectorAll('#SK_TB button').forEach(b=>b.setAttribute('aria-pressed',b.dataset.t===t));
    $('SK_B').hidden=t!=='b';$('SK_P').hidden=t!=='p';$('SK_T').hidden=t!=='t';
    if(t==='p')PL_R();
    TR_R();
  }
  $('SK_TB').onclick=e=>{const b=e.target.closest('button');if(b)TB_1(b.dataset.t);};

  const PK_F=u=>P.find(x=>x.u===u);
  function FR_1(it){for(const k of ['pv','pc'])if(it[k]?.startsWith('blob:'))URL.revokeObjectURL(it[k]);it.ov.forEach(o=>{if(o.src?.startsWith('blob:'))URL.revokeObjectURL(o.src);});}
  function PK_AD(it){it.ov=it.ov||[];P.push(it);UP_1();}
  function PK_RM(it){const i=P.indexOf(it);if(i<0)return;FR_1(it);P.splice(i,1);UP_1();}
  function UP_1(){$('SK_PN').textContent=P.length;TR_R();if(!$('SK_P').hidden)PL_R();gEl.querySelectorAll('.sk-it').forEach(b=>b.setAttribute('aria-pressed',!!PK_F(b._u)));}

  function TR_R(){
    $('SK_TP').hidden=!P.length;
    TR.hidden=!P.length&&$('SK_WT').hidden;
    const v=$('SK_TV');v.textContent='';
    const b=document.createElement('b');b.textContent=P.length+'/'+SK_MX;v.append(b);
    const e=$('SK_P').hidden,n=innerWidth<480;
    (e&&n?[]:P.slice(n?-2:-4)).forEach(it=>{const m=document.createElement('img');m.src=it.pc||it.pv;m.alt='';v.append(m);});
    if(e){const s=document.createElement('span');s.className='SK_TE';s.textContent='✏️ Editar';v.append(s);}
    v.setAttribute('aria-label',(e?'Editar tu pack: ':'Ver tu pack: ')+P.length+' stickers');
  }
  $('SK_TV').onclick=()=>TB_1('p');

  function SN_P(){if(SN_A)return;SN_A=new Audio(SN_U);SN_A.muted=true;SN_A.play().then(()=>{SN_A.pause();SN_A.currentTime=0;SN_A.muted=false;}).catch(()=>{SN_A.muted=false;});}
  function SN_1(){try{navigator.vibrate?.(800);}catch{}if(SN_A){SN_A.currentTime=0;SN_A.play().catch(()=>{});}}
  async function WT_1(sid,w,el){
    const tx=n=>{el.textContent=n?'⏳ En espera: '+n+(n>1?' personas':' persona')+' antes que vos. Te avisamos con un sonido.':'⏳ Preparando tus stickers...';};
    tx(w);el.hidden=false;TR_R();
    while(!GONE){
      await new Promise(r=>setTimeout(r,60000));
      if(GONE)break;
      let j=null;
      try{const r=await fetch('/api/stickers?sid='+sid,{cache:'no-store'});if(r.status===404)throw new Error('404');if(r.ok)j=await r.json();}catch(e){if(e.message==='404')throw e;}
      if(j){if(j.e)throw new Error('servidor');if(j.ok)return j;tx(j.w|0);}
    }
    throw new Error('salida');
  }
  let TSP=null;
  const TL_1=()=>window.TS1?Promise.resolve():TSP||(TSP=new Promise((ok,no)=>{const s=document.createElement('script');s.src='web/js/lib/Turnstile.js';s.onload=ok;s.onerror=()=>{TSP=null;no(new Error('verificacion'))};document.head.appendChild(s)}));
  const TK_1=()=>TL_1().then(()=>window.TS1()).catch(()=>{throw new Error('verificacion')});
  const ER_1=e=>e.message==='sinwa'?'✖️ Servidor Saturado 😿':e.message==='503'?'Servidor ocupado, proba en un minuto':e.message==='403'||e.message==='verificacion'?'Error verificacion, recarga la pagina':null;
  const RS_1=j=>{const g=(Array.isArray(j.g)?j.g:[]).filter(u=>/^https:\/\/chat\.whatsapp\.com\/\S+$/.test(u));if(!g.length)throw new Error('sinwa');return {g,m:String(j.m||'')};};

  function OK_1(r){
    if(GONE)return;
    SN_1();
    const b=$('SK_GC'),w=$('SK_GW'),c=()=>navigator.clipboard?.writeText(r.m)||Promise.reject();
    const GJ=()=>{try{const a=JSON.parse(localStorage.getItem('SK_GJ'));return Array.isArray(a)?a:[];}catch{return [];}};
    const u=GJ().find(x=>r.g.includes(x))||r.g[Math.random()*r.g.length|0];
    w.href=u;
    w.onclick=()=>{c().catch(()=>{});try{localStorage.setItem('SK_GJ',JSON.stringify([u,...GJ().filter(x=>x!==u)].slice(0,5)));}catch{}};
    b.textContent=r.m;
    b.onclick=()=>c().then(()=>{b.textContent='Copiado!';setTimeout(()=>{if(b.textContent==='Copiado!')b.textContent=r.m;},2000);}).catch(()=>{});
    if(!GD.open)GD.showModal();
    c().catch(()=>{});
  }

  async function doFetch(q){
    if(SB)return;SB=1;
    const btn=$('SK_SBB');btn.disabled=true;
    gEl.textContent='';gEl.append(LD_1('Buscando'));pgEl.textContent='';
    try{
      const j=await KS_1(q,ADS);
      R=(j.data||[]).filter(x=>x.type==='ad'?ADS&&x.content:x.url);lastQ=q;
      FL_1();
    }catch(e){gEl.textContent='';gEl.append(MS_1('Error Klipy '+e.message));}
    finally{setTimeout(()=>{SB=0;btn.disabled=false;},1500);}
  }

  function PS_1(){PS=[];RF.filter(x=>x.type!=='ad').forEach((x,i)=>{if(i%PG===0)PS.push([]);PS.at(-1).push(x);});if(!PS.length)PS.push([]);RF.filter(x=>x.type==='ad').forEach((x,i)=>PS[i]?.splice(1,0,x));}
  function FL_1(){
    RF=FT?R.filter(x=>x.type===FT||x.type==='ad'):R;
    if(!RF.some(x=>x.type!=='ad'))RF=[];
    pg=0;PS_1();
    if(RF.length)renderPage(0);else{gEl.textContent='';pgEl.textContent='';gEl.append(MS_1('Sin resultados'));}
  }
  $('SK_FT').onclick=e=>{
    const b=e.target.closest('button');if(!b)return;
    FT=b.dataset.f;$('SK_FT').querySelectorAll('button').forEach(x=>x.setAttribute('aria-pressed',x===b));
    if(R.length)FL_1();
  };
  $('SK_SF').onsubmit=e=>{
    e.preventDefault();
    const q=qEl.value.trim();
    if(TG_IP(q)){TB_1('t');$('SK_TQ').value=q;SN_P();TG_1(q);return;}
    if(q!==lastQ)doFetch(q);
  };

  function CD_1(it,v){
    const b=document.createElement('button');b.type='button';b.className='sk-it';b._u=it.url;b._k=it;
    b.setAttribute('aria-pressed',!!PK_F(it.url));
    if(it.title)b.title=it.title;
    const m=document.createElement('img');m.alt=it.title||'Sticker';m.decoding='async';
    if(v||!it.blur_preview)m.src=it.url;
    else{m.src=it.blur_preview;const r=new Image();r.onload=()=>{m.src=it.url};r.src=it.url;}
    b.append(m);return b;
  }

  function AD_1(it){
    const f=document.createElement('iframe');f.className='sk-ad';f.title='Anuncio';f.scrolling='no';
    f.sandbox='allow-scripts allow-popups allow-popups-to-escape-sandbox';
    f.width=it.width;f.height=it.height;f.srcdoc=it.content;gEl.append(f);
  }

  function renderPage(p,sw){
    const dir=p>pg?1:p<pg?-1:0;
    pg=p;gEl.textContent='';
    PS[p].forEach(it=>it.type==='ad'?AD_1(it):gEl.append(CD_1(it)));
    renderPg();
    if(sw)return;
    if(SW)SW.pre();
    gEl.style.setProperty('--d',dir?(dir>0?'24px':'-24px'):'0px');
    gEl.classList.remove('AN1');void gEl.offsetWidth;gEl.classList.add('AN1');
    if(dir)$('SK_B').scrollIntoView({behavior:'smooth',block:'start'});
  }

  function renderPg(){
    if(!_GF){loadGF().then(g=>{if(g)renderPg()});return}
    if(!SW){SW=_GF.SW1(gEl,{n:()=>PS.length,p:()=>pg,ok:()=>!$('SK_B').hidden,go:i=>renderPage(i,1),
      fill:(el,i)=>PS[i].forEach(it=>{if(it.type!=='ad')el.append(CD_1(it,1));else{const d=document.createElement('div');d.className='sk-ad';d.style.cssText=`width:${it.width}px;height:${it.height}px`;el.append(d);}})});SW.pre()}
    _GF.PN1(pgEl,pg,PS.length,renderPage);
  }

  gEl.onclick=e=>{
    const b=e.target.closest('.sk-it');if(!b||!b._u)return;
    const it=PK_F(b._u);
    if(it){PK_RM(it);b.setAttribute('aria-pressed','false');return;}
    if(P.length>=SK_MX){ER_D1('Maximo '+SK_MX+' stickers por pack');return;}
    PK_AD({u:b._u,pv:b._u,s:b._k.s,t:b._k.type,q:lastQ||''});b.setAttribute('aria-pressed','true');VL_1(b);
  };

  function VL_1(b){
    const n=$('SK_PN'),r=n.getBoundingClientRect(),h=document.elementFromPoint(r.left+r.width/2,r.top+r.height/2);
    const t=h&&n.parentNode.contains(h)?n:$('SK_TV').lastElementChild||$('SK_TV'),z=t.getBoundingClientRect(),m=b.querySelector('img');
    const bp=()=>t.animate([{transform:'none'},{transform:'scale(1.4)'},{transform:'none'}],{duration:350,easing:'ease-out'});
    if(!m||document.body.classList.contains('low-perf')||matchMedia('(prefers-reduced-motion: reduce)').matches)return bp();
    const s=m.getBoundingClientRect(),c=m.cloneNode();c.className='SK_VL';c.alt='';
    Object.assign(c.style,{left:s.left+'px',top:s.top+'px',width:s.width+'px',height:s.height+'px'});document.body.append(c);
    const dx=z.left+z.width/2-s.left-s.width/2,dy=z.top+z.height/2-s.top-s.height/2,k=Math.max(.15,Math.min(1,z.width/s.width));
    c.animate([{transform:'none'},{transform:`translate(${dx/2}px,${dy/2-80}px) scale(.8) rotate(-10deg)`,offset:.45},{transform:`translate(${dx}px,${dy}px) scale(${k}) rotate(8deg)`,opacity:.5}],{duration:650,easing:'ease-in-out'}).finished.then(()=>{c.remove();bp();},()=>c.remove());
  }

  function PL_R(){
    const L=$('SK_PL');L.textContent='';
    if(!P.length){L.append(MS_1('Tu pack esta vacio'));return;}
    P.forEach(it=>{
      const d=document.createElement('div');d.className='sc-fr';
      const f=document.createElement('div');f.className='SK_FI';d.append(f);
      const m=document.createElement('img');m.src=it.pc||it.pv;m.alt='';f.append(m);
      if(it.isVid){const s=document.createElement('span');s.className='SK_BG';s.textContent='🎬';f.append(s);}
      const x=BT_1('✕','Quitar','sc-rm');x.onclick=()=>PK_RM(it);d.append(x);
      const t=document.createElement('div');t.className='SK_TO';
      [['c','✂️','Recortar',!!it.crop],['o','🖼️','Imagen',it.ov.length>0],['m','🎵','Sonido',!!it.au]].filter(x=>MU||x[0]!=='m').forEach(([md,ic,lb,on])=>{
        const b=BT_1(ic+' '+lb+(on?' ✅':''),lb);b.setAttribute('aria-pressed',on);b.onclick=()=>ED_O(it,md);t.append(b);
      });
      d.append(t);L.append(d);
    });
  }

  function getVidThumb(file){
    return new Promise(res=>{
      const v=document.createElement('video'),u=URL.createObjectURL(file);
      let done=false;
      const end=r=>{if(done)return;done=true;clearTimeout(to);URL.revokeObjectURL(u);v.removeAttribute('src');v.load();res(r);};
      const to=setTimeout(()=>end(''),5000);
      v.muted=true;v.playsInline=true;v.preload='metadata';
      v.onseeked=()=>{
        const k=Math.min(1,THM/Math.max(v.videoWidth,v.videoHeight,1));
        const c=document.createElement('canvas');c.width=Math.round(v.videoWidth*k)||DIM;c.height=Math.round(v.videoHeight*k)||DIM;
        c.getContext('2d').drawImage(v,0,0,c.width,c.height);
        c.toBlob(b=>end(b?URL.createObjectURL(b):''),'image/webp',.7);
      };
      v.onerror=()=>end('');
      v.onloadedmetadata=()=>{if(!v.videoWidth)return end('');v.currentTime=Math.min(0.5,v.duration*0.1||0);};
      v.src=u;
    });
  }

  async function MK_F(f){
    const isVid=f.type.startsWith('video/'),isWebp=f.type==='image/webp';
    if(isVid){
      let pv=await getVidThumb(f),fv=!pv;
      if(fv){PD_O('Abriendo video...');try{pv=URL.createObjectURL((await FV_1(f,1))[0]);}finally{PD_C();}}
      return{file:f,pv,fv,isVid,isWebp:false,isAnim:false,sq:false,au:MU?{f,s:0,d:AU_S,v:1}:null};
    }
    const bm=await createImageBitmap(f);const r=bm.width/bm.height;bm.close();
    return{file:f,pv:URL.createObjectURL(f),isVid,isWebp,isAnim:await AN_T1(f),sq:r>=.8&&r<=1.25};
  }

  async function KF_1(it){
    if(it.file)return;
    const b=await fetch(it.u).then(r=>{if(!r.ok)throw new Error(r.status);return r.blob();});
    const ty=b.type.startsWith('image/')?b.type:'image/webp';
    const pv=it.pv;Object.assign(it,await MK_F(new File([b],'k.'+ty.split('/')[1],{type:ty})));
    if(pv?.startsWith('blob:'))URL.revokeObjectURL(pv);
  }

  async function addFiles(list){
    for(const f of list){
      if(GONE)return;
      if(P.length>=SK_MX){ER_D1('Maximo '+SK_MX+' stickers por pack');break;}
      const v=f.type.startsWith('video/');
      if(!v&&!f.type.startsWith('image/')){ER_D1('Archivo no compatible');continue;}
      if(!v&&f.size>MAX_SZ){ER_D1('Maximo 20MB por imagen');continue;}
      try{PK_AD(await MK_F(f));}catch{ER_D1(v?'Video no compatible':'Imagen no compatible');}
    }
    TB_1('p');
  }
  $('SK_AD').onclick=()=>inEl.click();
  const DP_1=l=>{const fs=[...(l||[])].filter(f=>/^(image|video)\//.test(f.type));if(!fs.length||GONE||DG.open||PD.open)return 0;addFiles(fs);return 1;};
  const DP_P=e=>{if(DP_1(e.clipboardData?.files))e.preventDefault();};
  const DP_O=e=>{if([...(e.dataTransfer?.types||[])].includes('Files'))e.preventDefault();};
  const DP_D=e=>{if(!e.dataTransfer?.files.length)return;e.preventDefault();DP_1(e.dataTransfer.files);};
  document.addEventListener('paste',DP_P);document.addEventListener('dragover',DP_O);document.addEventListener('drop',DP_D);
  inEl.onchange=e=>{const fs=[...e.target.files];inEl.value='';if(fs.length)addFiles(fs);};

  function loadCropperJS(){
    return new Promise((res,rej)=>{
      if(window.Cropper){res();return;}
      const l=document.createElement('link');l.rel='stylesheet';l.href='web/js/lib/Cropper/cropper.min.css';l.onerror=()=>{l.onerror=null;l.href='https://cdn.jsdelivr.net/npm/cropperjs@1/dist/cropper.min.css';};document.head.appendChild(l);
      const s=document.createElement('script');s.src='web/js/lib/Cropper/cropper.min.js';s.onload=res;
      s.onerror=()=>{const c=document.createElement('script');c.src='https://cdn.jsdelivr.net/npm/cropperjs@1/dist/cropper.min.js';c.onload=res;c.onerror=rej;document.head.appendChild(c);};
      document.head.appendChild(s);
    });
  }

  function CR_O(it){
    cropImg.onload=()=>loadCropperJS().then(()=>{
      if(ED?.it!==it||!DG.open||cropper)return;
      const o={viewMode:1,dragMode:'move',background:false,autoCropArea:.9};
      if(it.crop)o.data={x:it.crop.x,y:it.crop.y,width:it.crop.w,height:it.crop.h};
      cropper=new Cropper(cropImg,o);
    }).catch(()=>ER_D1('Error Recorte'));
    cropImg.onerror=()=>ER_D1('Error Recorte');
    cropImg.removeAttribute('src');cropImg.src=it.pv;
  }

  async function ED_O(it,md,h){
    if(ED||ED_W||GONE)return;
    ED_W=1;
    let t=0;
    try{
      if(!it.file){t=setTimeout(()=>PD_O('Cargando...'),300);await KF_1(it);}
    }catch(e){ER_D1('Error Klipy '+e.message);return;}
    finally{if(t){clearTimeout(t);PD_C();}ED_W=0;}
    if(!P.includes(it)||GONE||ED)return;
    ED={it,md,ok:0,sn:{crop:it.crop,ov:it.ov.map(o=>({...o})),au:it.au}};
    for(const k in ED_S)ED_S[k].hidden=k!==md;
    if(!h){const t=Math.random();HM.set(t,[it,md]);window.__HS3?.('SK',t);}
    DG.showModal();document.body.style.overflow='hidden';
    if(md==='c')CR_O(it);else if(md==='o')ovOpen(it);else MU_O(it);
  }

  $('SK_DK').onclick=()=>{
    if(!ED)return;
    const {it,md}=ED;
    if(md==='c'){if(!cropper)return;const d=cropper.getData(true);it.crop={x:d.x,y:d.y,w:d.width,h:d.height,sw:cropImg.naturalWidth,sh:cropImg.naturalHeight};}
    else if(md==='m')it.au=EA.f?{f:EA.f,s:EA.s,d:EA.d,v:MU_V()}:null;
    ED.ok=1;ED_X();
  };
  $('SK_DC').onclick=()=>ED_X();
  DG.querySelector('[data-x]').onclick=()=>ED_X();
  $('SK_CN').onclick=()=>{if(!ED)return;ED.it.crop=null;ED.ok=1;ED_X();};
  function ED_C(){
    const e=ED;ED=null;
    if(cropper){cropper.destroy();cropper=null;}
    MU_X();
    $('sc-ov-wrap').querySelectorAll('.sc-ov-it').forEach(x=>x.remove());
    document.body.style.overflow='';
    if(e){
      const a=e.ok?e.sn.ov:e.it.ov,b=new Set((e.ok?e.it.ov:e.sn.ov).map(o=>o.src));
      a.forEach(o=>{if(!b.has(o.src)&&o.src?.startsWith('blob:'))URL.revokeObjectURL(o.src);});
      if(!e.ok)Object.assign(e.it,{crop:e.sn.crop,ov:e.sn.ov,au:e.sn.au});
      if(!GONE)PV_1(e.it).then(()=>{if(!GONE){if(!$('SK_P').hidden)PL_R();TR_R();}});
      if(HM.has(history.state?.SK))history.back();
    }
  }
  function ED_X(){ED_C();if(DG.open)DG.close();}
  DG.addEventListener('close',()=>{if(!DG.open)ED_C();});
  const CS_1=e=>{
    const t=e.detail?.SK;
    if(!HM.has(t)){if(ED||DG.open)ED_X();}
    else if(!DG.open&&!ED){const [it,md]=HM.get(t);ED_O(it,md,1);}
  };
  document.addEventListener('contentState',CS_1);

  async function PV_1(it){
    if(it.pc){URL.revokeObjectURL(it.pc);it.pc=null;}
    if(!it.crop&&!it.ov.length)return;
    try{
      const img=await IMG_U1(it.pv);
      const c=document.createElement('canvas');c.width=DIM;c.height=DIM;
      const x=c.getContext('2d');DR_B1(x,img,it.crop);DR_O1(x,it.ov,0);
      const b=await new Promise(r=>c.toBlob(r,'image/webp',.8));
      if(b&&!GONE)it.pc=URL.createObjectURL(b);
    }catch{}
  }

  function MU_X(){RC_X();AU.pause();if(AU.src.startsWith('blob:'))URL.revokeObjectURL(AU.src);AU.removeAttribute('src');}
  function MU_O(it){EA=it.au?{...it.au}:{f:null,s:0,d:AU_S};$('SK_MV').hidden=!it.isVid;$('SK_MR').hidden=!window.MediaRecorder||!navigator.mediaDevices?.getUserMedia;MU_L();}
  const MU_V=()=>!!EA.f&&EA.f===ED?.it.file;
  const TM_1=s=>Math.floor(s/60)+':'+String(Math.floor(s%60)).padStart(2,'0');
  function MU_L(){
    const v=MU_V();
    $('SK_M0').setAttribute('aria-pressed',!EA.f);$('SK_MV').setAttribute('aria-pressed',v);$('SK_MB').setAttribute('aria-pressed',!!EA.f&&!v&&!EA.f.r);$('SK_MR').setAttribute('aria-pressed',!!EA.f?.r);
    MU_X();$('SK_MC').hidden=!EA.f;$('SK_MP').textContent='▶️ Escuchar';
    if(!EA.f)return;
    const S=$('SK_MS');S.hidden=v;
    AU.onloadedmetadata=()=>{
      EA.du=isFinite(AU.duration)?AU.duration:EA.f?.du||AU_S;
      S.max=Math.max(0,EA.du-1);
      EA.s=v?0:Math.min(EA.s||0,+S.max);S.value=EA.s;MU_T();
    };
    AU.onerror=()=>{if(!AU.getAttribute('src'))return;ER_D1('Audio no compatible');EA.f=null;MU_L();};
    AU.src=URL.createObjectURL(EA.f);
  }
  function MU_T(){EA.d=Math.max(1,Math.min(AU_S,(EA.du||AU_S)-EA.s));$('SK_ML').textContent=(MU_V()?'Sonido del video':EA.f.r?'🎤 Grabacion':EA.f.name)+' · desde '+TM_1(EA.s)+' · '+Math.round(EA.d)+'s';}
  $('SK_MS').oninput=e=>{EA.s=+e.target.value;MU_T();if(!AU.paused)AU.currentTime=EA.s;};
  $('SK_MP').onclick=()=>{if(!EA.f)return;if(AU.paused){AU.currentTime=EA.s;AU.play().then(()=>{$('SK_MP').textContent='⏸️ Pausa';}).catch(()=>{});}else AU.pause();};
  AU.onpause=()=>{$('SK_MP').textContent='▶️ Escuchar';};
  AU.ontimeupdate=()=>{if(AU.currentTime>=EA.s+EA.d)AU.pause();};
  $('SK_M0').onclick=()=>{EA.f=null;MU_L();};
  $('SK_MV').onclick=()=>{if(!ED)return;EA.f=ED.it.file;EA.s=0;MU_L();};
  $('SK_MB').onclick=()=>$('SK_MF').click();
  $('SK_MF').onchange=e=>{const f=e.target.files[0];e.target.value='';if(!f||!ED)return;EA.f=f;EA.s=0;MU_L();};
  let RC=null;
  function RC_X(k){const r=RC;if(!r)return;RC=null;r.k=k;clearInterval(r.t);if(r.m.state!=='inactive')r.m.stop();r.s.getTracks().forEach(x=>x.stop());$('SK_MR').textContent='🎤 Grabar';}
  $('SK_MR').onclick=async()=>{
    if(RC)return RC_X(1);
    if(!ED)return;
    let s;try{s=await navigator.mediaDevices.getUserMedia({audio:true});}catch(e){ER_D1(e.name==='NotFoundError'?'Sin microfono':'Microfono bloqueado');return;}
    if(!ED||GONE||RC){s.getTracks().forEach(x=>x.stop());return;}
    MU_X();$('SK_MC').hidden=true;
    const m=new MediaRecorder(s),ch=[],t0=Date.now(),r={m,s};
    const T=()=>{const e=(Date.now()-t0)/1000;if(e>=AU_S)return RC_X(1);$('SK_MR').textContent='⏹️ Grabando '+Math.ceil(AU_S-e)+'s';};
    m.ondataavailable=e=>{if(e.data.size)ch.push(e.data);};
    m.onstop=()=>{if(!r.k||!ED||GONE||!ch.length)return;const ty=m.mimeType||ch[0].type,f=new File(ch,'Grabacion.'+(/mp4/.test(ty)?'m4a':'webm'),{type:ty});f.r=1;f.du=Math.min(AU_S,(Date.now()-t0)/1000);EA.f=f;EA.s=0;MU_L();};
    RC=r;r.t=setInterval(T,250);m.start();T();
  };

  function FF_L1(){
    if(GONE)return Promise.reject(new Error('salida'));
    if(FFP)return FFP;
    FFP=(window.FF1?Promise.resolve():new Promise((ok,no)=>{const s=document.createElement('script');s.src='web/js/lib/FFmpeg.js';s.onload=ok;s.onerror=()=>{s.remove();no(new Error('ffmpeg'));};document.head.appendChild(s);})).then(()=>window.FF1());
    FFP.catch(()=>{FFP=null;});
    return FFP;
  }

  async function AN_T1(f){
    const h=new Uint8Array(await f.slice(0,4096).arrayBuffer());
    let s='';for(let i=0;i<h.length;i++)s+=String.fromCharCode(h[i]);
    if(s.startsWith('GIF8'))return 'gif';
    if(s.startsWith('RIFF')&&s.substr(8,4)==='WEBP')return s.indexOf('ANIM',12)>0?'webp_anim':false;
    return false;
  }

  async function AN_D1(b,ty){
    if(!ID_OK)return null;
    let dec;
    try{
      dec=new ImageDecoder({data:await b.arrayBuffer(),type:ty==='gif'?'image/gif':'image/webp'});
      await dec.tracks.ready;
    }catch{return null;}
    const tr=dec.tracks.selectedTrack;
    if(!tr||!tr.frameCount||tr.frameCount<2){try{dec.close();}catch{}return null;}
    const n=Math.min(tr.frameCount,MAXFR),fr=[];let dur=0;
    try{
      for(let i=0;i<n;i++){const r=await dec.decode({frameIndex:i});fr.push(r.image);dur+=(r.image.duration||100000)/1000;}
    }catch{fr.forEach(x=>{try{x.close();}catch{}});try{dec.close();}catch{}return null;}
    try{dec.close();}catch{}
    return {fr,fps:Math.max(1,Math.min(30,Math.round(1000/(dur/n||100))))};
  }

  function AN_F1(a){(a?.fr||[]).forEach(x=>{try{x.close();}catch{}});}

  function DR_B1(ctx,img,cd){
    if(cd){
      const sw=img.displayWidth||img.videoWidth||img.naturalWidth||img.width;
      const sh=img.displayHeight||img.videoHeight||img.naturalHeight||img.height;
      const kx=sw/cd.sw,ky=sh/cd.sh;
      ctx.drawImage(img,cd.x*kx,cd.y*ky,cd.w*kx,cd.h*ky,0,0,DIM,DIM);
    }else ctx.drawImage(img,0,0,DIM,DIM);
  }

  function DR_O1(ctx,ovs,i){
    ovs.forEach(o=>{
      const src=o.an?o.an.fr[i%o.an.fr.length]:o.img;
      try{ctx.drawImage(src,o.x-o.s/2,o.y-o.s/2,o.s,o.s);}catch{}
    });
  }

  async function OV_P1(overlays){
    const out=[];
    for(const o of overlays){
      const an=o.blob&&o.anim?await AN_D1(o.blob,o.anim):null;
      out.push({img:o.img,an,x:o.x,y:o.y,s:o.s});
    }
    return out;
  }

  async function WB_E1(it,base,ovs,fps,onp){
    const ff=await FF_L1();
    const c=document.createElement('canvas');c.width=DIM;c.height=DIM;
    const ctx=c.getContext('2d');
    const lv=$('sc-lv'),ckEl=$('sc-ck');
    const lctx=lv.getContext('2d');
    ckEl.style.display='none';lv.style.display='block';
    const nb=base.fr?base.fr.length:1;
    const no=ovs.reduce((m,o)=>Math.max(m,o.an?o.an.fr.length:1),1);
    const n=Math.min(MAXFR,Math.max(nb,no));
    const names=[];
    let op=true;
    try{
      for(let i=0;i<n;i++){
        ctx.clearRect(0,0,DIM,DIM);
        DR_B1(ctx,base.fr?base.fr[i%nb]:base.img,it.crop);
        DR_O1(ctx,ovs,i);
        if(op){const d=ctx.getImageData(0,0,DIM,DIM).data;for(let k=3;k<d.length;k+=4)if(d[k]<255){op=false;break;}}
        try{lctx.clearRect(0,0,DIM,DIM);lctx.drawImage(c,0,0,DIM,DIM);}catch{}
        const bl=await new Promise(r=>c.toBlob(r,'image/png'));
        const nm='i'+String(i).padStart(4,'0')+'.png';
        await ff.writeFile(nm,new Uint8Array(await bl.arrayBuffer()));
        names.push(nm);
        if(onp)onp((i+1)/n);
      }
      let out=null;
      for(const q of [50,43,36,29,22,15,8,1]){
        await ff.exec(['-framerate',String(fps),'-i','i%04d.png','-c:v',op?'libwebp':'libwebp_anim','-f','webp','-quality',String(q),'-loop','0','-y','o.webp']);
        out=await ff.readFile('o.webp');
        if(out.byteLength<=TARGET)break;
      }
      await ff.deleteFile('o.webp').catch(()=>{});
      return new Blob([out],{type:'image/webp'});
    }finally{
      for(const nm of names)await ff.deleteFile(nm).catch(()=>{});
      lv.style.display='none';ckEl.style.display='';
    }
  }

  async function VD_F1(file,fps){
    const v=document.createElement('video'),u=URL.createObjectURL(file),fr=[];
    v.src=u;v.muted=true;v.playsInline=true;v.preload='auto';
    try{
      await new Promise((res,rej)=>{setTimeout(()=>rej(new Error('video')),5000);v.onloadedmetadata=res;v.onerror=()=>rej(new Error('video'));});
      const dur=Math.min(v.duration||0,VID_MAX);
      if(!dur||!isFinite(dur))throw new Error('video');
      const k=Math.min(1,THM/Math.max(v.videoWidth,v.videoHeight,1));
      const o={resizeWidth:Math.max(1,Math.round(v.videoWidth*k)),resizeHeight:Math.max(1,Math.round(v.videoHeight*k)),resizeQuality:'high'};
      const n=Math.min(MAXFR,Math.max(1,Math.round(dur*fps)));
      for(let i=0;i<n;i++){
        await new Promise((res,rej)=>{
          const to=setTimeout(()=>rej(new Error('video')),3000);
          v.onseeked=()=>{clearTimeout(to);res();};
          v.onerror=()=>{clearTimeout(to);rej(new Error('video'));};
          v.currentTime=Math.min(dur-.001,i/fps);
        });
        fr.push(await createImageBitmap(v,o));
      }
      return {fr,fps};
    }catch(e){AN_F1({fr});throw e;}
    finally{URL.revokeObjectURL(u);v.removeAttribute('src');v.load();}
  }

  async function FM_1(f,fn){
    const ff=await FF_L1();
    await ff.createDir('/vc').catch(()=>{});
    await ff.mount(window.FFmpegWASM.FFFSType.WORKERFS,{files:[f]},'/vc');
    try{return await fn(ff,'/vc/'+f.name);}
    catch(e){FF_R1();throw e;}
    finally{await ff.unmount('/vc').catch(()=>{});}
  }
  function FF_R1(){if(FFP){FFP.then(f=>f.terminate()).catch(()=>{});FFP=null;}}

  function FV_1(f,n){
    return FM_1(f,async(ff,p)=>{
      await ff.exec(['-t',String(VID_MAX),'-i',p,'-an','-vf','fps='+VID_FPS+',scale='+THM+':'+THM+':force_original_aspect_ratio=decrease','-frames:v',String(n),'-y','v%04d.png']);
      const o=[];
      for(let i=1;i<=n;i++){
        const nm='v'+String(i).padStart(4,'0')+'.png';
        try{o.push(new Blob([await ff.readFile(nm)],{type:'image/png'}));}catch{break;}
        await ff.deleteFile(nm).catch(()=>{});
      }
      if(!o.length)throw new Error('video');
      return o;
    });
  }

  async function VD_F2(it){
    await FF_L1();
    const fr=[];
    try{for(const b of await FV_1(it.file,MAXFR))fr.push(await createImageBitmap(b));return {fr,fps:VID_FPS};}
    catch(e){AN_F1({fr});if(it.fv||GONE)throw e;}
    return VD_F1(it.file,VID_FPS);
  }

  async function ST_E1(it,ovs){
    const img=await IMG_L1(it.file);
    const c=document.createElement('canvas');c.width=DIM;c.height=DIM;
    const x=c.getContext('2d');DR_B1(x,img,it.crop);DR_O1(x,ovs,0);
    const b=await new Promise(r=>c.toBlob(r,'image/webp',.9));
    if(!b)throw new Error('webp');
    return b;
  }

  async function EX_1(it,onp){
    await KF_1(it);
    if(!it.isVid&&it.isWebp&&it.sq&&it.file.size<TARGET&&!it.crop&&!it.ov.length)return it.file;
    let base=null,ovs=[];
    try{
      if(it.isVid)base=await VD_F2(it);
      else if(it.isAnim)base=await AN_D1(it.file,it.isAnim);
      ovs=await OV_P1(it.ov);
      if(!base&&!ovs.some(o=>o.an))return await ST_E1(it,ovs);
      if(!base)base={img:await IMG_L1(it.file)};
      const fps=base.fps||ovs.find(o=>o.an)?.an.fps||VID_FPS;
      return await WB_E1(it,base,ovs,fps,onp);
    }finally{
      AN_F1(base);
      ovs.forEach(o=>AN_F1(o.an));
    }
  }

  function AU_1(a){
    return FM_1(a.f,async(ff,p)=>{
      try{
        const r=await ff.exec(['-ss',String(a.s),'-t',String(a.d),'-i',p,'-vn','-map_metadata','-1','-ac','1','-ar','48000','-c:a','libopus','-b:a','48k','-f','ogg','-y','a.ogg']);
        const o=r===0?await ff.readFile('a.ogg'):null;
        if(!o?.byteLength||o.byteLength>AU_MX)throw new Error('audio');
        return new Blob([o],{type:'audio/ogg'});
      }finally{await ff.deleteFile('a.ogg').catch(()=>{});}
    });
  }

  function PD_O(l){setProg(0,l);if(!PD.open)PD.showModal();document.body.style.overflow='hidden';}
  function PD_C(){if(PD.open)PD.close();document.body.style.overflow='';}
  PD.addEventListener('cancel',e=>e.preventDefault());

  $('sk-cf').onclick=async()=>{
    if(!P.length||PD.open)return;
    SN_P();
    const items=[...P];
    PD_O('Procesando...');
    let nA=0,nF=0;
    try{
      const form=new FormData(),urls=[];
      for(let i=0;i<items.length;i++){
        const it=items[i],n=N3(i+1),b0=Math.round(i/items.length*80),b1=Math.round((i+1)/items.length*80);
        const lb='Procesando '+(i+1)+'/'+items.length;setProg(b0,lb);
        if(!it.file&&!ID_OK){urls.push([i+1,it.u]);continue;}
        try{form.append('files',await EX_1(it,p=>setProg(Math.round(b0+(b1-b0)*p),lb)),n+'.webp');}catch{nF++;continue;}
        if(MU&&it.au){try{form.append('files',await AU_1(it.au),n+'.ogg');}catch{if(!it.au.v)nA++;}}
      }
      if(GONE)return;
      if(nF===items.length)throw new Error('conversion');
      if(urls.length)form.append('urls',JSON.stringify(urls));
      setProg(85,'Subiendo...');
      const res=await fetch('/api/stickers',{method:'POST',headers:{'x-ts':await TK_1()},body:form});
      if(!res.ok)throw new Error(res.status);
      let jr=await res.json();const {sid,w}=jr;
      if(!SD_RX.test(sid||''))throw new Error('sid');
      KH_1(items);
      if(!w)jr=RS_1(jr);
      items.forEach(FR_1);P=[];UP_1();
      if(w){PD_C();try{jr=RS_1(await WT_1(sid,w,$('SK_WT')));}finally{$('SK_WT').hidden=true;TR_R();}}
      OK_1(jr);
      if(nF)ER_D1(nF+' no se pudieron convertir');
      if(nA)ER_D1(nA+' sin sonido');
    }catch(e){ER_D1(ER_1(e)||'Error Stickers '+e.message);}
    finally{PD_C();}
  };

  async function TG_1(q){
    const pack=TG_PN(q.trim());
    if(TG_B)return;
    if(!/^[A-Za-z0-9_]{1,64}$/.test(pack)){ER_D1('Enlace de Telegram no valido');return;}
    TG_B=1;
    const L=$('SK_TL'),W=$('SK_TW'),B=$('SK_TBR');
    W.hidden=false;B.style.width='0%';L.textContent='Pidiendo el pack...';
    try{
      const r=await fetch('/api/stickers',{method:'POST',headers:{'Content-Type':'application/json','x-ts':await TK_1()},body:JSON.stringify({pack})});
      if(!r.ok)throw new Error(r.status);
      let jr=await r.json();const {sid,w}=jr;
      if(!SD_RX.test(sid||''))throw new Error('sid');
      if(w){W.hidden=true;jr=await WT_1(sid,w,L);}
      else await new Promise((ok,no)=>{const t0=Date.now(),iv=setInterval(()=>{
        if(GONE){clearInterval(iv);no(new Error('salida'));return;}
        const e=(Date.now()-t0)/1000;
        if(e>=TG_W){clearInterval(iv);ok();return;}
        L.textContent='Preparando el pack... '+Math.ceil(TG_W-e)+'s';B.style.width=Math.round(100*e/TG_W)+'%';
      },500);});
      L.textContent='';W.hidden=true;
      OK_1(RS_1(jr));
    }catch(e){L.textContent='';W.hidden=true;ER_D1(ER_1(e)||'Error Telegram '+e.message);}
    finally{TG_B=0;}
  }
  $('SK_TF').onsubmit=e=>{e.preventDefault();SN_P();TG_1($('SK_TQ').value);};

  function ovOpen(it){
    ovSel=-1;
    $('ov-sz-lbl').textContent=ovNS+'px';
    $('sc-ov-res').textContent='';
    $('sc-ov-q').value='';
    const c=$('sc-ov-c'),ctx=c.getContext('2d');
    ctx.clearRect(0,0,DIM,DIM);
    IMG_U1(it.pv).then(img=>{if(ED?.it===it){ctx.clearRect(0,0,DIM,DIM);DR_B1(ctx,img,it.crop);}}).catch(()=>{});
    requestAnimationFrame(ovRL);
  }

  function ovSC(){const r=$('sc-ov-c').getBoundingClientRect();return r.width>0?r.width/DIM:1;}

  function ovRL(){
    const wrap=$('sc-ov-wrap');
    wrap.querySelectorAll('.sc-ov-it').forEach(e=>e.remove());
    if(!ED)return;
    const ovs=ED.it.ov,sc=ovSC();
    ovs.forEach((ov,i)=>{
      const d=document.createElement('div');d.className='sc-ov-it'+(i===ovSel?' ov-sel':'');
      d.style.cssText='left:'+(ov.x-ov.s/2)*sc+'px;top:'+(ov.y-ov.s/2)*sc+'px;width:'+ov.s*sc+'px;height:'+ov.s*sc+'px';
      const img=document.createElement('img');img.src=ov.src;img.alt='';img.style.cssText='width:'+ov.s*sc+'px;height:'+ov.s*sc+'px';
      const rm=BT_1('✕','Quitar imagen','ov-rm');
      rm.onclick=e=>{e.stopPropagation();ovs.splice(i,1);if(ovSel===i)ovSel=-1;else if(ovSel>i)ovSel--;$('ov-sz-lbl').textContent=ovNS+'px';ovRL();};
      d.append(img,rm);
      ovDrag(d,ov,i);
      wrap.append(d);
    });
  }

  function ovDrag(el,ov,i){
    el.addEventListener('pointerdown',e=>{
      if(e.target.classList.contains('ov-rm'))return;
      ovSel=i;$('ov-sz-lbl').textContent=ov.s+'px';
      el.parentElement.querySelectorAll('.sc-ov-it').forEach(x=>x.classList.remove('ov-sel'));
      el.classList.add('ov-sel');
      el.setPointerCapture(e.pointerId);
      let lx=e.clientX,ly=e.clientY;
      const sc=ovSC();
      const mm=pe=>{
        ov.x=Math.max(ov.s/2,Math.min(DIM-ov.s/2,ov.x+(pe.clientX-lx)/sc));
        ov.y=Math.max(ov.s/2,Math.min(DIM-ov.s/2,ov.y+(pe.clientY-ly)/sc));
        lx=pe.clientX;ly=pe.clientY;
        el.style.left=(ov.x-ov.s/2)*sc+'px';
        el.style.top=(ov.y-ov.s/2)*sc+'px';
      };
      el.addEventListener('pointermove',mm);
      el.addEventListener('pointerup',()=>el.removeEventListener('pointermove',mm),{once:true});
      e.preventDefault();
    });
  }

  async function ovAdd(src0){
    if(!ED)return;
    const it=ED.it;
    try{
      let blob=src0 instanceof Blob?src0:null,src,anim=false;
      if(!blob){try{blob=await fetch(src0).then(r=>{if(!r.ok)throw 0;return r.blob();});}catch{}}
      if(!blob)throw 0;
      src=URL.createObjectURL(blob);anim=await AN_T1(blob);
      let img;
      try{img=await IMG_U1(src);}catch(e){URL.revokeObjectURL(src);throw e;}
      if(ED?.it!==it){URL.revokeObjectURL(src);return;}
      it.ov.push({img,src,blob,x:128,y:128,s:ovNS,anim});
      ovSel=it.ov.length-1;
      $('ov-sz-lbl').textContent=ovNS+'px';
      ovRL();
    }catch{ER_D1('Error Imagen');}
  }

  async function ovSrch(q){
    if(!q)return;
    const res=$('sc-ov-res');
    res.textContent='';res.append(MS_1('Buscando...'));
    try{
      const j=await KS_1(q);
      res.textContent='';
      (j.data||[]).filter(x=>x.type!=='ad'&&x.url).slice(0,16).forEach(item=>{
        const b=document.createElement('button');b.type='button';b.className='ov-it';b.setAttribute('aria-label',item.title||'Imagen');
        const img=document.createElement('img');img.alt='';img.decoding='async';img.src=item.blur_preview||item.url;
        if(item.blur_preview){const ri=new Image();ri.onload=()=>{img.src=item.url};ri.src=item.url;}
        b.append(img);b.onclick=()=>ovAdd(item.url);res.append(b);
      });
      if(!res.children.length)res.append(MS_1('Sin resultados'));
    }catch{res.textContent='';res.append(MS_1('Error Klipy'));}
  }

  function ovSz(d){
    const ov=ovSel>=0?ED?.it.ov[ovSel]:null;
    if(ov){ov.s=Math.max(16,Math.min(240,ov.s+d));$('ov-sz-lbl').textContent=ov.s+'px';ovRL();}
    else{ovNS=Math.max(16,Math.min(240,ovNS+d));$('ov-sz-lbl').textContent=ovNS+'px';}
  }
  $('ov-sm').onclick=()=>ovSz(-16);
  $('ov-lg').onclick=()=>ovSz(16);
  $('sc-ov-f').onsubmit=e=>{e.preventDefault();ovSrch($('sc-ov-q').value.trim());};
  $('sc-ov-fi').onchange=e=>{const f=e.target.files[0];e.target.value='';if(f)ovAdd(f);};
  $('sc-ov-up').onclick=()=>$('sc-ov-fi').click();

  const cont=$('content');
  if(cont)cont.addEventListener('contentUnload',()=>{
    GONE=true;
    document.removeEventListener('contentState',CS_1);HM.clear();
    document.removeEventListener('paste',DP_P);document.removeEventListener('dragover',DP_O);document.removeEventListener('drop',DP_D);
    ED_X();
    PD_C();
    P.forEach(FR_1);P=[];
    if(_gfRo){_gfRo.disconnect();_gfRo=null}
    if(SN_A){SN_A.pause();SN_A=null;}
    FF_R1();
  },{once:true});

  TL_1().then(()=>window.TS0()).catch(()=>{});

  doFetch('');
  (async()=>{
    try{
      const C={cacheName:'share-pending'},r=await caches.match('/__share_data',C);
      if(!r||Date.now()>+r.headers.get('X-Expires'))return;
      const d=await r.json(),b=d.files.filter(x=>/^(image|video)\//.test(x.type)),q=(d.url||d.text).trim();
      if(!b.length&&!TG_IP(q))return;
      const fs=await Promise.all(b.map(async x=>new File([await(await caches.match(x.key,C)).blob()],x.name,{type:x.type})));
      await caches.delete('share-pending');
      if(fs.length)return addFiles(fs);
      TB_1('t');$('SK_TQ').value=q;TG_1(q);
    }catch{}
  })();
})();
</script>

</br>

<details>
  <summary style="font-size: 1.5em; font-weight: bold;"> 🤔 ¿Como Usar?</summary>

<iframe class="EM1" loading="lazy" src="https://www.youtube.com/embed/7J9x16irofc?si=cp_GO720xz8qq6R-&amp;controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

</details>

</br>

<a href="web/paginas/apps.html" class="back-button">← Volver a Applicaciones </a>

</br>

<div id="sh" data-t="Mira, Stickers Animados para WhatsApp sin instalar nada aqui"></div>
