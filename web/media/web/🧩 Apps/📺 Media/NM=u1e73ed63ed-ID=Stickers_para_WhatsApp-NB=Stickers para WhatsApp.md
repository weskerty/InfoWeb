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
.SK1 .SK_NT a{margin-top:6px;font-size:.85rem}
.SK_PL{display:grid;grid-template-columns:repeat(auto-fill,minmax(250px,1fr));gap:10px;margin-top:14px}
.sc-fr{position:relative;display:flex;align-items:center;gap:10px;padding:8px;border-radius:14px;background:var(--RD_M);border:1px solid var(--RD_L)}
.SK_FI{position:relative;flex:none;width:96px;height:96px;border-radius:10px;overflow:hidden}
.SK_FI>img{width:100%;height:100%;object-fit:fill;display:block}
.SK_CW{position:relative;display:block;overflow:hidden;flex:none}
.SK_CW>img{position:absolute;max-width:none;object-fit:fill}
.SK_FI>.SK_CW{width:100%;height:100%}
.SK_TI .SK_CW{width:40px;height:40px;border-radius:8px}
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
#SK_AP .SK_DF{flex-wrap:wrap}
#SK_AX{white-space:pre-line}
@keyframes SK_LT{50%{transform:scale(1.15)}}
.SK_LT{animation:SK_LT .5s ease-in-out 6}
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
.SK_MEDIA{position:fixed;width:1px;height:1px;left:0;top:0;opacity:.001;pointer-events:none}
#SK_DG{box-sizing:border-box;max-height:calc(100vh - 24px);max-height:calc(100dvh - 24px);overflow-y:auto}
#SK_EC .sc-crop-wrap,#SK_EC .sc-crop-wrap img{max-height:42vh}
#SK_CT{width:100%;display:flex;flex-direction:column;gap:6px}
#SK_CT .SK_TX,#SK_MC .SK_TX{margin:2px 0}
.SK_RANGE{position:relative;height:44px;width:100%;max-width:360px;margin:0 auto}
.SK_RANGE::before{content:'';position:absolute;top:19px;left:11px;right:11px;height:6px;background:var(--RD_L);border-radius:3px}
.SK_RANGE_H{position:absolute;top:19px;height:6px;background:var(--ok);border-radius:3px;z-index:1;touch-action:none}
#SK_CH{cursor:grab}
#SK_CH::before{content:'';position:absolute;inset:-12px 0}
.SK_RANGE_IN{position:absolute;top:0;left:0;width:100%;height:44px;margin:0;padding:0;border:0!important;box-shadow:none!important;background:none!important;-webkit-appearance:none;appearance:none;pointer-events:none;z-index:2}
.SK_RANGE_IN::-webkit-slider-thumb{-webkit-appearance:none;width:22px;height:22px;margin-top:-8px;border-radius:50%;background:var(--ok);border:2px solid var(--RD_F);box-shadow:0 1px 4px #0006;cursor:pointer;pointer-events:auto;touch-action:none}
.SK_RANGE_IN::-moz-range-thumb{width:18px;height:18px;border-radius:50%;background:var(--ok);border:2px solid var(--RD_F);box-shadow:0 1px 4px #0006;cursor:pointer;pointer-events:auto;touch-action:none}
.SK_RANGE_IN::-webkit-slider-runnable-track{height:6px;background:none}
.SK_RANGE_IN::-moz-range-track{height:6px;background:none}
.SK_RANGE_IN:focus-visible{outline:2px solid var(--RD_F);outline-offset:1px}
.SK_RANGE_IN:disabled{opacity:.5}
.SK_RANGE_IN:disabled::-webkit-slider-thumb{pointer-events:none}
.SK_RANGE_IN:disabled::-moz-range-thumb{pointer-events:none}
.SK_RANGE_FIELDS{display:flex;justify-content:center;gap:12px;width:100%}
.SK_RANGE_FIELDS label{display:flex;align-items:center;gap:6px;font-size:.85rem}
.SK_RANGE_FIELDS input{box-sizing:border-box;width:82px;min-width:0;padding:6px}
.SK_RANGE_BT{display:flex;flex-wrap:wrap;justify-content:center;gap:8px}
#SK_CL,#SK_ML{font-variant-numeric:tabular-nums}
#SK_CStatus{font-size:.82rem;margin:0;color:var(--RD_MF)}
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
<p class="SK_NT" id="SK_DA">Descarga la App Creadora de Stickers<br><a class="RD_B1" href="web/js/lib/Binarios/CheAgana.apk" target="_blank" rel="noopener" download>⬇️ Descargar la app</a></p>
</section>
<section id="SK_P" hidden>
<p class="SK_TX">Subi fotos, GIF o videos y elegi un tramo de hasta 10s en Recortar, o elegi stickers en Buscar.</p>
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
<dialog id="SK_AP" class="DX1 SK_DG"><button data-x="1" aria-label="Cerrar">✕</button><p id="SK_AT"></p><p id="SK_AX" class="SK_TX" hidden></p><p id="SK_AM" hidden>Primero instala la app Che😻Agana</p><div class="SK_DF"><a id="SK_AL" class="RD_B1" href="web/js/lib/Binarios/CheAgana.apk" target="_blank" rel="noopener" download>⬇️ Descargar la app</a><button type="button" id="SK_AO" class="RD_B1 GL_C">📲 Abrir la app</button></div></dialog>
<dialog id="SK_DG" class="DX1 SK_DG">
<button data-x="1" aria-label="Cancelar">✕</button>
<div id="SK_EC" hidden>
<div class="sc-crop-wrap"><img id="sc-crop-img" alt="Vista previa para recortar"></div>
<p id="SK_CStatus"></p>
<div id="SK_CT" hidden>
<div class="SK_RANGE">
<div id="SK_CH" class="SK_RANGE_H" title="Arrastra para mover el tramo"></div>
<input type="range" class="SK_RANGE_IN" id="SK_CS" min="0" max="0" step="any" value="0" aria-label="Inicio del video o animacion">
<input type="range" class="SK_RANGE_IN" id="SK_CE" min="0" max="0" step="any" value="0" aria-label="Fin del video o animacion">
</div>
<div class="SK_RANGE_FIELDS">
<label>Inicio (s)<input type="number" id="SK_CSN" min="0" step="0.1" value="0" inputmode="decimal"></label>
<label>Fin (s)<input type="number" id="SK_CEN" min="0" step="0.1" value="0" inputmode="decimal"></label>
</div>
<p id="SK_CL" class="SK_TX"></p>
<div class="SK_RANGE_BT"><button type="button" id="SK_CP" disabled>▶️ Ver tramo</button><button type="button" id="SK_CRetry">↻ Recargar imagen</button></div>
</div>
<button type="button" id="SK_CN">Sin recorte de imagen</button>
</div>
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
<div id="SK_MC" hidden>
<p id="SK_MN" class="SK_TX"></p>
<div class="SK_RANGE">
<div id="SK_MH" class="SK_RANGE_H"></div>
<input type="range" class="SK_RANGE_IN" id="SK_MS" min="0" max="0" step="0.1" value="0" aria-label="Inicio del audio">
<input type="range" class="SK_RANGE_IN" id="SK_ME" min="0" max="0" step="0.1" value="0" aria-label="Fin del audio">
</div>
<div class="SK_RANGE_FIELDS">
<label>Inicio (s)<input type="number" id="SK_MSN" min="0" max="0" step="0.1" value="0" inputmode="decimal"></label>
<label>Fin (s)<input type="number" id="SK_MEN" min="0" max="0" step="0.1" value="0" inputmode="decimal"></label>
</div>
<p id="SK_ML" class="SK_TX" aria-live="polite"></p>
<button type="button" id="SK_MP" disabled>▶️ Escuchar</button>
</div>
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
  const MAX_SZ=20*1024*1024,DIM=512,TARGET=900*1024,AU_MX=700*1024,AU_S=10,LA=490*1024,LS=95*1024;
  const PB={t:TARGET,st:TARGET,s:1},PA={t:LA,st:LS,s:0};
  const MAXFR=150,VID_MAX=10,VID_FPS=15,THM=512;
  const ID_OK=typeof ImageDecoder!=='undefined';
  const WS_OK=(()=>{try{return new WebAssembly.Module(new Uint8Array([0,97,115,109,1,0,0,0]))instanceof WebAssembly.Module;}catch{return false;}})();
  const SD_RX=/^[a-f0-9]{12}$/;
  const $=id=>document.getElementById(id);
  const N3=n=>String(n).padStart(3,'0');
  const WA=window.__CFG?.waitAnim||'';
  let FFP=null,GONE=false,SB=0,TG_B=0,ED=null,ED_W=0,EA={},cropper=null,lastQ=null;
  const MA=window.__AN1==='webview';
  let R=[],RF=[],PS=[],FT='',pg=0,P=[];
  let ovNS=DIM/4,ovSel=-1;
  const HM=new Map();

  const gEl=$('sk-grid'),pgEl=$('sk-pg'),ERD=$('SK_ER'),GD=$('SK_GD'),qEl=$('sk-q'),inEl=$('sc-in');
  const DG=$('SK_DG'),PD=$('SK_PD'),pBar=$('sc-pbar'),pLbl=$('sc-prog-lbl'),cropImg=$('sc-crop-img');
  const TR=$('SK_TR'),AU=$('SK_AU');
  for(const c of [$('sc-ov-c'),$('sc-lv')])c.width=c.height=DIM;
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
      if(!gf||GONE)return;
      const scheduleGF=()=>{
        if(_gfPending)return;_gfPending=true;
        (window.requestIdleCallback||(cb=>setTimeout(cb,1)))(()=>{
          _gfPending=false;
          if(GONE||!gEl.clientWidth)return;
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
  const APD=$('SK_AP');APD.querySelector('[data-x]').onclick=()=>APD.close();
  function setProg(p,l){pBar.style.width=p+'%';if(l!=null)pLbl.textContent=l;}
  function getCID(){try{let id=localStorage.getItem('sk_cid');if(!id){id=crypto.randomUUID();localStorage.setItem('sk_cid',id);}return id;}catch{return 'anon';}}
  function KN_1(it){
    if(it.type==='ad')return it.content?{type:'ad',content:it.content,width:it.width,height:it.height}:null;
    const f=it.file,url=f&&(typeof f.webp==='string'?f.webp:f.sm?.webp?.url);
    const hq=f&&typeof f==='object'?['hd','md','sm'].map(k=>f[k]?.webp).filter(w=>w?.url).sort((a,b)=>(b.width||0)-(a.width||0))[0]?.url:null;
    return url?{url,hq:hq||url,title:it.title||'',type:it.type,blur_preview:it.blur_preview||'',s:it.slug}:null;
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
  function FR_1(it){it.pr=(it.pr||0)+1;for(const k of ['pv','pc','fp'])if(it[k]?.startsWith('blob:'))URL.revokeObjectURL(it[k]);it.ov.forEach(o=>{if(o.src?.startsWith('blob:'))URL.revokeObjectURL(o.src);});}
  function PK_AD(it){it.ov=it.ov||[];P.push(it);UP_1();}
  function PK_RM(it){const i=P.indexOf(it);if(i<0)return;FR_1(it);P.splice(i,1);UP_1();}
  function UP_1(){$('SK_PN').textContent=P.length;TR_R();if(!$('SK_P').hidden)PL_R();gEl.querySelectorAll('.sk-it').forEach(b=>b.setAttribute('aria-pressed',!!PK_F(b._u)));}

  function TH_1(it){
    const m=document.createElement('img'),c=it.crop;m.alt='';
    if(c&&it.isAnim&&!it.ov.length&&!it.pc){m.src=it.trim&&it.fp?it.fp:it.pv;Object.assign(m.style,{width:c.sw/c.w*100+'%',height:c.sh/c.h*100+'%',left:-c.x/c.w*100+'%',top:-c.y/c.h*100+'%'});const w=document.createElement('span');w.className='SK_CW';w.append(m);return w;}
    m.src=it.pc||(it.trim&&it.fp?it.fp:it.pv);return m;
  }
  function TR_R(){
    $('SK_TP').hidden=!P.length;
    TR.hidden=!P.length&&$('SK_WT').hidden;
    const v=$('SK_TV');v.textContent='';
    const b=document.createElement('b');b.textContent=P.length+'/'+SK_MX;v.append(b);
    const e=$('SK_P').hidden,n=innerWidth<480;
    (e&&n?[]:P.slice(n?-2:-4)).forEach(it=>v.append(TH_1(it)));
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
    PK_AD({u:b._u,h:b._k.hq,pv:b._u,s:b._k.s,t:b._k.type,q:lastQ||''});b.setAttribute('aria-pressed','true');VL_1(b);
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
      f.append(TH_1(it));
      if(it.isVid){const s=document.createElement('span');s.className='SK_BG';s.textContent='🎬';f.append(s);}
      const x=BT_1('✕','Quitar','sc-rm');x.onclick=()=>PK_RM(it);d.append(x);
      const t=document.createElement('div');t.className='SK_TO';
      [['c','✂️','Recortar',!!it.crop||!!it.trim],['o','🖼️','Imagen',it.ov.length>0],['m','🎵','Sonido',!!it.au]].filter(x=>MU&&!MA||x[0]!=='m').forEach(([md,ic,lb,on])=>{
        const b=BT_1(ic+' '+lb+(on?' ✅':''),lb);b.setAttribute('aria-pressed',on);b.onclick=()=>ED_O(it,md);t.append(b);
      });
      d.append(t);L.append(d);
    });
  }

  // Times are source seconds. Preview position never changes the saved interval.
  const SK_TIME=s=>{const n=Math.round(Math.max(0,Number(s)||0)*10);return Math.floor(n/600)+':'+((n%600)/10).toFixed(1).padStart(4,'0');};
  function SK_RANGE(du,s=0,d=VID_MAX,limit=VID_MAX){
    du=Number(du);if(!Number.isFinite(du)||du<=0)du=limit;
    const gap=Math.min(.1,du);
    s=Math.max(0,Math.min(Number(s)||0,du-gap));
    d=Math.max(gap,Math.min(Number.isFinite(+d)?+d:limit,limit,du-s));
    return{s,d};
  }
  function TRIM_1(it,du=it.du){return SK_RANGE(du,it.trim?.s||0,it.trim?.d??VID_MAX);}
  function SK_EDIT_RANGE(du,s,d,value,edge,limit=VID_MAX){
    const r=SK_RANGE(du,s,d,limit),gap=Math.min(.1,du);let a=r.s,b=r.s+r.d;
    if(edge==='s'){
      a=Math.max(0,Math.min(Number(value)||0,du-gap));
      if(a>=b-gap)b=Math.min(du,a+r.d);
      b=Math.min(b,a+limit);
    }else{
      b=Math.max(gap,Math.min(Number(value)||gap,du));
      if(b<=a+gap)a=Math.max(0,b-r.d);
      a=Math.max(a,b-limit);
    }
    return SK_RANGE(du,a,b-a,limit);
  }
  function SK_RANGE_UI(p,du,s,d){
    const end=Math.min(du,s+d);
    for(const [id,v] of [[p+'S',s],[p+'E',end],[p+'SN',s],[p+'EN',end]]){
      const el=$(id);el.min='0';el.max=String(du);el.step=id.endsWith('N')?'0.1':'any';el.value=String(+v.toFixed(3));
      if(!id.endsWith('N'))el.setAttribute('aria-valuetext',SK_TIME(v));
    }
    const h=$(p+'H');h.style.left='calc(11px + (100% - 22px) * '+s/du+')';h.style.width='calc((100% - 22px) * '+d/du+')';
    $(p+'L').textContent=SK_TIME(s)+' → '+SK_TIME(end)+' · '+(+d.toFixed(2))+'s / '+VID_MAX+'s';
  }

  const VMS=new Set();
  function SK_BLOB(c){return new Promise((ok,no)=>c.toBlob(b=>b?ok(b):no(new Error('fotograma')),'image/png'));}
  function SK_PAINT_TICK(v,alive){
    return new Promise((ok,no)=>{
      let id=0,raf=0,done=false;
      const end=()=>{if(done)return;done=true;clearTimeout(to);if(id)v.cancelVideoFrameCallback?.(id);if(raf)cancelAnimationFrame(raf);alive()?ok():no(new Error('salida'));};
      const to=setTimeout(end,90);
      // A paused WebView may never deliver rVFC. Do not make it a requirement.
      if(v.requestVideoFrameCallback)try{id=v.requestVideoFrameCallback(end);}catch{}
      raf=requestAnimationFrame(()=>{raf=requestAnimationFrame(end);});
    });
  }
  async function VM_OPEN(file,onCreate){
    if(GONE)throw new Error('salida');
    const v=document.createElement('video'),url=URL.createObjectURL(file),pending=new Set();let closed=false;
    const alive=()=>!closed&&!GONE;
    v.muted=true;v.defaultMuted=true;v.playsInline=true;v.preload='auto';
    v.setAttribute('playsinline','');v.setAttribute('webkit-playsinline','');v.setAttribute('aria-hidden','true');v.tabIndex=-1;v.className='SK_MEDIA';
    $('SK1').append(v);
    const vm={v,du:0,close(){
      if(closed)return;closed=true;pending.forEach(f=>f(new Error('salida')));pending.clear();
      v.pause();v.removeAttribute('src');v.load();v.remove();URL.revokeObjectURL(url);VMS.delete(vm);
    }};
    VMS.add(vm);onCreate?.(vm);
    function wait(events,test,ms=10000){return new Promise((ok,no)=>{
      let done=false;
      const end=err=>{if(done)return;done=true;clearTimeout(to);events.forEach(n=>v.removeEventListener(n,check));v.removeEventListener('error',error);pending.delete(end);err?no(err):ok();};
      const check=()=>{if(!alive())end(new Error('salida'));else if(test())end();};
      const error=()=>end(new Error('video'));
      const to=setTimeout(()=>end(new Error('video')),ms);
      pending.add(end);events.forEach(n=>v.addEventListener(n,check));v.addEventListener('error',error);Promise.resolve().then(check);
    });}
    try{
      if(!alive())throw new Error('salida');
      const loaded=wait(['loadedmetadata','durationchange'],()=>v.readyState>=1&&v.videoWidth>0&&v.videoHeight>0);
      v.src=url;v.load();await loaded;
      if(!Number.isFinite(v.duration)||v.duration<=0)throw new Error('duracion');
      vm.du=v.duration;
      vm.frame=async time=>{
        if(!alive())throw new Error('salida');
        const t=Math.max(0,Math.min(Number(time)||0,vm.du-.001));
        const settled=wait(['seeked','loadeddata','canplay','timeupdate'],()=>!v.seeking&&v.readyState>=2&&Math.abs(v.currentTime-t)<.025);
        try{if(Math.abs(v.currentTime-t)>.0001||v.readyState<2)v.currentTime=t;}catch(e){vm.close();await settled.catch(()=>{});throw e;}
        await settled;await SK_PAINT_TICK(v,alive);
        if(!alive()||v.seeking||v.readyState<2||!v.videoWidth||!v.videoHeight)throw new Error('fotograma');
        const k=Math.min(1,THM/Math.max(v.videoWidth,v.videoHeight)),c=document.createElement('canvas');
        c.width=Math.max(1,Math.round(v.videoWidth*k));c.height=Math.max(1,Math.round(v.videoHeight*k));
        c.getContext('2d').drawImage(v,0,0,c.width,c.height);
        const b=await SK_BLOB(c);if(!alive())throw new Error('salida');return b;
      };
      return vm;
    }catch(e){vm.close();throw e;}
  }

  async function getVidThumb(file){
    let du=0;
    for(let attempt=0;attempt<2&&!GONE;attempt++){
      let vm;
      try{vm=await VM_OPEN(file);du=vm.du;const t=Math.min(.5,du*.1),b=await vm.frame(t);return{pv:URL.createObjectURL(b),du,pt:t};}
      catch{}finally{vm?.close();}
    }
    return{pv:'',du,pt:du?Math.min(.5,du*.1):0};
  }
  function VF_META(file){return FM_1(file,async(ff,p)=>{
    let du=0;const log=({message})=>{const m=message.match(/Duration:\s*(\d+):(\d+):(\d+(?:\.\d+)?)/);if(m)du=+m[1]*3600+(+m[2])*60+(+m[3]);};
    ff.on('log',log);try{await ff.exec(['-i',p]);}finally{ff.off('log',log);}return du;
  });}

  async function AN_OPEN(it,onCreate){
    if(!ID_OK)throw new Error('animacion');
    const meta=await AN_META(it.file,it.isAnim);if(!meta?.du)throw new Error('animacion');
    let closed=false,dec;const vm={du:meta.du,close(){if(closed)return;closed=true;try{dec?.close();}catch{}VMS.delete(vm);}};VMS.add(vm);onCreate?.(vm);
    try{
      const data=await it.file.arrayBuffer();if(GONE||closed)throw new Error('salida');
      dec=new ImageDecoder({data,type:it.isAnim==='gif'?'image/gif':'image/webp'});
      await dec.tracks.ready;
      if(GONE||closed)throw new Error('salida');
      vm.frame=async t=>{
        if(GONE||closed)throw new Error('salida');
        t=Math.max(0,Math.min(t,meta.du-.000001));
        let lo=0,hi=meta.times.length-1;
        while(lo<hi){const m=Math.ceil((lo+hi)/2);if(meta.times[m]<=t)lo=m;else hi=m-1;}
        const r=await dec.decode({frameIndex:lo});
        try{
          if(GONE||closed)throw new Error('salida');
          const f=r.image,k=Math.min(1,THM/Math.max(f.displayWidth,f.displayHeight)),c=document.createElement('canvas');
          c.width=Math.max(1,Math.round(f.displayWidth*k));c.height=Math.max(1,Math.round(f.displayHeight*k));c.getContext('2d').drawImage(f,0,0,c.width,c.height);return await SK_BLOB(c);
        }finally{r.image.close();}
      };
      return vm;
    }catch(e){vm.close();throw e;}
  }

  async function MK_F(f){
    const isVid=f.type.startsWith('video/'),isWebp=f.type==='image/webp';
    if(isVid){
      let {pv,du,pt}=await getVidThumb(f),fv=!pv;
      if(GONE)throw new Error('salida');
      if(fv){PD_O('Abriendo video...');try{
        du=du||await VF_META(f).catch(()=>0);pt=du?Math.min(.5,du*.1):pt;
        const b=(await FV_1(f,1,pt,.25))[0];if(GONE)throw new Error('salida');pv=URL.createObjectURL(b);
      }finally{if(!GONE)PD_C();}}
      return{file:f,pv,du,pt,fv,isVid,isWebp:false,isAnim:false,sq:false,au:MU?{f,s:0,d:Math.min(AU_S,du||AU_S),v:1}:null};
    }
    const bm=await createImageBitmap(f),w=bm.width,h=bm.height,r=w/h;bm.close();
    return{file:f,pv:URL.createObjectURL(f),isVid,isWebp,isAnim:await AN_T1(f),sq:r>=.8&&r<=1.25,w,h};
  }

  async function KF_1(it){
    if(it.file)return;
    const b=await fetch(it.h||it.u).then(r=>{if(!r.ok)throw new Error(r.status);return r.blob();});
    const ty=b.type.startsWith('image/')?b.type:'image/webp';
    if(GONE)throw new Error('salida');
    const pv=it.pv,next=await MK_F(new File([b],'k.'+ty.split('/')[1],{type:ty}));
    if(GONE){next.ov=[];FR_1(next);throw new Error('salida');}
    Object.assign(it,next);
    if(pv?.startsWith('blob:'))URL.revokeObjectURL(pv);
  }

  async function addFiles(list){
    for(const f of list){
      if(GONE)return;
      if(P.length>=SK_MX){ER_D1('Maximo '+SK_MX+' stickers por pack');break;}
      const v=f.type.startsWith('video/');
      if(!v&&!f.type.startsWith('image/')){ER_D1('Archivo no compatible');continue;}
      if(!v&&f.size>MAX_SZ){ER_D1('Maximo 20MB por imagen');continue;}
      try{const it=await MK_F(f);if(GONE){it.ov=[];FR_1(it);return;}PK_AD(it);}catch{ER_D1(v?'Video no compatible':'Imagen no compatible');}
    }
    if(!GONE)TB_1('p');
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

  const CR_LIVE=e=>!!e&&ED===e&&!GONE&&DG.open&&e.md==='c';
  function CR_STATE(e){
    if(!CR_LIVE(e))return;
    $('SK_DK').disabled=!e.ready||!!e.busy||!!e.want||!!e.opening||!!e.source&&!e.previewValid;
    $('SK_CP').disabled=!e.source||!e.ready;
    for(const id of ['SK_CS','SK_CE','SK_CSN','SK_CEN'])$(id).disabled=!e.ready||!!e.opening;
  }
  function CR_STOP(e){
    if(!e)return;clearTimeout(e.playTimer);e.playTimer=0;e.playing=false;
    if(CR_LIVE(e))$('SK_CP').textContent='▶️ Ver tramo';
  }
  function CR_CLOSE(e){
    if(!e)return;CR_STOP(e);e.dragStop?.();e.want=null;e.source?.close();e.source=null;
    if(e.previewURL)URL.revokeObjectURL(e.previewURL);e.previewURL=null;
    cropImg.onload=null;cropImg.onerror=null;
  }
  async function CR_IMAGE(e,blob){
    let img=await IMG_L1(blob);if(!CR_LIVE(e))return;
    if(!e.pw){e.pw=img.naturalWidth;e.ph=img.naturalHeight;}
    if(img.naturalWidth!==e.pw||img.naturalHeight!==e.ph){
      const c=document.createElement('canvas');c.width=e.pw;c.height=e.ph;c.getContext('2d').drawImage(img,0,0,c.width,c.height);blob=await SK_BLOB(c);
      if(!CR_LIVE(e))return;
    }
    const url=URL.createObjectURL(blob),old=e.previewURL;
    e.previewURL=url;e.frameBlob=blob;
    if(cropper&&e.ready){
      cropper.replace(url,true);if(old)URL.revokeObjectURL(old);
    }else{
      if(old)URL.revokeObjectURL(old);
      e.imageLoading=true;
      cropImg.onload=()=>CR_BUILD(e);cropImg.onerror=()=>{if(CR_LIVE(e)){$('SK_CStatus').textContent='No se pudo mostrar la imagen. Proba recargarla.';e.imageLoading=false;e.ready=false;CR_STATE(e);}};
      cropImg.src=url;
    }
  }
  async function CR_BUILD(e){
    try{
      await loadCropperJS();if(!CR_LIVE(e)||cropper)return;
      const saved=e.it.crop,w=cropImg.naturalWidth,h=cropImg.naturalHeight;
      const o={viewMode:1,dragMode:'move',background:false,autoCropArea:.9,cropstart(){if(CR_LIVE(e))e.noCrop=false;},cropend(){if(CR_LIVE(e))cropper?.setDragMode('move');},ready(){
        if(!CR_LIVE(e))return;e.ready=true;e.imageLoading=false;CR_STATE(e);
        if(e.want&&!e.busy)CR_DRAIN(e);
      }};
      if(saved)o.data={x:saved.x*w/saved.sw,y:saved.y*h/saved.sh,width:saved.w*w/saved.sw,height:saved.h*h/saved.sh};
      cropper=new Cropper(cropImg,o);
    }catch{if(CR_LIVE(e)){e.imageLoading=false;$('SK_CStatus').textContent='No se pudo cargar el recortador.';CR_STATE(e);}}
  }
  function CR_REQUEST(e,t,force=false){
    if(!CR_LIVE(e)||!e.source)return;
    e.want={t:Math.max(0,Math.min(t,e.source.du-.001)),force,id:++e.request,version:e.rangeVersion};CR_STATE(e);
    if(!e.busy&&(!e.imageLoading&&!cropper||e.ready))CR_DRAIN(e);
  }
  async function CR_DRAIN(e){
    if(e.busy||!CR_LIVE(e))return;e.busy=true;CR_STATE(e);
    try{
      while(CR_LIVE(e)&&e.want){
        const req=e.want;e.want=null;let b;
        try{
          if(req.force&&e.it.isVid)b=(await FV_1(e.it.file,1,req.t,.25))[0];
          else try{b=await e.source.frame(req.t);}catch(err){
            if(!e.it.isVid||!CR_LIVE(e))throw err;
            b=(await FV_1(e.it.file,1,req.t,.25))[0];
          }
          if(!CR_LIVE(e))return;if(req.version!==e.rangeVersion||e.want&&!e.playing)continue;
          await CR_IMAGE(e,b);if(!CR_LIVE(e))return;
          e.pt=req.t;e.previewValid=req.version===e.rangeVersion&&req.t>=e.range.s-.002&&req.t<e.range.s+e.range.d;
          $('SK_CStatus').textContent='Vista: '+SK_TIME(e.pt);
          if(e.imageLoading)break;
        }catch{
          if(!CR_LIVE(e))return;
          if(!e.want){CR_STOP(e);$('SK_CStatus').textContent='No se pudo leer ese fotograma. Proba mover el tramo o recargar la imagen.';}
        }
      }
    }finally{e.busy=false;CR_STATE(e);}
  }
  function CR_RANGE(e,value,edge){
    if(!CR_LIVE(e)||!e.source)return;CR_STOP(e);
    e.range=SK_EDIT_RANGE(e.source.du,e.range.s,e.range.d,value,edge);e.rangeChanged=true;e.rangeVersion++;e.previewValid=false;
    SK_RANGE_UI('SK_C',e.source.du,e.range.s,e.range.d);
    CR_REQUEST(e,edge==='e'?Math.max(e.range.s,e.range.s+e.range.d-.001):e.range.s);
  }
  for(const [id,edge] of [['SK_CS','s'],['SK_CE','e'],['SK_CSN','s'],['SK_CEN','e']]){
    $(id)[id.endsWith('N')?'onchange':'oninput']=ev=>{if(ED)CR_RANGE(ED,ev.target.value,edge);};
  }
  $('SK_CP').onclick=()=>{
    const e=ED;if(!CR_LIVE(e)||!e.source)return;
    if(e.playing){CR_STOP(e);return;}
    e.playing=true;$('SK_CP').textContent='⏸️ Pausa';
    const start=performance.now();
    const tick=()=>{
      if(!CR_LIVE(e)||!e.playing)return;
      const elapsed=(performance.now()-start)/1000;
      if(elapsed>=e.range.d){CR_STOP(e);CR_REQUEST(e,Math.max(e.range.s,e.range.s+e.range.d-.001));return;}
      CR_REQUEST(e,e.range.s+elapsed);e.playTimer=setTimeout(tick,e.source.slow?600:140);
    };tick();
  };
  $('SK_CRetry').onclick=()=>{const e=ED;if(CR_LIVE(e)&&e.source){CR_STOP(e);CR_REQUEST(e,Math.max(e.range.s,Math.min(e.pt??e.range.s,e.range.s+e.range.d-.001)),true);}};
  $('SK_CH').onpointerdown=ev=>{
    const e=ED;if(!CR_LIVE(e)||!e.source||ev.button>0)return;
    ev.preventDefault();CR_STOP(e);
    const el=ev.currentTarget,rect=el.parentElement.getBoundingClientRect(),x=ev.clientX,s=e.range.s,d=e.range.d;
    el.setPointerCapture(ev.pointerId);
    const move=event=>{
      if(!CR_LIVE(e))return;
      e.range=SK_RANGE(e.source.du,Math.max(0,Math.min(e.source.du-d,s+(event.clientX-x)/Math.max(1,rect.width-22)*e.source.du)),d);e.rangeChanged=true;e.rangeVersion++;e.previewValid=false;
      SK_RANGE_UI('SK_C',e.source.du,e.range.s,e.range.d);CR_REQUEST(e,e.range.s);
    };
    const end=()=>{el.removeEventListener('pointermove',move);el.removeEventListener('pointerup',end);el.removeEventListener('pointercancel',end);if(e.dragStop===end)e.dragStop=null;};
    e.dragStop?.();e.dragStop=end;
    el.addEventListener('pointermove',move);el.addEventListener('pointerup',end);el.addEventListener('pointercancel',end);
  };
  async function CR_O(it){
    const e=ED;e.ready=false;e.opening=true;e.request=0;e.rangeVersion=0;e.previewValid=false;e.rangeChanged=false;e.range=TRIM_1(it);e.pt=it.pt||0;
    $('SK_CT').hidden=true;$('SK_CP').textContent='▶️ Ver tramo';$('SK_CRetry').hidden=!it.isVid;
    $('SK_CStatus').textContent='Cargando imagen...';CR_STATE(e);
    try{
      if(it.isVid||it.isAnim){
        let source;
        const pending=vm=>{if(CR_LIVE(e))e.source=vm;else vm.close();};
        try{source=it.isVid?await VM_OPEN(it.file,pending):await AN_OPEN(it,pending);}catch{
          if(!CR_LIVE(e))return;
          e.source=null;
          if(it.isVid){
            const du=it.du||await VF_META(it.file);
            if(du>0){let closed=false;source={du,slow:true,close(){closed=true;},async frame(t){if(closed||GONE)throw new Error('salida');return(await FV_1(it.file,1,t,.25))[0];}};}
          }
        }
        if(!CR_LIVE(e)){source?.close();return;}
        if(source){
          e.source=source;it.du=source.du;e.range=TRIM_1(it,source.du);
          $('SK_CT').hidden=false;SK_RANGE_UI('SK_C',source.du,e.range.s,e.range.d);
          CR_REQUEST(e,Math.max(e.range.s,Math.min(it.pt??e.range.s,e.range.s+e.range.d-.001)));
        }else{
          $('SK_CStatus').textContent=it.isAnim?'Este navegador permite recortar el encuadre, pero no elegir el tiempo de esta animacion.':'No se pudo leer la duracion. Se conserva el tramo inicial.';
          cropImg.onload=()=>CR_BUILD(e);cropImg.src=it.pv;
        }
      }else{cropImg.onload=()=>{if(CR_LIVE(e)){$('SK_CStatus').textContent='';CR_BUILD(e);}};cropImg.src=it.pv;}
    }catch{if(CR_LIVE(e))$('SK_CStatus').textContent='No se pudo abrir la vista previa.';}
    finally{e.opening=false;CR_STATE(e);}
  }
  function CR_SAVE(e){
    if(!e.ready||e.busy||e.want||e.opening||!cropper||e.source&&!e.previewValid)return false;
    const d=cropper.getData(true);
    if(!e.noCrop&&(!Number.isFinite(d.width)||!Number.isFinite(d.height)||d.width<=0||d.height<=0))return false;
    const it=e.it;
    it.crop=e.noCrop?null:{x:d.x,y:d.y,w:d.width,h:d.height,sw:cropImg.naturalWidth,sh:cropImg.naturalHeight};
    if(e.source&&(e.rangeChanged||it.trim||it.isAnim&&e.source.du>VID_MAX))it.trim={...e.range};
    if(e.source&&it.au?.v){const r=TRIM_1(it);it.au={...it.au,s:r.s,d:r.d};}
    if(e.frameBlob&&(it.isVid||it.isAnim)){
      const key=it.isVid?'pv':'fp',old=it[key];it[key]=URL.createObjectURL(e.frameBlob);it.pt=e.pt;if(old?.startsWith('blob:'))URL.revokeObjectURL(old);
    }
    delete it.o;return true;
  }

  async function ED_O(it,md,h){
    if(ED||ED_W||GONE)return;
    ED_W=1;
    let t=0;
    try{
      if(!it.file){t=setTimeout(()=>PD_O('Cargando...'),300);await KF_1(it);}
    }catch(e){ER_D1('Error Klipy '+e.message);return;}
    finally{if(t){clearTimeout(t);if(!GONE)PD_C();}ED_W=0;}
    if(!P.includes(it)||GONE||ED)return;
    ED={it,md,ok:0,sn:{crop:it.crop,trim:it.trim,ov:it.ov.map(o=>({...o})),au:it.au}};
    $('SK_DK').disabled=md==='c';
    for(const k in ED_S)ED_S[k].hidden=k!==md;
    if(!h){const t=Math.random();HM.set(t,[it,md]);window.__HS3?.('SK',t);}
    DG.showModal();document.body.style.overflow='hidden';
    if(md==='c')CR_O(it);else if(md==='o')ovOpen(it);else MU_O(it);
  }

  $('SK_DK').onclick=()=>{
    if(!ED)return;
    const {it,md}=ED;
    if(md==='c'){if(!CR_SAVE(ED))return;}
    else if(md==='m'){if(EA.f&&!MU_READY){ER_D1('Espera a cargar el audio');return;}MU_T();it.au=EA.f?{f:EA.f,s:EA.s,d:EA.d,v:MU_V(),du:EA.du}:null;}
    delete it.o;
    ED.ok=1;ED_X();
  };
  $('SK_DC').onclick=()=>ED_X();
  DG.querySelector('[data-x]').onclick=()=>ED_X();
  $('SK_CN').onclick=()=>{if(!CR_LIVE(ED)||!ED.ready)return;ED.noCrop=true;cropper.clear();cropper.setDragMode('crop');};
  function ED_C(){
    const e=ED;if(!e)return;ED=null;CR_CLOSE(e);
    if(cropper){cropper.destroy();cropper=null;}
    MU_X();
    $('sc-ov-wrap').querySelectorAll('.sc-ov-it').forEach(x=>x.remove());
    document.body.style.overflow='';
    if(e){
      const a=e.ok?e.sn.ov:e.it.ov,b=new Set((e.ok?e.it.ov:e.sn.ov).map(o=>o.src));
      a.forEach(o=>{if(!b.has(o.src)&&o.src?.startsWith('blob:'))URL.revokeObjectURL(o.src);});
      if(!e.ok)Object.assign(e.it,{crop:e.sn.crop,trim:e.sn.trim,ov:e.sn.ov,au:e.sn.au});
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
    const request=it.pr=(it.pr||0)+1;
    if(it.pc){URL.revokeObjectURL(it.pc);it.pc=null;}
    if(!it.crop&&!it.ov.length)return;
    if(it.isAnim&&!it.ov.length)return;
    try{
      const img=await IMG_U1(it.trim&&it.fp?it.fp:it.pv);
      const c=document.createElement('canvas');c.width=DIM;c.height=DIM;
      const x=c.getContext('2d');DR_B1(x,img,it.crop);DR_O1(x,it.ov,0);
      const b=await new Promise(r=>c.toBlob(r,'image/webp',.8));
      if(b&&!GONE&&it.pr===request&&P.includes(it))it.pc=URL.createObjectURL(b);
    }catch{}
  }

  let MU_GEN=0,MU_URL=null,MU_TIMER=0,MU_PLAY_ID=0,MU_WAIT=false,MU_READY=false,MU_CHECK=null,MU_PICK=null;
  function MU_P2(){
    ++MU_PLAY_ID;MU_WAIT=false;clearTimeout(MU_TIMER);MU_TIMER=0;
    AU.pause();$('SK_MP').textContent='▶️ Escuchar';
  }
  function MU_X(){
    RC_X();++MU_GEN;++MU_PLAY_ID;MU_WAIT=false;MU_READY=false;MU_CHECK=null;MU_PICK=null;
    clearTimeout(MU_TIMER);MU_TIMER=0;
    for(const k of ['onloadedmetadata','ondurationchange','onerror','ontimeupdate','onpause','onended','onplay','onplaying','onseeked','onratechange'])AU[k]=null;
    AU.pause();AU.removeAttribute('src');AU.load();
    if(MU_URL){URL.revokeObjectURL(MU_URL);MU_URL=null;}
    $('SK_MP').textContent='▶️ Escuchar';$('SK_MP').disabled=true;
  }
  function MU_O(it){
    EA=it.au?{...it.au}:{f:null,s:0,d:AU_S,v:false,du:0};
    if(it.isVid&&EA.f&&(EA.v||EA.f===it.file)){EA.f=it.file;EA.v=true;Object.assign(EA,TRIM_1(it));}
    $('SK_MV').hidden=!it.isVid;
    $('SK_MR').hidden=!window.MediaRecorder||!navigator.mediaDevices?.getUserMedia;
    MU_L();
  }
  const MU_V=()=>!!EA.f&&!!ED?.it.isVid&&(EA.v===true||EA.f===ED.it.file);
  function MU_T(){
    if(!EA.f)return;
    const v=MU_V();EA.v=v;
    if(MU_READY){
      Object.assign(EA,v?TRIM_1(ED.it,EA.du):SK_RANGE(EA.du,EA.s,EA.d));
      SK_RANGE_UI('SK_M',EA.du,EA.s,EA.d);
      if(v)$('SK_ML').textContent+=' · Sigue el tramo del video';
    }
    $('SK_MN').textContent=v?'🎬 Sonido del video':EA.f.r?'🎤 Grabación':EA.f.name||'Audio';
    for(const id of ['SK_MS','SK_ME','SK_MSN','SK_MEN'])$(id).disabled=!MU_READY||v;
    $('SK_MP').disabled=!MU_READY;
  }
  function MU_L(){
    MU_X();
    const v=MU_V();
    $('SK_M0').setAttribute('aria-pressed',!EA.f);$('SK_MV').setAttribute('aria-pressed',v);
    $('SK_MB').setAttribute('aria-pressed',!!EA.f&&!v&&!EA.f.r);$('SK_MR').setAttribute('aria-pressed',!!EA.f?.r);
    $('SK_MC').hidden=!EA.f;
    if(!EA.f)return;
    $('SK_ML').textContent='Cargando audio…';MU_T();
    const ed=ED,ea=EA,gen=MU_GEN,u=URL.createObjectURL(ea.f);MU_URL=u;
    const live=()=>!GONE&&ED===ed&&EA===ea&&MU_GEN===gen&&MU_URL===u&&AU.getAttribute('src')===u;
    const fail=msg=>{if(!live())return;ER_D1(msg);EA={f:null,s:0,d:AU_S,v:false,du:0};MU_L();};
    const metadata=()=>{
      if(!live()||AU.readyState<1||AU.currentSrc&&AU.currentSrc!==u)return;
      const du=[AU.duration,ea.f.du,v?ed.it.du:0,ea.du].find(n=>Number.isFinite(n)&&n>0);
      if(!du){fail('No se pudo leer la duración del audio');return;}
      ea.du=du;MU_READY=true;MU_T();
    };
    const check=()=>{
      if(!live())return;
      clearTimeout(MU_TIMER);MU_TIMER=0;
      if(AU.paused)return;
      const rest=ea.s+ea.d-AU.currentTime;
      if(rest<=0){MU_P2();return;}
      MU_TIMER=setTimeout(check,Math.max(10,Math.min(100,rest*1000/Math.max(.1,AU.playbackRate||1))));
    };
    MU_CHECK=check;
    AU.onloadedmetadata=metadata;AU.ondurationchange=metadata;
    AU.onerror=()=>fail('Audio no compatible');
    AU.ontimeupdate=check;AU.onseeked=check;AU.onratechange=check;
    AU.onplay=AU.onplaying=()=>{if(!live()||AU.paused)return;$('SK_MP').textContent='⏸️ Pausa';check();};
    AU.onpause=AU.onended=()=>{if(!live()||!AU.paused)return;clearTimeout(MU_TIMER);MU_TIMER=0;$('SK_MP').textContent='▶️ Escuchar';};
    AU.src=u;AU.load();
  }
  function MU_E(value,edge){
    if(!ED||ED.md!=='m'||!EA.f||!MU_READY||MU_V())return;
    if(!Number.isFinite(value)){MU_T();return;}
    MU_P2();Object.assign(EA,SK_EDIT_RANGE(EA.du,EA.s,EA.d,value,edge,AU_S));MU_T();
    try{AU.currentTime=edge==='e'?Math.min(EA.s+EA.d,Math.max(0,EA.du-.001)):EA.s;}catch{}
  }
  $('SK_MS').oninput=e=>MU_E(e.target.valueAsNumber,'s');
  $('SK_ME').oninput=e=>MU_E(e.target.valueAsNumber,'e');
  $('SK_MSN').onchange=e=>MU_E(e.target.valueAsNumber,'s');
  $('SK_MEN').onchange=e=>MU_E(e.target.valueAsNumber,'e');
  $('SK_MP').onclick=()=>{
    if(!ED||ED.md!=='m'||!EA.f||!MU_READY||GONE)return;
    if(!AU.paused||MU_WAIT){MU_P2();return;}
    MU_T();const ed=ED,ea=EA,gen=MU_GEN,id=++MU_PLAY_ID,check=MU_CHECK;
    const live=()=>!GONE&&ED===ed&&EA===ea&&MU_GEN===gen&&MU_PLAY_ID===id;
    MU_WAIT=true;let play;
    try{AU.currentTime=ea.s;play=AU.play();}catch{MU_WAIT=false;ER_D1('No se pudo reproducir el audio');return;}
    Promise.resolve(play).then(()=>{if(!live())return;MU_WAIT=false;if(!AU.paused){$('SK_MP').textContent='⏸️ Pausa';check?.();}}).catch(e=>{
      if(!live())return;MU_WAIT=false;$('SK_MP').textContent='▶️ Escuchar';
      if(e?.name!=='AbortError')ER_D1('No se pudo reproducir el audio');
    });
  };
  $('SK_M0').onclick=()=>{if(!ED)return;EA={f:null,s:0,d:AU_S,v:false,du:0};MU_L();};
  $('SK_MV').onclick=()=>{if(!ED?.it.isVid)return;EA={f:ED.it.file,...TRIM_1(ED.it),v:true,du:ED.it.du||0};MU_L();};
  $('SK_MB').onclick=()=>{if(ED?.md==='m'){MU_PICK=ED;$('SK_MF').click();}};
  $('SK_MF').onchange=e=>{
    const f=e.target.files[0];e.target.value='';const ed=MU_PICK;MU_PICK=null;
    if(!f||!ED||ED!==ed||ED.md!=='m'||GONE)return;
    EA={f,s:0,d:AU_S,v:false,du:0};MU_L();
  };

  let RC=null;
  function RC_X(k){const r=RC;if(!r)return;RC=null;r.k=k;clearInterval(r.t);if(r.m.state!=='inactive')r.m.stop();r.s.getTracks().forEach(x=>x.stop());$('SK_MR').textContent='🎤 Grabar';}
  $('SK_MR').onclick=async()=>{
    if(RC)return RC_X(1);
    if(!ED)return;
    const ed=ED,requestGen=MU_GEN;
    let s;try{s=await navigator.mediaDevices.getUserMedia({audio:true});}catch(e){if(ED===ed&&!GONE)ER_D1(e.name==='NotFoundError'?'Sin microfono':'Microfono bloqueado');return;}
    if(ED!==ed||MU_GEN!==requestGen||GONE||RC){s.getTracks().forEach(x=>x.stop());return;}
    MU_X();const gen=MU_GEN;$('SK_MC').hidden=true;
    const m=new MediaRecorder(s),ch=[],t0=Date.now(),r={m,s};
    const T=()=>{const e=(Date.now()-t0)/1000;if(e>=AU_S)return RC_X(1);$('SK_MR').textContent='⏹️ Grabando '+Math.ceil(AU_S-e)+'s';};
    m.ondataavailable=e=>{if(e.data.size)ch.push(e.data);};
    m.onstop=()=>{if(!r.k||ED!==ed||MU_GEN!==gen||GONE||!ch.length)return;const ty=m.mimeType||ch[0].type,f=new File(ch,'Grabacion.'+(/mp4/.test(ty)?'m4a':'webm'),{type:ty});f.r=1;f.du=Math.min(AU_S,(Date.now()-t0)/1000);EA={f,s:0,d:Math.min(AU_S,f.du),v:false,du:f.du};MU_L();};
    RC=r;r.t=setInterval(T,250);m.start();T();
  };

  let FFQ=Promise.resolve();
  function FF_JOB(fn){const p=FFQ.catch(()=>{}).then(()=>{if(GONE)throw new Error('salida');return fn();});FFQ=p.catch(()=>{});return p;}

  function FF_L1(){
    if(GONE)return Promise.reject(new Error('salida'));
    if(FFP)return FFP;
    FFP=(window.FF1?Promise.resolve():new Promise((ok,no)=>{const s=document.createElement('script');s.src='web/js/lib/FFmpeg.js';s.onload=ok;s.onerror=()=>{s.remove();no(new Error('ffmpeg'));};document.head.appendChild(s);})).then(()=>window.FF1());
    FFP.catch(()=>{FFP=null;});
    return FFP;
  }

  const AN_MC=new WeakMap();
  async function AN_T1(f){
    const h=new Uint8Array(await f.slice(0,32).arrayBuffer());
    const s=(a,n)=>String.fromCharCode(...h.subarray(a,a+n));
    if(s(0,4)==='GIF8')return 'gif';
    return s(0,4)==='RIFF'&&s(8,4)==='WEBP'&&s(12,4)==='VP8X'&&(h[20]&2)?'webp_anim':false;
  }

  function AN_META(file,ty){
    if(AN_MC.has(file))return AN_MC.get(file);
    const task=(async()=>{
      const b=new Uint8Array(await file.arrayBuffer()),times=[],durations=[];
      let du=0;
      const need=(p,n)=>{if(p<0||n<0||p+n>b.length)throw new Error('animacion incompleta');};
      const str=(p,n)=>{need(p,n);return String.fromCharCode(...b.subarray(p,p+n));};
      const u32=p=>{need(p,4);return (b[p]|b[p+1]<<8|b[p+2]<<16|b[p+3]<<24)>>>0;};
      const add=d=>{d=d>0?d:.1;times.push(du);durations.push(d);du+=d;};
      if(str(0,4)==='GIF8'){
        need(0,13);
        let p=13,delay=.1;
        if(b[10]&128)p+=3*(1<<((b[10]&7)+1));
        need(p,0);
        const blocks=()=>{for(;;){need(p,1);const n=b[p++];if(!n)return;need(p,n);p+=n;}};
        while(p<b.length){
          const tag=b[p++];
          if(tag===0x3b)break;
          if(tag===0x21){
            need(p,1);const label=b[p++];
            if(label===0xf9){
              need(p,1);const n=b[p++];need(p,n+1);
              if(n!==4||b[p+n]!==0)throw new Error('control GIF');
              delay=(b[p+1]|b[p+2]<<8)/100||.1;p+=n+1;
            }else{blocks();if(label===0x01)delay=.1;}
          }else if(tag===0x2c){
            need(p,9);const packed=b[p+8];p+=9;
            if(packed&128)p+=3*(1<<((packed&7)+1));
            need(p,1);p++;blocks();add(delay);delay=.1;
          }else throw new Error('bloque GIF');
        }
      }else if(str(0,4)==='RIFF'&&str(8,4)==='WEBP'){
        const end=u32(4)+8;need(0,end);
        for(let p=12;p+8<=end;){
          const tag=str(p,4),n=u32(p+4),start=p+8;
          if(start+n>end)throw new Error('bloque WebP');
          if(tag==='ANMF'){
            if(n<16)throw new Error('fotograma WebP');
            add((b[start+12]|b[start+13]<<8|b[start+14]<<16)/1000);
          }
          p=start+n+(n&1);
        }
      }else throw new Error('animacion no compatible');
      if(!times.length||!isFinite(du)||du<=0)throw new Error('animacion sin fotogramas');
      return {du,times,durations};
    })();
    AN_MC.set(file,task);task.catch(()=>AN_MC.delete(file));return task;
  }

  function AN_IDX(meta,t){
    let lo=0,hi=meta.times.length-1;
    while(lo<hi){const mid=Math.ceil((lo+hi)/2);if(meta.times[mid]<=t+1e-9)lo=mid;else hi=mid-1;}
    return lo;
  }

  async function AN_D1(b,ty,trim){
    if(!ID_OK)return null;
    let dec,current=null;const fr=[];
    try{
      const meta=await AN_META(b,ty),cut=TRIM_1({trim},meta.du);
      dec=new ImageDecoder({data:await b.arrayBuffer(),type:ty==='gif'?'image/gif':'image/webp'});
      await dec.tracks.ready;await dec.completed;
      const tr=dec.tracks.selectedTrack;
      if(!tr||tr.frameCount<2)return null;
      const n=Math.min(MAXFR,Math.max(1,Math.ceil(cut.d*VID_FPS-1e-8)));
      let previous=-1;
      for(let i=0;i<n;i++){
        if(GONE)throw new Error('salida');
        const time=Math.min(meta.du-1e-7,cut.s+i/VID_FPS);
        const index=Math.min(tr.frameCount-1,AN_IDX(meta,time));
        if(index!==previous){
          if(current){current.close();current=null;}
          current=(await dec.decode({frameIndex:index})).image;previous=index;
        }
        const w=current.displayWidth||current.codedWidth||current.width||0,h=current.displayHeight||current.codedHeight||current.height||0;
        const scale=Math.min(1,THM/Math.max(w,h,1));
        if(scale<1)fr.push(await createImageBitmap(current,{resizeWidth:Math.max(1,Math.round(w*scale)),resizeHeight:Math.max(1,Math.round(h*scale)),resizeQuality:'high'}));
        else fr.push(typeof current.clone==='function'?current.clone():await createImageBitmap(current));
      }
      return {fr,fps:VID_FPS,dur:cut.d};
    }catch(e){AN_F1({fr});if(GONE)throw e;return null;}
    finally{if(current)try{current.close();}catch{}if(dec)try{dec.close();}catch{}}
  }

  function AN_F1(a){
    if(!a)return;
    for(const x of new Set(a.fr||[]))try{x.close();}catch{}
    a.fr=[];
  }

  function DR_B1(ctx,img,cd){
    if(cd){
      const sw=img.displayWidth||img.videoWidth||img.naturalWidth||img.width;
      const sh=img.displayHeight||img.videoHeight||img.naturalHeight||img.height;
      const kx=sw/cd.sw,ky=sh/cd.sh;
      ctx.drawImage(img,cd.x*kx,cd.y*ky,cd.w*kx,cd.h*ky,0,0,DIM,DIM);
    }else ctx.drawImage(img,0,0,DIM,DIM);
  }

  function DR_O1(ctx,ovs,time=0){
    ovs.forEach(o=>{
      let src=o.img;
      if(o.an?.fr.length){
        const fps=o.an.fps||VID_FPS,dur=o.an.dur||o.an.fr.length/fps;
        const i=Math.min(o.an.fr.length-1,Math.floor((time%dur)*fps+1e-8));
        src=o.an.fr[i];
      }
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

  async function WB_E1(it,base,ovs,fps,onp,pf){return FF_JOB(async()=>{
    const ff=await FF_L1();
    const c=document.createElement('canvas');c.width=DIM;c.height=DIM;
    const ctx=c.getContext('2d');
    const lv=$('sc-lv'),ckEl=$('sc-ck'),lctx=lv.getContext('2d');
    ckEl.style.display='none';lv.style.display='block';
    const baseDur=base.fr?.length?(base.dur||base.fr.length/(base.fps||VID_FPS)):0;
    const overlayDur=ovs.reduce((m,o)=>Math.max(m,o.an?(o.an.dur||o.an.fr.length/(o.an.fps||VID_FPS)):0),0);
    const dur=Math.min(VID_MAX,baseDur||overlayDur||1/VID_FPS);
    fps=VID_FPS;
    const n=Math.min(MAXFR,Math.max(1,Math.ceil(dur*fps-1e-8))),names=[];
    let op=true;
    try{
      for(let i=0;i<n;i++){
        if(GONE)throw new Error('salida');
        const time=i/fps;
        ctx.clearRect(0,0,DIM,DIM);
        const bi=base.fr?.length?Math.min(base.fr.length-1,Math.floor(time*(base.fps||fps)+1e-8)):0;
        DR_B1(ctx,base.fr?.length?base.fr[bi]:base.img,it.crop);
        DR_O1(ctx,ovs,time);
        const d=ctx.getImageData(0,0,DIM,DIM).data;
        if(op)for(let q=3;q<d.length;q+=4)if(d[q]<255){op=false;break;}
        try{lctx.clearRect(0,0,DIM,DIM);lctx.drawImage(c,0,0,DIM,DIM);}catch{}
        const nm='i'+String(i).padStart(4,'0')+'.raw';
        await ff.writeFile(nm,new Uint8Array(d.buffer));names.push(nm);
        if(onp)onp((i+1)/n);
      }
      AN_F1(base);
      let out=null;
      const L=[[fps,50],[fps,30],[Math.min(fps,12),22],[Math.min(fps,10),10],[Math.min(fps,10),1]].filter((x,j,a)=>!j||x[0]!==a[j-1][0]||x[1]!==a[j-1][1]);
      const st=[...L.map(x=>[...x,DIM]),...(pf.s?L.map(x=>[...x,256]):[])];
      for(let j=0;j<st.length;j++){
        const [f,q,z]=st[j];
        const code=await ff.exec(['-f','image2','-framerate',String(fps),'-pixel_format','rgba','-video_size',DIM+'x'+DIM,'-c:v','rawvideo','-i','i%04d.raw','-t',String(dur),'-vf','fps='+f+(z!==DIM?',scale='+z+':'+z:''),'-c:v',op?'libwebp':'libwebp_anim','-f','webp','-quality',String(q),'-loop','0','-y','o.webp']);
        if(code!==0)throw new Error('webp '+code);
        out=await ff.readFile('o.webp');
        if(out.byteLength<=pf.t)break;
        if(out.byteLength>pf.t*2.5)while(st[j+1]&&st[j+1][0]===f&&st[j+1][2]===z)j++;
      }
      if(!out?.byteLength)throw new Error('webp vacio');
      return out.byteLength<=pf.t||pf.s?new Blob([out],{type:'image/webp'}):null;
    }finally{
      for(const nm of [...names,'o.webp'])await ff.deleteFile(nm).catch(()=>{});
      lv.style.display='none';ckEl.style.display='';
    }
  });}

  async function VD_F1(file,fps,trim){
    const vm=await VM_OPEN(file),fr=[];
    try{
      const cut=TRIM_1({trim},vm.du);
      const n=Math.min(MAXFR,Math.max(1,Math.ceil(cut.d*fps-1e-8)));
      for(let i=0;i<n;i++){
        if(GONE)throw new Error('salida');
        fr.push(await createImageBitmap(await vm.frame(Math.min(vm.du-.001,cut.s+i/fps))));
      }
      return {fr,fps,dur:cut.d};
    }catch(e){AN_F1({fr});throw e;}
    finally{vm.close();}
  }

  async function FM_1(f,fn){return FF_JOB(async()=>{
    const ff=await FF_L1();
    await ff.createDir('/vc').catch(()=>{});
    await ff.mount(window.FFmpegWASM.FFFSType.WORKERFS,{files:[f]},'/vc');
    try{return await fn(ff,'/vc/'+f.name);}
    catch(e){FF_R1();throw e;}
    finally{await ff.unmount('/vc').catch(()=>{});}
  });}
  function FF_R1(){if(FFP){FFP.then(f=>f.terminate()).catch(()=>{});FFP=null;}}

  function FV_1(f,n,s=0,d=VID_MAX){
    s=Math.max(0,Number(s)||0);d=Math.max(.001,Math.min(VID_MAX,Number(d)||VID_MAX));
    n=Math.max(1,Math.min(MAXFR,Math.floor(n)||1));
    return FM_1(f,async(ff,p)=>{
      const scale='scale='+THM+':'+THM+':force_original_aspect_ratio=decrease';
      if(n===1){
        const name='vframe.png';
        try{
          // Keep the last frame at the requested time, including the frame held at EOF.
          // Very sparse VFR may need more history than the short first attempt.
          for(const begin of new Set([Math.max(0,s-.5),0])){
            if(GONE)throw new Error('salida');
            await ff.deleteFile(name).catch(()=>{});
            const filter="select='lte(t,"+String(s-begin+.0001)+")',"+scale;
            const code=await ff.exec(['-ss',String(begin),'-t',String(s-begin+.001),'-i',p,'-an','-vf',filter,'-fps_mode','passthrough','-update','1','-y',name]);
            if(code!==0)throw new Error('video '+code);
            try{const data=await ff.readFile(name);if(data.byteLength)return[new Blob([data],{type:'image/png'})];}catch{}
          }
          throw new Error('video');
        }finally{await ff.deleteFile(name).catch(()=>{});}
      }
      const o=[];
      try{
        const code=await ff.exec(['-ss',String(s),'-t',String(d),'-i',p,'-an','-vf',(n===1?'':'fps='+VID_FPS+',')+scale,'-frames:v',String(n),'-y','v%04d.png']);
        if(code!==0)throw new Error('video '+code);
        for(let i=1;i<=n;i++){
          const nm='v'+String(i).padStart(4,'0')+'.png';
          try{o.push(new Blob([await ff.readFile(nm)],{type:'image/png'}));}catch{break;}
        }
        if(!o.length)throw new Error('video');
        return o;
      }finally{for(let i=1;i<=n;i++)await ff.deleteFile('v'+String(i).padStart(4,'0')+'.png').catch(()=>{});}
    });
  }

  async function VD_F2(it){
    await FF_L1();
    const fr=[],cut=TRIM_1(it);
    try{
      for(const b of await FV_1(it.file,MAXFR,cut.s,cut.d)){
        if(GONE)throw new Error('salida');
        fr.push(await createImageBitmap(b));
      }
      return {fr,fps:VID_FPS,dur:Math.min(cut.d,fr.length/VID_FPS)};
    }catch(e){AN_F1({fr});if(it.fv||GONE)throw e;}
    return VD_F1(it.file,VID_FPS,it.trim);
  }

  async function PW_1(b,pf){return FF_JOB(async()=>{
    const ff=await FF_L1();let o=null;
    try{
      await ff.writeFile('p.png',new Uint8Array(await b.arrayBuffer()));
      for(const q of [90,75,60,45,30]){await ff.exec(['-i','p.png','-c:v','libwebp','-quality',String(q),'-y','p.webp']);o=await ff.readFile('p.webp');if(o.byteLength<=pf.st)break;}
    }finally{for(const n of ['p.png','p.webp'])await ff.deleteFile(n).catch(()=>{});}
    return o.byteLength<=pf.st||pf.s?new Blob([o],{type:'image/webp'}):null;
  });}
  async function ST_E1(it,ovs,pf){
    const img=it.isVid?await IMG_U1(it.pv):it.trim&&it.fp?await IMG_U1(it.fp):await IMG_L1(it.file);
    const c=document.createElement('canvas');c.width=DIM;c.height=DIM;
    const x=c.getContext('2d');DR_B1(x,img,it.crop);DR_O1(x,ovs,0);
    let b=null;
    for(const q of [.9,.75,.6,.45,.3]){b=await new Promise(r=>c.toBlob(r,'image/webp',q));if(!b)throw new Error('webp');if(b.type!=='image/webp')return WS_OK?await PW_1(b,pf):pf.s?b:null;if(b.size<=pf.st)return b;}
    return pf.s?b:null;
  }

  async function AN_PASS(it){
    if(it.trim)return false;
    if(!it.isAnim)return true;
    try{return (await AN_META(it.file,it.isAnim)).du<=VID_MAX+1e-8;}catch{return false;}
  }

  async function FX_1(it,ovs,pf){
    if(pf.s&&it.isWebp&&it.file.size<=pf.t&&!it.crop&&!it.ov.length&&await AN_PASS(it))return it.file;
    if(it.isAnim&&it.trim&&!it.fp)throw new Error('No se pudo recuperar el fotograma del tramo elegido');
    it.fx=1;
    return await ST_E1(it,ovs,pf);
  }

  async function EX_1(it,onp,pf=PB,lg){
    await KF_1(it);
    if(!it.isVid&&it.isWebp&&it.w===DIM&&it.h===DIM&&it.file.size<=(it.isAnim?pf.t:pf.st)&&!it.crop&&!it.ov.length&&await AN_PASS(it))return it.file;
    if(!WS_OK&&(it.isVid||it.isAnim)){const ov=await OV_P1(it.ov);try{return await FX_1(it,ov,pf);}finally{ov.forEach(o=>AN_F1(o.an));}}
    let base=null,ovs=[];
    try{
      if(it.isVid)base=await VD_F2(it);
      else if(it.isAnim){base=await AN_D1(it.file,it.isAnim,it.trim);if(!base){if(it.trim&&!it.fp)throw new Error('No se pudo recuperar el fotograma del tramo elegido');it.fx=1;lg?.('d');}}
      ovs=await OV_P1(it.ov);
      if(!base&&it.isAnim&&it.trim)return await ST_E1(it,ovs,pf);
      if(!base&&!ovs.some(o=>o.an))return await ST_E1(it,ovs,pf);
      if(!base)base={img:await IMG_L1(it.file)};
      const fps=base.fps||ovs.find(o=>o.an)?.an.fps||VID_FPS;
      try{return await WB_E1(it,base,ovs,fps,onp,pf);}catch(e){if(GONE||!(it.isAnim||it.isVid))throw e;FF_R1();lg?.('v:'+DG_1(e));return await FX_1(it,ovs,pf);}
    }finally{AN_F1(base);ovs.forEach(o=>AN_F1(o.an));}
  }

  function AU_1(a){
    return FM_1(a.f,async(ff,p)=>{
      let lm='';const lh=({message})=>{if(message!=='Aborted()')lm=message;};ff.on('log',lh);
      try{
        const r=await ff.exec(['-ss',String(a.s),'-t',String(a.d),'-i',p,'-vn','-map_metadata','-1','-ac','1','-ar','48000','-c:a','libopus','-b:a','48k','-f','ogg','-y','a.ogg']);
        const o=r===0?await ff.readFile('a.ogg'):null;
        if(!o?.byteLength||o.byteLength>AU_MX)throw new Error('audio '+r+' '+lm);
        return new Blob([o],{type:'audio/ogg'});
      }finally{ff.off('log',lh);await ff.deleteFile('a.ogg').catch(()=>{});}
    });
  }
  async function AU_2(a,lg){
    for(let k=1;k<3;k++){try{return await AU_1(a);}catch(e){if(GONE||/any stream/.test(e?.message))return null;lg('a'+k+':'+DG_1(e));FF_R1();}}
    return null;
  }
  const DG_1=e=>String(e?.message||e).replace(/\s+/g,' ').slice(0,90)+(document.hidden?' [oculta]':'');

  let ZP_T=null;
  const DS_1=()=>fetch('/api/stickers?d=1',{cache:'no-store'}).then(r=>r.ok?r.json():{}).then(j=>j.d!==false).catch(()=>true);
  async function WI_1(b){
    const d=new Uint8Array(await b.slice(0,30).arrayBuffer()),s=String.fromCharCode(...d.slice(12,16));
    if(s==='VP8X')return{w:1+(d[24]|d[25]<<8|d[26]<<16),h:1+(d[27]|d[28]<<8|d[29]<<16),a:!!(d[20]&2)};
    if(s==='VP8 ')return{w:(d[26]|d[27]<<8)&16383,h:(d[28]|d[29]<<8)&16383,a:false};
    if(s==='VP8L'){const v=(d[21]|d[22]<<8|d[23]<<16|d[24]<<24)>>>0;return{w:(v&16383)+1,h:((v>>>14)&16383)+1,a:false};}
    return{w:0,h:0,a:false};
  }
  async function D2_1(b){return FF_JOB(async()=>{
    const ff=await FF_L1(),img=await IMG_L1(b),c=document.createElement('canvas');c.width=DIM;c.height=DIM;
    const x=c.getContext('2d');
    try{
      for(let k=0;k<2;k++){x.clearRect(0,0,DIM,DIM);x.drawImage(img,0,0,DIM,DIM);if(k){const q=x.getImageData(0,0,1,1).data;x.fillStyle='rgb('+(255-q[0])+','+(255-q[1])+','+(255-q[2])+')';x.fillRect(0,0,1,1);}await ff.writeFile('d'+k+'.png',new Uint8Array(await(await new Promise(r=>c.toBlob(r,'image/png'))).arrayBuffer()));}
      await ff.exec(['-framerate','1','-i','d%d.png','-c:v','libwebp_anim','-f','webp','-quality','75','-loop','0','-y','d.webp']);
      const o=new Blob([await ff.readFile('d.webp')],{type:'image/webp'});
      return o.size<=LA&&(await WI_1(o)).a?o:null;
    }finally{for(const n of ['d0.png','d1.png','d.webp'])await ff.deleteFile(n).catch(()=>{});}
  });}
  async function ZP_1(fs){
    const T=ZP_T||(ZP_T=Array.from({length:256},(_,n)=>{for(let k=0;k<8;k++)n=n&1?0xEDB88320^(n>>>1):n>>>1;return n>>>0;}));
    const p=[],c=[],e=new TextEncoder();let o=0;
    for(const f of fs){
      const d=new Uint8Array(await f.b.arrayBuffer()),nm=e.encode(f.n);let r=-1;for(const x of d)r=T[(r^x)&255]^(r>>>8);r=(r^-1)>>>0;
      const h=new DataView(new ArrayBuffer(30)),k=new DataView(new ArrayBuffer(46));
      h.setUint32(0,0x04034b50,true);h.setUint16(4,10,true);h.setUint32(14,r,true);h.setUint32(18,d.length,true);h.setUint32(22,d.length,true);h.setUint16(26,nm.length,true);
      k.setUint32(0,0x02014b50,true);k.setUint16(4,20,true);k.setUint16(6,10,true);k.setUint32(16,r,true);k.setUint32(20,d.length,true);k.setUint32(24,d.length,true);k.setUint16(28,nm.length,true);k.setUint32(42,o,true);
      p.push(h,nm,d);c.push(k,nm);o+=30+nm.length+d.length;
    }
    const z=new DataView(new ArrayBuffer(22));z.setUint32(0,0x06054b50,true);z.setUint16(8,fs.length,true);z.setUint16(10,fs.length,true);z.setUint32(12,c.reduce((a,x)=>a+x.byteLength,0),true);z.setUint32(16,o,true);
    return new Blob([...p,...c,z],{type:'application/zip'});
  }
  async function AP_1(items){
    const o=[];
    items.forEach(it=>{delete it.fx;});
    for(let i=0;i<items.length;i++){
      const it=items[i];setProg(Math.round(i/items.length*80),'Preparando...');
      let b=it.o,k=b?await WI_1(b):null;
      if(!k||k.w!==DIM||k.h!==DIM||b.size>(k.a?LA:LS)){try{b=await EX_1(it,p=>setProg(Math.round((i+p)/items.length*80)),PA);}catch{b=null;}k=b?await WI_1(b):null;}
      if(b&&k.w===DIM&&k.h===DIM&&b.size<=(k.a?LA:LS))o.push({b,a:k.a});
    }
    if(GONE)return;
    if(o.some(x=>x.a)&&o.some(x=>!x.a))for(const x of o)if(!x.a){x.b=await D2_1(x.b).catch(()=>null);x.a=true;}
    const z=o.filter(x=>x.b).map((x,i)=>({n:(x.a?'animados/':'estaticos/')+N3(i+1)+'.webp',b:x.b}));
    if(z.length<3){ER_D1('La app Che😻Agana necesita al menos 3 stickers compatibles');return;}
    WV_1(await ZP_1(z),items.length-z.length,items.filter(it=>it.fx).length);
  }
  async function WV_1(zb,om,fx){
    const b64=await new Promise((ok,no)=>{const r=new FileReader();r.onload=()=>ok(String(r.result).split(',')[1]);r.onerror=no;r.readAsDataURL(zb);});
    if(GONE)return;
    const t=$('SK_AT');
    APD.querySelector('.SK_DF').hidden=true;$('SK_AM').hidden=true;
    $('SK_AX').hidden=!om&&!fx;$('SK_AX').textContent=[om?om+' no entran en el pack':'',fx?'Tu navegador no convierte animados: salieron fijos':''].filter(Boolean).join('\n');
    t.textContent='📲 Agregando a WhatsApp...';
    if(!APD.open)APD.showModal();
    window.__CS.onmessage=e=>{const d=String(e.data||'');if(d==='R:ok')setTimeout(()=>{if(APD.open&&t.textContent.startsWith('✅'))APD.close();},2000);t.textContent=d==='R:ok'?'✅ Agregado a WhatsApp':d==='R:cancel'?'No se agrego':d.startsWith('R:err:')?'WhatsApp rechazo el pack: '+d.slice(6):d.startsWith('R:x:')?'Error Che😻Agana '+d.slice(4):t.textContent;};
    window.__CS.postMessage('Z:'+b64);
  }
  function SA_1(m){
    if(GONE)return;
    $('SK_AT').textContent=m||'😿 Servidor saturado. Usa la app Che😻Agana para cargar los stickers a WhatsApp (sin sonido).';
    $('SK_AX').hidden=true;$('SK_AM').hidden=true;APD.querySelector('.SK_DF').hidden=false;$('SK_AL').classList.remove('SK_LT');
    $('SK_AO').onclick=AI_1;
    if(!APD.open)APD.showModal();
  }
  function AI_1(){
    let f=0;const h=()=>{f=1;};
    window.addEventListener('blur',h,{once:true});document.addEventListener('visibilitychange',h,{once:true});
    location.href='cheagana://open';
    setTimeout(()=>{window.removeEventListener('blur',h);document.removeEventListener('visibilitychange',h);if(f||GONE)return;$('SK_AM').hidden=false;const a=$('SK_AL');a.classList.remove('SK_LT');void a.offsetWidth;a.classList.add('SK_LT');},2000);
  }
  function PD_O(l){setProg(0,l);if(!PD.open)PD.showModal();document.body.style.overflow='hidden';}
  function PD_C(){if(PD.open)PD.close();document.body.style.overflow='';}
  PD.addEventListener('cancel',e=>e.preventDefault());

  $('sk-cf').onclick=async()=>{
    if(!P.length||PD.open)return;
    SN_P();
    const items=[...P];
    PD_O('Procesando...');
    let nA=0,nF=0,nX=0;
    if(MA){if(!window.__CS){PD_C();SA_1('Abri esta pagina desde la app Che😻Agana para cargar los stickers a WhatsApp.');return;}try{await AP_1(items);}catch(e){ER_D1('Error Stickers '+e.message);}finally{PD_C();}return;}
    if(!await DS_1()){PD_C();SA_1();return;}
    try{
      const form=new FormData(),urls=[],dg=[],ab=[];
      if(MU)for(let i=0;i<items.length;i++){const it=items[i];if(it.au&&(it.file||ID_OK)){ab[i]=await AU_2(it.au,s=>dg.push(N3(i+1)+s));if(!ab[i]&&!it.au.v)nA++;}}
      for(let i=0;i<items.length;i++){
        const it=items[i],n=N3(i+1),b0=Math.round(i/items.length*80),b1=Math.round((i+1)/items.length*80);
        const lb='Procesando '+(i+1)+'/'+items.length;setProg(b0,lb);
        if(!ID_OK&&it.u&&!it.trim&&(!it.file||it.isAnim&&!it.crop&&!it.ov.length)){urls.push([i+1,it.u]);if(ab[i])form.append('files',ab[i],n+'.ogg');continue;}
        delete it.fx;
        try{it.o=await EX_1(it,p=>setProg(Math.round(b0+(b1-b0)*p),lb),PB,s=>dg.push(n+s));form.append('files',it.o,n+'.webp');}catch(e){nF++;dg.push(n+'x:'+DG_1(e));continue;}
        if(it.fx)nX++;
        if(ab[i])form.append('files',ab[i],n+'.ogg');
      }
      if(GONE)return;
      if(nF===items.length)throw new Error('conversion');
      if(urls.length)form.append('urls',JSON.stringify(urls));
      if(dg.length)form.append('dg',(navigator.deviceMemory||'?')+'GB '+(navigator.hardwareConcurrency||'?')+'n '+dg.join(' | '));
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
      if(nX)ER_D1(nX+' salieron fijos');
    }catch(e){if(e.message==='sinwa')SA_1();else ER_D1(ER_1(e)||'Error Stickers '+e.message);}
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
      if(!await DS_1())throw new Error('sinwa');
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
    IMG_U1(it.trim&&it.fp?it.fp:it.pv).then(img=>{if(ED?.it===it){ctx.clearRect(0,0,DIM,DIM);DR_B1(ctx,img,it.crop);}}).catch(()=>{});
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
      it.ov.push({img,src,blob,x:DIM/2,y:DIM/2,s:ovNS,anim});
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
    if(ov){ov.s=Math.max(DIM/16,Math.min(DIM*15/16,ov.s+d));$('ov-sz-lbl').textContent=ov.s+'px';ovRL();}
    else{ovNS=Math.max(DIM/16,Math.min(DIM*15/16,ovNS+d));$('ov-sz-lbl').textContent=ovNS+'px';}
  }
  $('ov-sm').onclick=()=>ovSz(-DIM/16);
  $('ov-lg').onclick=()=>ovSz(DIM/16);
  $('sc-ov-f').onsubmit=e=>{e.preventDefault();ovSrch($('sc-ov-q').value.trim());};
  $('sc-ov-fi').onchange=e=>{const f=e.target.files[0];e.target.value='';if(f)ovAdd(f);};
  $('sc-ov-up').onclick=()=>$('sc-ov-fi').click();

  const cont=$('content');
  if(cont)cont.addEventListener('contentUnload',()=>{
    GONE=true;VMS.forEach(v=>v.close());
    document.removeEventListener('contentState',CS_1);HM.clear();
    document.removeEventListener('paste',DP_P);document.removeEventListener('dragover',DP_O);document.removeEventListener('drop',DP_D);
    ED_X();
    PD_C();
    P.forEach(FR_1);P=[];
    if(_gfRo){_gfRo.disconnect();_gfRo=null}SW?.destroy?.();
    if(SN_A){SN_A.pause();SN_A=null;}
    FF_R1();
  },{once:true});

  TL_1().then(()=>window.TS0()).catch(()=>{});

  if(MA){document.querySelector('#SK_TB button[data-t=t]').hidden=true;$('SK_DA').hidden=true;if(WS_OK)FF_L1().catch(()=>{});}
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
