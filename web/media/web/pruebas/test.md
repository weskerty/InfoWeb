<style>
.SK1{--SK_I:120px;text-align:center}
.SK1 [hidden]{display:none!important}
.SK_H{margin:0 0 14px}
.SK_TB,#SK_FT{justify-content:center}
.SK_SB{display:flex;gap:8px;margin:0 0 12px}
.SK_SB input{flex:1;min-width:0}
.SK_TX{color:var(--RD_MF);font-size:.9rem;margin:0 0 12px}
.sk-viewport{position:relative;overflow:hidden}
.sk-grid{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;align-items:flex-start;margin-bottom:8px;min-height:40px}
.sk-it{flex:0 0 var(--SK_I);width:var(--SK_I);height:var(--SK_I);padding:0;border-radius:14px;overflow:hidden;cursor:pointer;position:relative;background:var(--RD_M);border:2px solid var(--RD_L);box-sizing:border-box;transition:border-color .15s}
.sk-it img{width:100%;height:100%;object-fit:fill;display:block;pointer-events:none}
.sk-it[aria-pressed=true]{border-color:var(--ok)}
.sk-it[aria-pressed=true]::after{content:'✅';position:absolute;top:4px;right:6px;font-size:1.1em}
@media(hover:hover){.sk-it:hover{border-color:var(--RD_BHB)}}
.sk-ad-slot{flex:0 0 100%;display:flex;justify-content:center;min-width:0}
.sk-ad{display:block;max-width:100%;border:0;color-scheme:light}
.sk-page{display:contents}
.sk-more{display:flex;align-items:center;justify-content:center;gap:8px;flex-wrap:wrap;margin:8px 0;color:var(--RD_MF)}
.sk-more>img{width:28px;height:28px;object-fit:contain}
.sk-msg{color:var(--RD_MF);font-size:.9em;padding:20px 0;margin:0;grid-column:1/-1}
.sk-searching{display:flex;flex-direction:column;align-items:center;gap:8px;padding:32px 0;grid-column:1/-1;color:var(--RD_MF)}
.SK1 .SK_KL{margin:10px 0 0}
.SK_KL a{display:inline-flex}
.SK1 .SK_NT{margin:4px 0 0;color:var(--RD_MF);font-size:.72rem;opacity:.8}
.SK1 .SK_NT a{margin-top:6px;font-size:.85rem}
.SK_PL{display:grid;grid-template-columns:repeat(auto-fill,minmax(250px,1fr));gap:10px;margin-top:14px}
.SK_IMPORT{display:flex;align-items:center;justify-content:center;gap:10px;margin-top:14px;color:var(--RD_MF)}
.SK_IMPORT>img{width:40px;height:40px;object-fit:contain}
.SK_FI.SK_LOADING{display:grid;place-items:center}
.SK_FI.SK_LOADING>img{width:40px;height:40px;object-fit:contain}
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
.SK_PD.SK_RETRY{box-sizing:border-box;max-width:calc(100vw - 24px);max-height:calc(100vh - 24px);max-height:calc(100dvh - 24px);overflow-y:auto}
.SK_PD.SK_RETRY>*{box-sizing:border-box;min-width:0;max-width:100%}
.SK_PD.SK_RETRY>img,.SK_PD.SK_RETRY>canvas,.SK_PD.SK_RETRY>.sc-pbar-w{display:none!important}
#SK_SEND_REC .SK_DF{flex-wrap:wrap}
#SK_SEND_REC .SK_DF>button{min-width:0;max-width:100%;white-space:normal}
#SK_SEND_MSG{margin:0;white-space:normal}
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
.SK_RANGE_BT{display:flex;flex-wrap:wrap;justify-content:center;gap:8px}
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
<div class="sk-viewport"><div id="sk-grid" class="sk-grid"></div></div>
<div id="sk-pg" class="PG1"></div>
<div id="SK_MORE" class="sk-more" role="status" aria-live="polite" hidden></div>
<p class="SK_KL"><a href="https://klipy.com/" target="_blank" rel="noopener"><img src="web/adjuntos/Stickers_para_WhatsApp/KLIPY.svg" width="120" height="20" alt="Powered by KLIPY"></a></p>
<p class="SK_NT" id="SK_DA">Descarga la App Creadora de Stickers<br><a class="RD_B1" href="web/js/lib/Binarios/CheAgana.apk" target="_blank" rel="noopener" download>⬇️ Descargar la app</a></p>
</section>
<section id="SK_P" hidden>
<p class="SK_TX">Subi fotos, GIF o videos y elegi un tramo de hasta <span data-sk-seconds>30</span>s en Recortar, o elegi stickers en Buscar.</p>
<button type="button" id="SK_AD" class="RD_B1">📤 Agregar fotos, GIF o videos</button>
<input type="file" id="sc-in" accept="image/*,video/*" multiple hidden>
<div id="SK_IMPORT" class="SK_IMPORT" role="status" aria-live="polite" hidden><img id="SK_IMPORT_IMG" class="wait-anim" alt=""><span id="SK_IMPORT_TX"></span></div>
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
<div class="SK_RANGE_BT"><button type="button" id="SK_CP" disabled>▶️ Ver tramo</button></div>
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
<p id="SK_ML" class="SK_TX" aria-live="polite"></p>
<button type="button" id="SK_MP" disabled>▶️ Escuchar</button>
</div>
<audio id="SK_AU" preload="metadata" hidden></audio>
<p class="SK_TX">Hasta <span data-sk-seconds>30</span>s de sonido. Los stickers con sonido son nuevos en WhatsApp: si el telefono no los muestra, actualiza WhatsApp.</p>
</div>
<div class="SK_DF"><button type="button" id="SK_DC">Cancelar</button><button type="button" id="SK_DK">✅ Listo</button></div>
</dialog>
<dialog id="SK_PD" class="SK_PD"><img id="sc-ck" class="wait-anim" alt=""><canvas id="sc-lv" class="sc-lv" width="256" height="256"></canvas><div id="sc-prog-lbl"></div><p id="SK_JH" class="SK_TX" hidden>Para mas velocidad usa un navegador con JIT</p><div class="sc-pbar-w"><div class="sc-pbar" id="sc-pbar"></div></div><div id="SK_SEND_REC" hidden><p id="SK_SEND_MSG" class="SK_TX" role="status"></p><div class="SK_DF"><button type="button" id="SK_SEND_RETRY">Reintentar verificacion</button><button type="button" id="SK_SEND_CANCEL">Volver al pack</button></div></div></dialog>
</div>

<script>
(function(){
  const ADS=true,MU=true,KY='gCkt49niqCB9S2nlTLshWVfj8DOHunjpQCc8dAhJaxWhWfeZfvKVMmhvA9LeGR4W';
  const MAX_SECONDS=10,MAX_FPS=15;
  const KL_PAGE_SIZE=50,KL_KEEP_PAGES=6;
  const MA=window.__AN1==='webview';
  const VID_MAX=MA?Math.min(10,MAX_SECONDS):MAX_SECONDS,VID_FPS=MAX_FPS,AU_S=VID_MAX,MAXFR=Math.ceil(VID_MAX*VID_FPS),THM=512;
  const SK_MX=10,GAP=8,PG_FALLBACK=6,TG_W=75;
  const ITEM=innerWidth<480?86:120;
  const MAX_SZ=20*1024*1024,DIM=512,TARGET=900*1024,AU_MX=700*1024,LA=490*1024,LS=95*1024;
  const PB={t:TARGET,st:TARGET,s:1,max:MAX_SECONDS},PA={t:LA,st:LS,s:0,max:Math.min(10,MAX_SECONDS)};
  const ID_OK=typeof ImageDecoder!=='undefined';
  const WS_OK=(()=>{try{return new WebAssembly.Module(new Uint8Array([0,97,115,109,1,0,0,0]))instanceof WebAssembly.Module;}catch{return false;}})();
  const SD_RX=/^[a-f0-9]{12}$/;
  let JL=WS_OK?0:1,JA=JL;
  const JH_T='. Activa JIT en este sitio o usa otro navegador';
  function JL_1(e,v){if(v?JL:JA)return;const t=String(e?.message||e);if((window.WebAssembly&&e instanceof WebAssembly.RuntimeError)||/WebAssembly|wasm|out of bounds|unreachable/i.test(t)){if(v)JL=1;else JA=1;$('SK_JH').hidden=false;}}
  const $=id=>document.getElementById(id);
  const N3=n=>String(n).padStart(3,'0');
  const WA=window.__CFG?.waitAnim||'';
  let FFP=null,GONE=false,SB=0,TG_B=0,ED=null,ED_W=0,EA={},cropper=null,lastQ=null;
  let R=[],RF=[],PS=[],FT='',pg=0,P=[];
  let KQ=null,KL_VIEW=0,KL_GESTURE=null;
  const KL_NET=new Set(),KL_LIFE=new AbortController();
  let IMP_PENDING=0,IMP_RUNNING=false;
  const IMP_Q=[],KF_TASK=new Map();
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
  $('sc-ck').src=WA;$('SK_IMPORT_IMG').src=WA;
  $('SK1').querySelectorAll('[data-sk-seconds]').forEach(el=>el.textContent=VID_MAX);

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
                                                                                  
          if(n!==PG){PG=n;KL_REFLOW();}
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
  function setProg(p,l){pBar.style.width=p+'%';if(l!=null)pLbl.textContent=l;if(JL||JA)$('SK_JH').hidden=false;}
  function getCID(){try{let id=localStorage.getItem('sk_cid');if(!id){id=crypto.randomUUID();localStorage.setItem('sk_cid',id);}return id;}catch{return 'anon';}}
  function KN_1(it){
    if(it.type==='ad')return it.content?{type:'ad',content:it.content,width:it.width,height:it.height}:null;
    const f=it.file,url=f&&(typeof f.webp==='string'?f.webp:f.sm?.webp?.url);
    const hq=f&&typeof f==='object'?['hd','md','sm'].map(k=>f[k]?.webp).filter(w=>w?.url).sort((a,b)=>(b.width||0)-(a.width||0))[0]?.url:null;
    return url?{url,hq:hq||url,title:it.title||'',type:it.type,blur_preview:it.blur_preview||'',s:it.slug}:null;
  }
  const KT={sticker:'stickers',gif:'gifs',clip:'clips',static_meme:'static-memes'};
  function KH_1(l){if(KY)l.forEach(it=>{try{if(it.s&&KT[it.t])fetch(`https://api.klipy.com/api/v1/${KY}/${KT[it.t]}/share/${encodeURIComponent(it.s)}`,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({customer_id:getCID(),q:it.q})}).catch(()=>{});}catch{}});}
  async function KL_JSON(url,signal){
    const ac=new AbortController(),abort=()=>ac.abort();
    if(GONE||signal?.aborted)throw new Error('salida');
    KL_NET.add(ac);signal?.addEventListener('abort',abort,{once:true});
    const timer=setTimeout(abort,15000);
    try{
      const r=await fetch(url,{signal:ac.signal,cache:'no-store'});
      if(!r.ok)throw new Error('KLIPY '+r.status);
      return await r.json();
    }finally{clearTimeout(timer);signal?.removeEventListener('abort',abort);KL_NET.delete(ac);}
  }
  async function KL_GET(q,type,page,size,ad,signal){
    if(!KY)throw new Error('KLIPY');
    const p=new URLSearchParams({page,per_page:size,customer_id:getCID(),locale:'PY',content_filter:'off'});
    if(q)p.set('q',q);
    if(ad){
      const params={'ad-min-width':50,'ad-max-width':Math.max(50,Math.min(400,innerWidth-32)),'ad-min-height':50,'ad-max-height':250,'ad-device-w':Math.round(screen.width*(devicePixelRatio||1)),'ad-device-h':Math.round(screen.height*(devicePixelRatio||1)),'ad-pxratio':devicePixelRatio||1,'ad-language':(navigator.language||'es').split('-')[0]};
      for(const [key,value]of Object.entries(params))p.set(key,value);
    }
    const j=await KL_JSON(`https://api.klipy.com/api/v1/${KY}/${KT[type]}/${q?'search':'trending'}?${p}`,signal),d=j.data;
    if(!j.result||!Array.isArray(d?.data)||(d.current_page!=null&&Number(d.current_page)!==page))throw new Error('Respuesta KLIPY');
    const items=d.data.map(KN_1).filter(it=>it&&(it.type!=='ad'||ad));
    return{items,more:d.has_next===true&&items.some(it=>it.type!=='ad')};
  }
  async function KL_FALLBACK(q,ad,signal){
    const p=new URLSearchParams({cid:getCID()});if(q)p.set('q',q);if(!ad)p.set('ad','0');
    const j=await KL_JSON('/api/stickers?'+p,signal);
    if(!Array.isArray(j.data))throw new Error('Respuesta KLIPY');
    return j.data.filter(it=>it&&(it.type==='ad'?ad&&it.content:it.url));
  }
                                                                               
  async function KS_1(q,ad=false){
    try{
      const rows=await Promise.all(Object.keys(KT).map(type=>KL_GET(q,type,1,50,ad,KL_LIFE.signal)));
      return{data:rows.flatMap(row=>row.items)};
    }catch(e){if(GONE)throw e;return{data:await KL_FALLBACK(q,ad,KL_LIFE.signal)};}
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
  function FR_1(it){if(it.pin){PIN_FREE(it.pin);it.pin=null;}it.pr=(it.pr||0)+1;for(const k of ['pv','pc','fp'])if(it[k]?.startsWith('blob:'))URL.revokeObjectURL(it[k]);it.ov.forEach(o=>{if(o.src?.startsWith('blob:'))URL.revokeObjectURL(o.src);});}
  function PK_AD(it){it.ov=it.ov||[];it.t0=Date.now();P.push(it);UP_1();}
  function PK_RM(it){const i=P.indexOf(it);if(i<0)return;KF_TASK.get(it)?.ac.abort();FR_1(it);P.splice(i,1);UP_1();}
  function UP_1(){$('SK_PN').textContent=P.length;TR_R();if(!$('SK_P').hidden)PL_R();gEl.querySelectorAll('.sk-it').forEach(b=>b.setAttribute('aria-pressed',!!PK_F(b._u)));}

  function TH_1(it){
    const m=document.createElement('img'),c=it.crop;m.alt='';
    if(c&&it.isAnim&&!it.ov.length&&!it.pc){m.src=it.trim&&it.fp?it.fp:it.pv;Object.assign(m.style,{width:c.sw/c.w*100+'%',height:c.sh/c.h*100+'%',left:-c.x/c.w*100+'%',top:-c.y/c.h*100+'%'});const w=document.createElement('span');w.className='SK_CW';w.append(m);return w;}
    m.src=it.pc||(it.trim&&it.fp?it.fp:it.pv);return m;
  }
  function TR_R(){
    $('sk-cf').disabled=!!IMP_PENDING||!!KF_TASK.size||!!ED_W;
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
  const SE_1=(code,message,status=0)=>Object.assign(new Error(message),{sendCode:code,status});
  const TK_1=()=>TL_1().then(()=>window.TS1()).catch(()=>{throw SE_1('verify-local','No se pudo completar la verificacion en este navegador. El paquete todavia no se envio.');});
  const ER_1=e=>e.sendCode?e.message:e.message==='sinwa'?'✖️ Servidor Saturado 😿':e.message==='503'?'503 proba luego':e.message==='403'?'403 proba luego':e.message==='verificacion'?'No se pudo completar la verificacion en este navegador.':null;
  const SEND_REMOTE=e=>['verify-local','verify-server','forbidden','http','network','response'].includes(e?.sendCode)||['sinwa','403','503','verificacion'].includes(e?.message);
  let SEND_OP=null;
  const SEND_NET=new Set();
  async function SEND_BODY(res){
    if(!/application\/json/i.test(res.headers.get('content-type')||'')||!res.body)return null;
    const reader=res.body.getReader(),parts=[];let size=0;
    try{
      for(;;){const {done,value}=await reader.read();if(done)break;size+=value.byteLength;if(size>8192){reader.cancel().catch(()=>{});return null;}parts.push(value);}
      const bytes=new Uint8Array(size);let at=0;for(const part of parts){bytes.set(part,at);at+=part.byteLength;}
      return JSON.parse(new TextDecoder().decode(bytes));
    }catch{return null;}finally{try{reader.releaseLock();}catch{}}
  }
  async function SEND_HTTP(res){
    const body=await SEND_BODY(res),status=res.status;
                                                                                   
    if(status===403&&body?.error==='Error verificacion, recarga la pagina')return SE_1('verify-server','El servidor rechazo la verificacion. Podes reintentar sin convertir de nuevo.',status);
    if(status===403)return SE_1('forbidden','El servidor rechazo el envio (403). No se confirmo un problema de verificacion.',status);
    if(status===413)return SE_1('http','Demasiado Pesado (413).',status);
    if(status===429)return SE_1('http','Demasiados intentos. Espera un rato (429).',status);
    if(status===503)return SE_1('http','Servidor ocupado. (503).',status);
    return SE_1('http','El servidor no pudo completar la solicitud ('+status+'). ',status);
  }
  function SEND_TOKEN(ac){
    return new Promise((resolve,reject)=>{
      const abort=()=>{ac.signal.removeEventListener('abort',abort);reject(SE_1('cancel',''));};
      if(ac.signal.aborted){abort();return;}
      ac.signal.addEventListener('abort',abort,{once:true});
      TK_1().then(token=>{ac.signal.removeEventListener('abort',abort);resolve(token);},error=>{ac.signal.removeEventListener('abort',abort);reject(error);});
    });
  }
  async function SEND_POST(body,headers={},op=null){
    const ac=new AbortController();SEND_NET.add(ac);
    const live=()=>!GONE&&!ac.signal.aborted&&(!op||SEND_OP===op);
    try{
      if(!live())throw SE_1('cancel','');
      if(op)setProg(85,'Verificando...');
      const token=await SEND_TOKEN(ac);
      if(!live())throw SE_1('cancel','');
      if(op)setProg(88,'Subiendo...');
      let res;
      try{res=await fetch('/api/stickers',{method:'POST',headers:{...headers,'x-ts':token},body,signal:ac.signal});}
      catch(e){if(!live())throw SE_1('cancel','');throw SE_1('network','Se perdio la conexion durante el envio. No se pudo confirmar si el servidor lo recibio; no se reenvio automaticamente.');}
      if(!live())throw SE_1('cancel','');
      if(!res.ok)throw await SEND_HTTP(res);
      let result;
      try{result=await res.json();}catch{if(!live())throw SE_1('cancel','');throw SE_1('response','El servidor respondio, pero no se pudo confirmar el resultado. No se reenvio automaticamente.');}
      if(!live())throw SE_1('cancel','');
      return result;
    }finally{SEND_NET.delete(ac);}
  }
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

  function KL_PAGES(items,layout){
    for(let i=layout.items.length;i<items.length;i++){
      const it=items[i];let row=layout.pages.at(-1);
      if(!row||it.type!=='ad'&&row.count>=PG){row=[];row.count=0;layout.pages.push(row);}
      row.push(it);if(it.type!=='ad')row.count++;
    }
    layout.items=items;return layout.pages;
  }
  function KL_BATCH(s,type,items){
    if(!items.length)return;
    const batch={type,items};
    s.batches.push(batch);s.sources[type].batches.push(batch);
  }
  function KL_FALLBACK_BATCHES(s,items){
    let type='',row=[];
    const flush=()=>{if(type&&!s.sources[type].page)KL_BATCH(s,type,row);row=[];};
    for(const it of items){
      const next=it.type==='ad'?type:it.type;
      if(next&&!KT[next])continue;
      if(type&&next!==type)flush();
      if(next)type=next;row.push(it);
    }
    flush();
  }
  function KL_TYPES(s=KQ){return s?(FT?[FT]:Object.keys(KT)):[];}
  function KL_RESET_VIEW(){
    KL_VIEW++;
    gEl.style.transform='';gEl.style.transition='';gEl.style.visibility='';
    for(const el of gEl.parentElement.children)if(el!==gEl&&el.classList.contains('sk-grid'))el.style.visibility='hidden';
  }
  function KL_PICK(s,view=FT,retry=false){
    const types=Object.keys(KT),order=view?[view]:types.map((_,i)=>types[(s.turn+i)%types.length]);
    if(retry){const failed=order.find(t=>s.sources[t].more&&s.sources[t].error);if(failed)return failed;}
    for(const type of order){
      const src=s.sources[type];
      if(!view&&src.used<src.batches.length)return type;
      if(src.more&&(!src.error||retry))return type;
    }
    return '';
  }
  function KL_STATUS(){
    const el=$('SK_MORE');if(!el||GONE)return;
    el.textContent='';el.hidden=true;
    const s=KQ;if(!s||PS.length&&pg<PS.length-2)return;
    if(s.busy){
      if(!PS.length)return;
      el.hidden=false;const im=document.createElement('img');im.src=WA;im.alt='';im.className='wait-anim';
      const tx=document.createElement('span');tx.textContent='Cargando más...';el.append(im,tx);return;
    }
    const failed=KL_TYPES(s).some(t=>s.sources[t].error);
    if(!KL_PICK(s,FT,true)&&!failed)return;
    el.hidden=false;
    if(failed){const tx=document.createElement('span');tx.textContent='No se pudieron cargar más resultados.';el.append(tx);}
    const b=BT_1(failed?'Reintentar':'Cargar más',failed?'Reintentar carga':'Cargar más resultados');
    b.onclick=()=>K_MORE(failed);el.append(b);
  }
  function PS_1(){
    const s=KQ,batches=s?.batches||[];
    R=batches.flatMap(b=>b.items);
    const selected=s?(FT?s.sources[FT].batches:s.global):[];
    RF=selected.flatMap(b=>b.items);
    if(!s){PS=[];return;}
    let layout=s.layouts.get(FT);
    if(!layout||layout.size!==PG||layout.items.length>RF.length||!layout.items.every((it,i)=>it===RF[i])){
      layout?.pages.forEach(row=>row.el?.remove());
      layout={items:[],pages:[],size:PG};s.layouts.set(FT,layout);
    }
    PS=KL_PAGES(RF,layout);
  }
  function KL_POSITION(s=KQ){
    const pos=s?.positions.get(FT);if(!pos)return 0;
    const p=PS.findIndex(row=>row.includes(pos.anchor));
    return p<0?Math.min(pos.page,Math.max(0,PS.length-1)):p;
  }
  function KL_REFLOW(){
    if(!KQ||GONE)return;
    KL_GESTURE=null;
    for(const layout of KQ.layouts.values())for(const row of layout.pages)row.el?.remove();
    KQ.layouts.clear();PS_1();
    if(PS.length)renderPage(KL_POSITION(),false,false);else KL_EMPTY();
  }
  function KL_HIDE(){
    for(const node of [...gEl.children]){
      if(node.classList.contains('sk-page')||node.classList.contains('sk-ad-slot'))node.hidden=true;
      else node.remove();
    }
  }
  function KL_EMPTY(){
    KL_HIDE();gEl.append(KQ?.busy?LD_1('Buscando'):MS_1('Sin resultados'));
    pgEl.textContent='';KL_STATUS();
  }
  function K_LOAD(s,type){
    if(GONE||s!==KQ||s.ac.signal.aborted)return Promise.resolve();
    if(s.flight)return s.flight;
    const src=s.sources[type];if(!src.more)return Promise.resolve();
    s.busy=true;if(!PS.length)KL_EMPTY();else KL_STATUS();
    s.flight=(async()=>{
      try{
        const page=src.page+1,row=await KL_GET(s.q,type,page,s.perPage,ADS,s.ac.signal);
        if(GONE||s!==KQ||s.ac.signal.aborted)return;
        src.page=page;src.more=row.more;src.error='';KL_BATCH(s,type,row.items);
      }catch{
        if(GONE||s!==KQ||s.ac.signal.aborted)return;
        if(!s.fallbackTried){
          s.fallbackTried=true;
          try{
            const items=await KL_FALLBACK(s.q,ADS,s.ac.signal);
            if(GONE||s!==KQ||s.ac.signal.aborted)return;
                                                                               
                                                                               
            KL_FALLBACK_BATCHES(s,items);s.fallback=true;
            for(const x of Object.values(s.sources)){x.page=Math.max(1,x.page);x.more=false;x.error='';}
            return;
          }catch{if(GONE||s!==KQ||s.ac.signal.aborted)return;}
        }
        src.error='load';
      }
    })().finally(()=>{s.busy=false;s.flight=null;if(s===KQ&&!GONE)KL_STATUS();});
    return s.flight;
  }
  function KL_AUTO(){
    const s=KQ;if(!s||GONE||!PS[pg]||pg<PS.length-2)return;
    const edge=(FT?s.sources[FT].batches:s.global).at(-1);
    if(!edge||s.edges.get(FT)===edge)return;
    s.edges.set(FT,edge);
    void K_MORE(false,false);
  }
  function K_MORE(retry=false,advance=true){
    const s=KQ,view=FT,token=KL_VIEW;
    if(!s||GONE)return Promise.resolve();
    if(s.jobs.has(token))return s.jobs.get(token);
    const live=()=>!GONE&&s===KQ&&!s.ac.signal.aborted&&view===FT&&token===KL_VIEW;
    const oldRow=PS[pg];
    const job=(async()=>{
      if(s.flight)await s.flight;
      if(!live())return;
      if(retry&&!s.fallback)s.fallbackTried=false;
                                                                           
                                                            
      for(let i=0;i<Object.keys(KT).length&&live();i++){
        const type=KL_PICK(s,view,retry);if(!type)break;
        const src=s.sources[type];
        if(view||src.used>=src.batches.length||retry&&src.error)await K_LOAD(s,type);
        if(!live())return;
        if(view||src.error&&src.used>=src.batches.length)break;
        s.turn=(Object.keys(KT).indexOf(type)+1)%Object.keys(KT).length;
        if(src.used<src.batches.length){s.global.push(src.batches[src.used++]);break;}
      }
      if(!live())return;
      const oldLength=PS.length,atEnd=PS[pg]===oldRow&&pg===oldLength-1,wasFull=oldRow?.count>=PG;
      PS_1();
      if(PS.length){
        const next=advance&&oldLength&&atEnd&&wasFull&&PS.length>oldLength?oldLength:KL_POSITION(s);
        renderPage(next,false,false);
      }else KL_EMPTY();
    })().finally(()=>{s.jobs.delete(token);if(retry&&!oldRow&&live())KL_AUTO();});
    s.jobs.set(token,job);return job;
  }
  async function doFetch(q){
    if(GONE)return;
    KQ?.ac.abort();KL_RESET_VIEW();
    const s={q,ac:new AbortController(),perPage:KL_PAGE_SIZE,sources:{},batches:[],global:[],layouts:new Map(),turn:0,busy:false,flight:null,fallback:false,fallbackTried:false,positions:new Map(),edges:new Map(),jobs:new Map(),tick:0};
    for(const type of Object.keys(KT))s.sources[type]={page:0,more:true,error:'',batches:[],used:0};
    KQ=s;lastQ=q;R=[];RF=[];PS=[];pg=0;
    gEl.textContent='';gEl.append(LD_1('Buscando'));pgEl.textContent='';KL_STATUS();SW?.pre();
    const token=KL_VIEW;await K_MORE(false,false);
    if(s===KQ&&token===KL_VIEW)KL_AUTO();
  }
  function FL_1(){
    KL_RESET_VIEW();PS_1();pg=KL_POSITION();
    if(PS.length)renderPage(pg);else{
      KL_EMPTY();const token=KL_VIEW;
      K_MORE(false,false).then(()=>{if(token===KL_VIEW)KL_AUTO();});
    }
  }
  $('SK_FT').onclick=e=>{
    const b=e.target.closest('button');if(!b||b.dataset.f===FT)return;
    FT=b.dataset.f;$('SK_FT').querySelectorAll('button').forEach(x=>x.setAttribute('aria-pressed',x===b));
    if(KQ)FL_1();
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

  function AD_1(it,order){
                                                                              
                                                                             
    if(!it._slot){
      const slot=document.createElement('div');slot.className='sk-ad-slot';
      const f=document.createElement('iframe');f.className='sk-ad';f.title='Anuncio';f.scrolling='no';
      f.sandbox='allow-scripts allow-popups allow-popups-to-escape-sandbox';
      f.width=it.width;f.height=it.height;f.srcdoc=it.content;
      slot.append(f);it._slot=slot;gEl.append(slot);
    }
    it._slot.style.order=order;it._slot.hidden=false;
  }
  function KL_GHOST(el,row){
    row.forEach((it,i)=>{
      if(it.type!=='ad'){const b=CD_1(it,1);b.style.order=i;el.append(b);}
      else{
        const slot=document.createElement('div');slot.className='sk-ad-slot';slot.style.order=i;
        const d=document.createElement('div');d.className='sk-ad';d.style.cssText='width:'+it.width+'px;height:'+it.height+'px';
        slot.append(d);el.append(slot);
      }
    });
  }
  function renderPage(p,sw=false,load=true){
    if(GONE||!KQ||!PS[p])return;
    const s=KQ,row=PS[p],dir=p>pg?1:p<pg?-1:0;
    pg=p;s.positions.set(FT,{page:p,anchor:row.find(it=>it.type!=='ad')||row[0]});
    KL_HIDE();
    if(!row.el){
      row.el=document.createElement('div');row.el.className='sk-page';gEl.append(row.el);
      row.drawn=0;
    }
    for(let i=row.drawn;i<row.length;i++)if(row[i].type!=='ad'){const b=CD_1(row[i]);b.style.order=i;row.el.append(b);}
    row.drawn=row.length;
    row.el.hidden=false;row.used=++s.tick;
    row.forEach((it,i)=>{if(it.type==='ad')AD_1(it,i);});
    row.el.querySelectorAll('.sk-it').forEach(b=>b.setAttribute('aria-pressed',!!PK_F(b._u)));
    const mounted=[...s.layouts.values()].flatMap(v=>v.pages).filter(r=>r.el).sort((a,b)=>a.used-b.used);
    while(mounted.length>KL_KEEP_PAGES){const old=mounted.shift();old.el.remove();old.el=null;}
    renderPg();if(load)KL_AUTO();
    if(sw)return;
    if(SW)SW.pre();
    gEl.style.setProperty('--d',dir?(dir>0?'24px':'-24px'):'0px');
    gEl.classList.remove('AN1');void gEl.offsetWidth;gEl.classList.add('AN1');
    if(dir)$('SK_B').scrollIntoView({behavior:'smooth',block:'start'});
  }

  function renderPg(){
    if(GONE)return;KL_STATUS();
    if(!_GF){loadGF().then(g=>{if(g&&!GONE)renderPg()});return}
    if(!SW){
      gEl.addEventListener('pointerdown',()=>{KL_GESTURE={session:KQ,view:KL_VIEW};},{signal:KL_LIFE.signal});
      SW=_GF.SW1(gEl,{sig:KL_LIFE.signal,n:()=>PS.length,p:()=>pg,ok:()=>!GONE&&!$('SK_B').hidden,
      go:i=>{if(KL_GESTURE?.session===KQ&&KL_GESTURE.view===KL_VIEW)renderPage(i,1);},
      fill:(el,i)=>KL_GHOST(el,PS[i]||[])});SW.pre()}
    _GF.PN1(pgEl,pg,PS.length,renderPage);
  }

  gEl.onclick=e=>{
    const b=e.target.closest('.sk-it');if(!b||!b._u)return;
    const it=PK_F(b._u);
    if(it){PK_RM(it);b.setAttribute('aria-pressed','false');return;}
    if(P.length+IMP_PENDING>=SK_MX){ER_D1('Maximo '+SK_MX+' stickers por pack');return;}
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
    if(!P.length){if(!IMP_PENDING)L.append(MS_1('Tu pack esta vacio'));return;}
    P.forEach(it=>{
      const d=document.createElement('div');d.className='sc-fr';
      const f=document.createElement('div');f.className='SK_FI';d.append(f);
      if(it.loading){f.classList.add('SK_LOADING');const wait=document.createElement('img');wait.className='wait-anim';wait.alt='Cargando';wait.src=WA;f.append(wait);}else f.append(TH_1(it));
      if(it.isVid){const s=document.createElement('span');s.className='SK_BG';s.textContent='🎬';f.append(s);}
      const x=BT_1('✕','Quitar','sc-rm');x.onclick=()=>PK_RM(it);d.append(x);
      const t=document.createElement('div');t.className='SK_TO';
      [['c','✂️','Recortar',!!it.crop||!!it.trim],['o','🖼️','Imagen',it.ov.length>0],['m','🎵','Sonido',!!it.au]].filter(x=>MU&&!MA||x[0]!=='m').forEach(([md,ic,lb,on])=>{
        const b=BT_1(ic+' '+lb+(on?' ✅':''),lb);b.setAttribute('aria-pressed',on);b.disabled=!!it.loading||!!IMP_PENDING;b.onclick=()=>ED_O(it,md);t.append(b);
      });
      d.append(t);L.append(d);
    });
  }

                                                                                 
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
    for(const [id,v] of [[p+'S',s],[p+'E',end]]){
      const el=$(id);el.min='0';el.max=String(du);el.step='any';el.value=String(+v.toFixed(3));
      el.setAttribute('aria-valuetext',SK_TIME(v));
    }
    const h=$(p+'H');h.style.left='calc(11px + (100% - 22px) * '+s/du+')';h.style.width='calc((100% - 22px) * '+d/du+')';
  }

  const VMS=new Set();
  function SK_BLOB(c){return new Promise((ok,no)=>c.toBlob(b=>b?ok(b):no(new Error('fotograma')),'image/png'));}
  function SK_PAINT_TICK(v,alive){
    return new Promise((ok,no)=>{
      let id=0,raf=0,done=false;
      const end=()=>{if(done)return;done=true;clearTimeout(to);if(id)v.cancelVideoFrameCallback?.(id);if(raf)cancelAnimationFrame(raf);alive()?ok():no(new Error('salida'));};
      const to=setTimeout(end,90);
                                                                               
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
      vm.seek=async (time,paint=false)=>{
        if(!alive())throw new Error('salida');
        const t=Math.max(0,Math.min(Number(time)||0,vm.du-.001));
        const settled=wait(['seeked','loadeddata','canplay','timeupdate'],()=>!v.seeking&&v.readyState>=2&&Math.abs(v.currentTime-t)<.025);
        try{if(Math.abs(v.currentTime-t)>.0001||v.readyState<2)v.currentTime=t;}catch(e){vm.close();await settled.catch(()=>{});throw e;}
        await settled;if(paint)await SK_PAINT_TICK(v,alive);
        if(!alive()||v.seeking||v.readyState<2||!v.videoWidth||!v.videoHeight)throw new Error('fotograma');
      };
      vm.bitmap=async time=>{
        await vm.seek(time);
        const k=Math.min(1,THM/Math.max(v.videoWidth,v.videoHeight));
        const options={resizeWidth:Math.max(1,Math.round(v.videoWidth*k)),resizeHeight:Math.max(1,Math.round(v.videoHeight*k)),resizeQuality:'high'};
        let bitmap;
        try{bitmap=await createImageBitmap(v,options);}catch{
          await SK_PAINT_TICK(v,alive);bitmap=await createImageBitmap(v,options);
        }
        if(!alive()){bitmap.close();throw new Error('salida');}
        return bitmap;
      };
      vm.frame=async time=>{
        await vm.seek(time,true);
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
    let closed=false,reader=null;
    const vm={du:0,close(){if(closed)return;closed=true;reader?.close();VMS.delete(vm);}};
    VMS.add(vm);onCreate?.(vm);
    try{
      reader=await AN_READER(it.file,it.isAnim);
      if(GONE||closed)throw new Error('salida');
      vm.du=reader.meta.du;
      vm.frame=async t=>{
        if(GONE||closed)throw new Error('salida');
        const frame=await reader.get(AN_IDX(reader.meta,Math.max(0,Math.min(t,vm.du-.000001))));
        if(GONE||closed)throw new Error('salida');
        const w=frame.displayWidth||frame.width,h=frame.displayHeight||frame.height,k=Math.min(1,THM/Math.max(w,h));
        const c=document.createElement('canvas');
        c.width=Math.max(1,Math.round(w*k));c.height=Math.max(1,Math.round(h*k));
        try{c.getContext('2d').drawImage(frame,0,0,c.width,c.height);return await SK_BLOB(c);}
        finally{c.width=c.height=1;}
      };
      return vm;
    }catch(e){reader?.close();vm.close();throw e;}
  }

  async function MK_F(f){
    const isVid=f.type.startsWith('video/'),isWebp=f.type==='image/webp';
    if(isVid){
      let {pv,du,pt}=await getVidThumb(f),fv=!pv;
      if(GONE){if(pv?.startsWith('blob:'))URL.revokeObjectURL(pv);throw new Error('salida');}
      if(fv){
        du=du||await VF_META(f).catch(()=>0);pt=du?Math.min(.5,du*.1):pt;
        const b=(await FV_1(f,1,pt,.25))[0];if(GONE)throw new Error('salida');pv=URL.createObjectURL(b);
      }
      return{file:f,pv,du,pt,fv,isVid,isWebp:false,isAnim:false,sq:false,au:MU?{f,s:0,d:Math.min(AU_S,du||AU_S),v:1}:null};
    }
    const bm=await createImageBitmap(f),w=bm.width,h=bm.height,r=w/h;bm.close();
    const isAnim=await AN_T1(f);if(GONE)throw new Error('salida');
    return{file:f,pv:URL.createObjectURL(f),isVid,isWebp,isAnim,sq:r>=.8&&r<=1.25,w,h};
  }

  let PIN_MEM=0,PIN_DIR=null;
  function PIN_FREE(p){if(!p)return;if(p.m){PIN_MEM=Math.max(0,PIN_MEM-p.m);p.m=0;}if(p.n&&PIN_DIR){const n=p.n;p.n='';PIN_DIR.removeEntry(n).catch(()=>{});}}
  async function PIN_FILE(f){
    const own={f,m:0,n:''};
    if(GONE||!f||!Number.isFinite(f.size)||f.size<=0)return own;
    const wrap=g=>new File([g],f.name,{type:f.type,lastModified:f.lastModified});
    if(PIN_MEM+f.size<=RAW_BUDGET()){
      PIN_MEM+=f.size;
      try{
        const buf=await f.arrayBuffer();
        if(buf.byteLength!==f.size)throw new Error('lectura');
        return{f:wrap(buf),m:f.size,n:''};
      }catch{PIN_MEM=Math.max(0,PIN_MEM-f.size);return own;}
    }
    if(f.size>512*1024*1024||RAW_BLOCKED||!navigator.storage?.getDirectory)return own;
    let n='';
    try{
      const est=await navigator.storage.estimate?.();
      if(est?.quota&&est.quota-(est.usage||0)<f.size*1.15)return own;
      if(!PIN_DIR){
        PIN_DIR=await(await navigator.storage.getDirectory()).getDirectoryHandle('sk-stickers-tmp',{create:true});
        for await(const [k,h] of PIN_DIR.entries())if(/^sk-[a-f0-9-]+\.pin$/.test(k)&&h.kind==='file'){try{if(Date.now()-(await h.getFile()).lastModified>86400000)await PIN_DIR.removeEntry(k);}catch{}}
      }
      n='sk-'+crypto.randomUUID()+'.pin';
      const h=await PIN_DIR.getFileHandle(n,{create:true});
      await f.stream().pipeTo(await h.createWritable());
      const g=await h.getFile();
      if(g.size!==f.size||GONE)throw new Error('copia');
      return{f:wrap(g),m:0,n};
    }catch(e){
      if(RAW_QUOTA(e))RAW_BLOCKED=true;
      if(n&&PIN_DIR)await PIN_DIR.removeEntry(n).catch(()=>{});
      return own;
    }
  }
  function IMP_UI(){
    if(GONE)return;
    const count=IMP_PENDING+KF_TASK.size;
    $('SK_IMPORT').hidden=!count;$('SK_P').setAttribute('aria-busy',String(!!count));
    $('SK_IMPORT_TX').textContent=count?'Cargando '+count+(count===1?' archivo...':' archivos...'):'';
    UP_1();
  }
  function KF_1(it){
    if(it.file)return Promise.resolve();
    const prev=KF_TASK.get(it);if(prev)return prev.promise;
    if(GONE)return Promise.reject(new Error('salida'));
    const job={ac:new AbortController(),promise:null},owned=P.includes(it);
    KF_TASK.set(it,job);it.loading=true;IMP_UI();
    job.promise=(async()=>{
      const live=()=>!GONE&&!job.ac.signal.aborted&&(!owned||P.includes(it));
      try{
        const b=await fetch(it.h||it.u,{signal:job.ac.signal}).then(r=>{if(!r.ok)throw new Error(r.status);return r.blob();});
        if(!live())throw new Error('salida');
        const ty=b.type.startsWith('image/')?b.type:'image/webp';
        const pv=it.pv,next=await MK_F(new File([b],'k.'+ty.split('/')[1],{type:ty}));
        if(!live()){next.ov=[];FR_1(next);throw new Error('salida');}
        Object.assign(it,next);
        if(pv?.startsWith('blob:'))URL.revokeObjectURL(pv);
      }finally{
        if(KF_TASK.get(it)===job)KF_TASK.delete(it);
        delete it.loading;IMP_UI();
      }
    })();
    return job.promise;
  }
  function IMP_STOP(){
    for(const job of IMP_Q.splice(0)){job.f=null;job.done(false);}
    IMP_PENDING=0;KF_TASK.forEach(job=>job.ac.abort());KF_TASK.clear();
    $('SK_IMPORT').hidden=true;$('SK_P').removeAttribute('aria-busy');
  }
  async function IMP_RUN(){
    if(IMP_RUNNING)return;
    IMP_RUNNING=true;
    try{
                                                                               
      await new Promise(resolve=>setTimeout(resolve,0));
      while(IMP_Q.length&&!GONE){
        const job=IMP_Q.shift(),f=job.f;job.f=null;let added=false,pin=null;
        try{
          if(P.length>=SK_MX){ER_D1('Maximo '+SK_MX+' stickers por pack');continue;}
          pin=await PIN_FILE(f);
          const it=await MK_F(pin.f);
          if(GONE){it.ov=[];FR_1(it);continue;}
          it.pin=pin;pin=null;
          PK_AD(it);added=true;
        }catch{if(!GONE)ER_D1(f.type.startsWith('video/')?'Video no compatible':'Imagen no compatible');}
        finally{if(pin)PIN_FREE(pin);IMP_PENDING=Math.max(0,IMP_PENDING-1);job.done(added);IMP_UI();}
      }
    }finally{IMP_RUNNING=false;}
  }
  function addFiles(list){
    if(GONE||DG.open||PD.open||ED_W)return Promise.resolve([]);
    const waits=[];
    for(const f of list){
      if(P.length+IMP_PENDING>=SK_MX){ER_D1('Maximo '+SK_MX+' stickers por pack');break;}
      const v=f.type.startsWith('video/');
      if(!v&&!f.type.startsWith('image/')){ER_D1('Archivo no compatible');continue;}
      if(!v&&f.size>MAX_SZ){ER_D1('Maximo 20MB por imagen');continue;}
      waits.push(new Promise(done=>IMP_Q.push({f,done})));IMP_PENDING++;
    }
    if(waits.length){TB_1('p');IMP_UI();void IMP_RUN();}
    return Promise.all(waits);
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
    for(const id of ['SK_CS','SK_CE'])$(id).disabled=!e.ready||!!e.opening;
  }
  function CR_STOP(e){
    if(!e)return;clearTimeout(e.playTimer);e.playTimer=0;e.playing=false;e.playVersion=(e.playVersion||0)+1;
    if(e.sound){e.sound.active=false;clearTimeout(e.sound.timer);e.sound.timer=0;e.sound.a.pause();}
    if(CR_LIVE(e))$('SK_CP').textContent='▶️ Ver tramo';
  }
  function CR_SOUND_CLOSE(e){
    const s=e?.sound;if(!s)return;e.sound=null;s.closed=true;s.active=false;
    clearTimeout(s.timer);s.timer=0;s.a.onloadedmetadata=null;s.a.onerror=null;s.a.onended=null;
    s.a.pause();s.a.removeAttribute('src');s.a.load();s.a.remove();URL.revokeObjectURL(s.url);
  }
  function CR_SOUND_TAIL(e,s,elapsed){
    if(!CR_LIVE(e)||e.sound!==s||!s.active||s.tail)return;
    clearTimeout(s.timer);s.timer=0;s.tail=true;s.tailElapsed=Math.max(0,Math.min(e.range.d,Number(elapsed)||0));s.tailAt=performance.now();s.a.pause();
  }
  function CR_SOUND_OPEN(e){
    if(MA||!MU||!e.it.au?.f)return;
    const spec={...e.it.au},original=!!e.it.isVid&&!!(spec.v||spec.f===e.it.file),f=original?e.it.file:spec.f;
    if(!f)return;
    const a=document.createElement('audio'),url=URL.createObjectURL(f),s={a,url,spec,original,active:false,closed:false,unavailable:false,warning:''};
    e.sound=s;a.preload='metadata';a.className='SK_MEDIA';a.setAttribute('aria-hidden','true');a.tabIndex=-1;
    const live=()=>CR_LIVE(e)&&e.sound===s&&!s.closed;
    a.onloadedmetadata=()=>{if(live()&&s.active&&!s.tail)try{a.currentTime=s.start;}catch{}};
    a.onerror=()=>{
      if(!live())return;s.unavailable=true;s.warning='Vista previa sin sonido: este archivo no se puede reproducir aquí.';
      CR_SOUND_TAIL(e,s,e.playElapsed||0);$('SK_CStatus').textContent=s.warning;
    };
    a.onended=()=>{if(live()&&s.active&&a.ended)CR_SOUND_TAIL(e,s,Math.min(s.duration,Math.max(0,a.currentTime-s.start)));};
    $('SK1').append(a);a.src=url;a.load();
  }
  function CR_SOUND_START(e,version){
    const s=e.sound;if(!s||s.unavailable)return;
    s.start=s.original?e.range.s:Math.max(0,Number(s.spec.s)||0);
    const requested=s.original?e.range.d:Number(s.spec.d);
    const available=Number.isFinite(s.a.duration)?Math.max(0,s.a.duration-s.start):Infinity;
    s.duration=Math.max(0,Math.min(e.range.d,Number.isFinite(requested)?requested:AU_S,available));
    s.active=s.duration>0;s.tail=false;s.warning='';
    if(!s.active)return;
    const live=()=>CR_LIVE(e)&&e.playing&&e.playVersion===version&&e.sound===s&&s.active;
    const fail=()=>{
      if(!live())return;s.warning='Vista previa sin sonido: no se pudo iniciar el audio.';
      CR_SOUND_TAIL(e,s,e.playElapsed||0);$('SK_CStatus').textContent=s.warning;
    };
                                                                                            
    try{s.a.currentTime=s.start;}catch{}
    try{Promise.resolve(s.a.play()).catch(fail);}catch{fail();}
    const check=()=>{
      if(!live()||s.tail)return;
      const elapsed=Math.max(0,s.a.currentTime-s.start),left=s.duration-elapsed;
      if(s.a.ended||left<=0){CR_SOUND_TAIL(e,s,Math.min(elapsed,s.duration));return;}
      s.timer=setTimeout(check,Math.max(10,Math.min(80,left*1000)));
    };check();
  }
  function CR_PLAY_TIME(e){
    const s=e.sound,now=performance.now();
    if(!s?.active)return (now-e.playClock)/1000;
    if(s.tail)return s.tailElapsed+(now-s.tailAt)/1000;
    const elapsed=Math.max(0,s.a.currentTime-s.start);
    if(s.a.ended||elapsed>=s.duration){CR_SOUND_TAIL(e,s,Math.min(elapsed,s.duration));return s.tailElapsed;}
    return elapsed;
  }
  function CR_CLOSE(e){
    if(!e)return;CR_STOP(e);CR_SOUND_CLOSE(e);e.dragStop?.();e.want=null;e.source?.close();e.source=null;
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
      cropImg.onload=()=>CR_BUILD(e);cropImg.onerror=()=>{if(CR_LIVE(e)){$('SK_CStatus').textContent='No se pudo mostrar la imagen. Cerra y volve a abrir Recortar.';e.imageLoading=false;e.ready=false;CR_STATE(e);}};
      cropImg.src=url;
    }
  }
  async function CR_BUILD(e){
    try{
      await loadCropperJS();if(!CR_LIVE(e)||cropper)return;
      const saved=e.it.crop,w=cropImg.naturalWidth,h=cropImg.naturalHeight;
      const o={viewMode:1,dragMode:'crop',movable:false,zoomable:false,zoomOnTouch:false,zoomOnWheel:false,rotatable:false,scalable:false,toggleDragModeOnDblclick:false,cropBoxMovable:true,cropBoxResizable:true,background:false,autoCropArea:.9,cropstart(){if(CR_LIVE(e)){CR_STOP(e);e.noCrop=false;}},ready(){
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
          $('SK_CStatus').textContent=e.sound?.warning||'';
          if(e.imageLoading)break;
        }catch{
          if(!CR_LIVE(e))return;
          if(!e.want){CR_STOP(e);$('SK_CStatus').textContent='No se pudo leer ese fotograma. Proba mover el tramo.';}
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
  for(const [id,edge] of [['SK_CS','s'],['SK_CE','e']]){
    $(id).oninput=ev=>{if(ED)CR_RANGE(ED,ev.target.value,edge);};
  }
  $('SK_CP').onclick=()=>{
    const e=ED;if(!CR_LIVE(e)||!e.source)return;
    if(e.playing){CR_STOP(e);return;}
    CR_STOP(e);e.playing=true;e.playElapsed=0;e.playClock=performance.now();const version=e.playVersion;
    $('SK_CP').textContent='⏸️ Pausa';
    CR_SOUND_START(e,version);
    const tick=()=>{
      if(!CR_LIVE(e)||!e.playing||e.playVersion!==version)return;
      const elapsed=CR_PLAY_TIME(e);e.playElapsed=Math.max(0,Math.min(e.range.d,elapsed));
      if(elapsed>=e.range.d){CR_STOP(e);CR_REQUEST(e,Math.max(e.range.s,e.range.s+e.range.d-.001));return;}
      CR_REQUEST(e,e.range.s+elapsed);e.playTimer=setTimeout(tick,e.source.slow?600:140);
    };tick();
  };
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
    $('SK_CT').hidden=true;$('SK_CP').textContent='▶️ Ver tramo';
    $('SK_CStatus').textContent='Cargando imagen...';CR_STATE(e);
    try{CR_SOUND_OPEN(e);}catch{}
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
    if(e.source){
      const du=e.source.du,r=SK_RANGE(du,e.range.s,e.range.d);
      if(du<=VID_MAX&&r.s<.001&&Math.abs(r.d-du)<.001)delete it.trim;else it.trim={...r};
    }
    if(e.source&&it.au?.v){const r=TRIM_1(it);it.au={...it.au,s:r.s,d:r.d};}
    if(e.frameBlob&&(it.isVid||it.isAnim)){
      const key=it.isVid?'pv':'fp',old=it[key];it[key]=URL.createObjectURL(e.frameBlob);it.pt=e.pt;if(old?.startsWith('blob:'))URL.revokeObjectURL(old);
    }
    delete it.o;return true;
  }

  async function ED_O(it,md,h){
    if(ED||ED_W||GONE||PD.open||IMP_PENDING)return;
    ED_W=1;IMP_UI();
    try{
      if(!it.file)await KF_1(it);
    }catch(e){if(!GONE&&P.includes(it))ER_D1('Error Klipy '+e.message);return;}
    finally{ED_W=0;IMP_UI();}
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
    if(it.isAnim&&!it.adu&&it.file)AN_META(it.file,it.isAnim).then(m=>{it.adu=m.du;}).catch(()=>{});
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
      $('SK_ML').textContent=v?'Sigue el tramo del video':'';
    }
    $('SK_MN').textContent=v?'🎬 Sonido del video':EA.f.r?'🎤 Grabación':EA.f.name||'Audio';
    for(const id of ['SK_MS','SK_ME'])$(id).disabled=!MU_READY||v;
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
  const AU_DEF=it=>Math.min(AU_S,(it?.isVid?TRIM_1(it).d:it?.adu)||AU_S);
  $('SK_MF').onchange=e=>{
    const f=e.target.files[0];e.target.value='';const ed=MU_PICK;MU_PICK=null;
    if(!f||!ED||ED!==ed||ED.md!=='m'||GONE)return;
    EA={f,s:0,d:AU_DEF(ED.it),v:false,du:0};MU_L();
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
    const mk=o=>{try{return new MediaRecorder(s,o);}catch{return null;}},mt=['audio/webm;codecs=opus','audio/ogg;codecs=opus'].find(t=>window.MediaRecorder.isTypeSupported?.(t)),m=(mt&&mk({mimeType:mt}))||new MediaRecorder(s),ch=[],t0=Date.now(),r={m,s};
    const T=()=>{const e=(Date.now()-t0)/1000;if(e>=AU_S)return RC_X(1);$('SK_MR').textContent='⏹️ Detener · '+Math.ceil(AU_S-e)+'s';};
    m.ondataavailable=e=>{if(e.data.size)ch.push(e.data);};
    m.onstop=()=>{if(!r.k||ED!==ed||MU_GEN!==gen||GONE||!ch.length)return;const ty=m.mimeType||ch[0].type,f=new File(ch,'Grabacion.'+(/mp4/.test(ty)?'m4a':/ogg/.test(ty)?'ogg':'webm'),{type:ty});f.r=1;f.du=Math.min(AU_S,(Date.now()-t0)/1000);EA={f,s:0,d:Math.min(AU_S,f.du),v:false,du:f.du};MU_L();};
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


  function AN_FPS(times,dur){
    const gcd=(a,b)=>{while(b){const r=a%b;a=b;b=r;}return a;};
    let grid=Math.max(1,Math.round(dur*1000));
    for(const time of times){const ms=Math.round(time*1000);if(ms>0)grid=gcd(grid,ms);if(grid<=1000/VID_FPS)return VID_FPS;}
    return Math.max(1,Math.min(VID_FPS,1000/grid));
  }

  function AN_AT(a,time,loop=false){
    if(!a?.fr?.length)return a?.img;
    const dur=a.dur||a.fr.length/(a.fps||VID_FPS);
    time=loop&&dur>0?((time%dur)+dur)%dur:Math.max(0,time);
    let i;
    if(a.times?.length){
      let lo=0,hi=a.times.length-1;
      while(lo<hi){const mid=Math.ceil((lo+hi)/2);if(a.times[mid]<=time+1e-8)lo=mid;else hi=mid-1;}
      i=lo;
    }else i=Math.floor(time*(a.fps||VID_FPS)+1e-8);
    return a.fr[Math.max(0,Math.min(a.fr.length-1,i))];
  }

  function AN_MIX_FPS(base,ovs,dur){
    const times=[0,dur];let floor=1;
    const add=(a,loop)=>{
      if(!a||!a.get&&!a.fr?.length)return;
      floor=Math.max(floor,a.fps||VID_FPS);
      if(!a.times?.length)return;
      const period=a.dur||dur;
      for(let offset=0;offset<dur-1e-8;offset+=loop?period:dur){
        for(const t of a.times){const at=offset+t;if(at>0&&at<dur)times.push(at);}
        if(times.length>MAXFR*MAXFR){floor=VID_FPS;return;}
        if(!loop||period<=0)break;
      }
    };
    add(base,false);ovs.forEach(o=>add(o.an,true));
    return Math.max(1,Math.min(VID_FPS,Math.max(floor,AN_FPS(times,dur))));
  }

                                                                  
  function AN_R_SIZE(w,h){
    if(!Number.isInteger(w)||!Number.isInteger(h)||w<1||h<1||w>4096||h>4096||w*h>8388608)throw new Error('animacion demasiado grande');
  }
  function AN_R_WEBP(b){
    const need=(p,n,end=b.length)=>{if(!Number.isSafeInteger(p)||!Number.isSafeInteger(n)||p<0||n<0||p+n>end)throw new Error('animacion incompleta');};
    const tag=p=>{need(p,4);return String.fromCharCode(b[p],b[p+1],b[p+2],b[p+3]);};
    const u24=p=>{need(p,3);return b[p]|b[p+1]<<8|b[p+2]<<16;};
    const u32=p=>{need(p,4);return (b[p]|b[p+1]<<8|b[p+2]<<16|b[p+3]<<24)>>>0;};
    if(tag(0)!=='RIFF'||tag(8)!=='WEBP')throw new Error('animacion WebP');
    const end=u32(4)+8;need(0,end);if(end<30)throw new Error('animacion incompleta');
    let w=0,h=0,anim=false,icc=null;const frames=[];
    for(let p=12;p<end;){
      need(p,8,end);const t=tag(p),n=u32(p+4),s=p+8,next=s+n+(n&1);need(s,n+(n&1),end);
      if(t==='VP8X'){
        if(w||n<10||!(b[s]&2))throw new Error('cabecera WebP');
        w=u24(s+4)+1;h=u24(s+7)+1;AN_R_SIZE(w,h);
      }else if(t==='ICCP'){
        if(icc||!n||n>4194304)throw new Error('perfil WebP');
        icc=b.subarray(p,next);
      }else if(t==='ANIM'){
        if(anim||n<6||!w)throw new Error('control WebP');
        anim=true;
      }else if(t==='ANMF'){
        if(!w||!anim||n<24||frames.length>=10000)throw new Error('fotograma WebP');
        const x=u24(s)*2,y=u24(s+3)*2,fw=u24(s+6)+1,fh=u24(s+9)+1;
        AN_R_SIZE(fw,fh);if(x+fw>w||y+fh>h)throw new Error('encuadre WebP');
        let alpha=null,pixels=null,hasAlpha=false;
        for(let q=s+16;q<s+n;){
          need(q,8,s+n);const kind=tag(q),len=u32(q+4),v=q+8,after=v+len+(len&1);need(v,len+(len&1),s+n);
          if(kind==='ALPH'){
            if(alpha||pixels||!len)throw new Error('alpha WebP');
            alpha=b.subarray(q,after);hasAlpha=true;
          }else if(kind==='VP8 '||kind==='VP8L'){
            if(pixels)throw new Error('datos WebP');
            let pw,ph;
            if(kind==='VP8 '){
              if(len<10||b[v]&1||b[v+3]!==157||b[v+4]!==1||b[v+5]!==42)throw new Error('datos VP8');
              pw=(b[v+6]|b[v+7]<<8)&16383;ph=(b[v+8]|b[v+9]<<8)&16383;
            }else{
              if(alpha||len<5||b[v]!==47)throw new Error('datos VP8L');
              const bits=u32(v+1);pw=(bits&16383)+1;ph=((bits>>>14)&16383)+1;hasAlpha=!!(bits&268435456);
              if(bits>>>29)throw new Error('version VP8L');
            }
            if(pw!==fw||ph!==fh)throw new Error('dimensiones WebP');
            pixels=b.subarray(q,after);
          }
          q=after;
        }
        if(!pixels)throw new Error('fotograma WebP vacio');
        frames.push({x,y,w:fw,h:fh,dispose:!!(b[s+15]&1),replace:!!(b[s+15]&2),alpha,pixels,hasAlpha});
      }
      p=next;
    }
    if(!anim||!frames.length)throw new Error('animacion sin fotogramas');
    const blob=i=>{
      const f=frames[i],head=new Uint8Array(30),view=new DataView(head.buffer);
      head.set([82,73,70,70],0);head.set([87,69,66,80,86,80,56,88],8);view.setUint32(16,10,true);
      head[20]=(f.hasAlpha?16:0)|(icc?32:0);
      for(let j=0;j<3;j++){head[24+j]=(f.w-1)>>>(8*j);head[27+j]=(f.h-1)>>>(8*j);}
      view.setUint32(4,22+(icc?.byteLength||0)+(f.alpha?.byteLength||0)+f.pixels.byteLength,true);
      return new Blob([head,...(icc?[icc]:[]),...(f.alpha?[f.alpha]:[]),f.pixels],{type:'image/webp'});
    };
    return {w,h,frames,blob};
  }
  async function AN_R_IMAGE(blob,signal){
    const live=()=>{if(GONE||signal.aborted)throw new Error('salida');};
    live();
    if(typeof createImageBitmap==='function')try{
      const image=await createImageBitmap(blob);
      try{live();return {image,close(){image.close();}};}catch(e){image.close();throw e;}
    }catch(e){live();}
    return new Promise((resolve,reject)=>{
      const image=new Image(),url=URL.createObjectURL(blob);let done=false;
      const clean=()=>{image.onload=null;image.onerror=null;signal.removeEventListener('abort',abort);URL.revokeObjectURL(url);};
      const finish=e=>{if(done)return;done=true;clean();if(e){image.removeAttribute('src');reject(e);}else resolve({image,close(){image.removeAttribute('src');}});};
      const abort=()=>finish(new Error('salida'));
      image.onload=()=>{try{live();if(!image.naturalWidth||!image.naturalHeight)throw new Error('fotograma vacio');finish();}catch(e){finish(e);}};
      image.onerror=()=>finish(new Error('fotograma WebP'));
      signal.addEventListener('abort',abort,{once:true});
      if(signal.aborted){abort();return;}
      image.src=url;
    });
  }
  async function AN_READER(file,ty,report){
    if(GONE)throw new Error('salida');
    if(!file?.size||file.size>67108864)throw new Error('animacion demasiado grande');
    const meta=await AN_META(file,ty);
    if(GONE)throw new Error('salida');
    if(!meta.times.length||meta.times.length>10000)throw new Error('demasiados fotogramas');
    let bytes=new Uint8Array(await file.arrayBuffer()),parsed=null,decoder=null,current=null,canvas=null,ctx=null,closed=false,index=-1,q=Promise.resolve();
    const ac=new AbortController(),check=()=>{if(closed||GONE)throw new Error('salida');};
    const note=e=>{try{report?.('native:'+String(e?.message||e).replace(/\s+/g,' ').slice(0,90));}catch{}};
    const nativeClose=()=>{try{current?.close();}catch{}current=null;try{decoder?.close();}catch{}decoder=null;index=-1;};
    const close=()=>{if(closed)return;closed=true;ac.abort();nativeClose();if(canvas)canvas.width=canvas.height=1;canvas=null;ctx=null;parsed=null;bytes=null;};
    const fallback=()=>{
      check();nativeClose();
      if(ty!=='webp_anim')throw new Error('lector de animacion no disponible');
      parsed=parsed||AN_R_WEBP(bytes);
      if(parsed.frames.length!==meta.times.length)throw new Error('fotogramas incompletos');
      canvas=document.createElement('canvas');canvas.width=parsed.w;canvas.height=parsed.h;
      ctx=canvas.getContext('2d');if(!ctx)throw new Error('canvas no disponible');
    };
    try{
      check();
      if(ty==='webp_anim'){
        parsed=AN_R_WEBP(bytes);
        if(parsed.frames.length!==meta.times.length)throw new Error('fotogramas incompletos');
      }else if(ty==='gif'){
        if(bytes.length<13)throw new Error('animacion incompleta');
        AN_R_SIZE(bytes[6]|bytes[7]<<8,bytes[8]|bytes[9]<<8);
      }else throw new Error('animacion no compatible');
      if(typeof ImageDecoder!=='undefined')try{
        decoder=new ImageDecoder({data:bytes,type:ty==='gif'?'image/gif':'image/webp'});
        await decoder.tracks.ready;await decoder.completed;check();
        if(!decoder.tracks.selectedTrack||decoder.tracks.selectedTrack.frameCount!==meta.times.length)throw new Error('fotogramas incompletos');
      }catch(e){check();note(e);fallback();}
      else fallback();
      const read=async wanted=>{
        check();if(!Number.isInteger(wanted)||wanted<0||wanted>=meta.times.length)throw new Error('fotograma fuera de rango');
        if(decoder){
          if(index===wanted&&current)return current;
          try{
            try{current?.close();}catch{}current=null;
            const result=await decoder.decode({frameIndex:wanted}),image=result.image;
            try{check();AN_R_SIZE(image.displayWidth||image.codedWidth,image.displayHeight||image.codedHeight);current=image;index=wanted;return current;}
            catch(e){image.close();throw e;}
          }catch(e){check();note(e);fallback();}
        }
        if(wanted<index){ctx.clearRect(0,0,canvas.width,canvas.height);index=-1;}
        while(index<wanted){
          check();const next=index+1,f=parsed.frames[next];
          const decoded=await AN_R_IMAGE(parsed.blob(next),ac.signal);
          try{
            check();
            if(index>=0){const prev=parsed.frames[index];if(prev.dispose)ctx.clearRect(prev.x,prev.y,prev.w,prev.h);}
            if(f.replace)ctx.clearRect(f.x,f.y,f.w,f.h);
            ctx.drawImage(decoded.image,f.x,f.y,f.w,f.h);index=next;
          }finally{decoded.close();}
        }
        check();return canvas;
      };
      return {meta,get mode(){return decoder?'native':'webp';},get(wanted){const task=q.catch(()=>{}).then(()=>read(wanted));q=task.catch(()=>{});return task;},close};
    }catch(e){close();throw e;}
  }

  const FRAME_ACTIVE=new Set(),RAW_ACTIVE=new Set();
  function FRAME_OWN(p){
    const close=p.close;let closed=false,closing;
    p.close=()=>{if(closed)return closing;closed=true;FRAME_ACTIVE.delete(p);closing=close();return closing;};
    FRAME_ACTIVE.add(p);return p;
  }
  async function FRAME_GET(p,time,ff,loop=false){
    if(GONE)throw new Error('salida');
    if(!p?.get)return AN_AT(p,time,loop);
    const t=loop&&p.dur>0?((time%p.dur)+p.dur)%p.dur:Math.max(0,time);
    return p.get(t,ff);
  }
  async function AN_STREAM(b,ty,trim,lg){
    let reader=null,current=null,scaled=null,closed=false,index=-1;
    try{
      reader=await AN_READER(b,ty,lg);
      const meta=reader.meta,cut=TRIM_1({trim},meta.du),end=cut.s+cut.d;
      const times=[0,...meta.times.filter(t=>t>cut.s&&t<end).map(t=>t-cut.s)];
      if(meta.times.length<2){reader.close();return null;}
      if(GONE)throw new Error('salida');
      return FRAME_OWN({fps:AN_FPS(times,cut.d),dur:cut.d,times,
        async get(time){
          if(closed||GONE)throw new Error('salida');
          const next=AN_IDX(meta,Math.min(meta.du-1e-7,cut.s+time));
          if(next===index&&current)return current;
          const frame=await reader.get(next);
          if(closed||GONE)throw new Error('salida');
          const w=frame.displayWidth||frame.width,h=frame.displayHeight||frame.height,k=Math.min(1,THM/Math.max(w,h));
          if(k<1){
            scaled||=document.createElement('canvas');
            scaled.width=Math.max(1,Math.round(w*k));scaled.height=Math.max(1,Math.round(h*k));
            scaled.getContext('2d').drawImage(frame,0,0,scaled.width,scaled.height);current=scaled;
          }else current=frame;
          index=next;return current;
        },
        close(){closed=true;reader.close();current=null;if(scaled)scaled.width=scaled.height=1;}
      });
    }catch(e){reader?.close();if(scaled)scaled.width=scaled.height=1;if(GONE)throw e;lg?.('decode:'+DG_1(e));return null;}
  }

  async function VD_STREAM(it){
    let vm=null,current=null,closed=false,ff0=null,mounted=false;
    const root='/skvideo',name='sk-frame.png',mem=FM_MEMORY.has(it.file)&&it.file.size>0&&it.file.size<=FM_LIMIT(),mp='/sk-vin'+(/\.[a-z0-9]{1,8}$/i.exec(it.file.name||'')?.[0]||'.bin');
    if(!it.fv)try{vm=await VM_OPEN(it.file);}catch(e){if(GONE)throw e;}
    const duration=vm?.du||it.du||await VF_META(it.file);
    if(!Number.isFinite(duration)||duration<=0){vm?.close();throw new Error('duracion de video desconocida');}
    if(GONE){vm?.close();throw new Error('salida');}
    const cut=TRIM_1(it,duration);
    const p=FRAME_OWN({fps:VID_FPS,dur:cut.d,
      async get(time,ff){
        if(closed||GONE)throw new Error('salida');
        current?.close();current=null;
        const at=Math.min(duration-.001,cut.s+time);
        if(vm)try{current=await vm.bitmap(at);if(closed||GONE){current.close();current=null;throw new Error('salida');}return current;}catch(e){vm.close();vm=null;if(GONE||closed)throw e;}
                                                                          
        ff0=ff;
        if(!mounted){if(mem){await ff.writeFile(mp,new Uint8Array(await it.file.arrayBuffer()));mounted=true;if(closed||GONE){mounted=false;await ff.deleteFile(mp).catch(()=>{});throw new Error('salida');}}else{await ff.createDir(root).catch(()=>{});await ff.mount(window.FFmpegWASM.FFFSType.WORKERFS,{files:[it.file]},root);mounted=true;if(closed||GONE){mounted=false;await ff.unmount(root).catch(()=>{});throw new Error('salida');}}}
        try{
          for(const begin of new Set([Math.max(0,at-.5),0])){
            if(closed||GONE)throw new Error('salida');
            await ff.deleteFile(name).catch(()=>{});
            const filter="select='lte(t,"+(at-begin+.0001)+")',scale="+THM+':'+THM+':force_original_aspect_ratio=decrease';
            const code=await ff.exec(['-ss',String(begin),'-t',String(at-begin+.001),'-i',mem?mp:root+'/'+it.file.name,'-an','-vf',filter,'-fps_mode','passthrough','-update','1','-y',name]);
            if(code!==0)throw new Error('video '+code);
            let data;try{data=await ff.readFile(name);}catch{}
            if(data?.byteLength){current=await createImageBitmap(new Blob([data],{type:'image/png'}));break;}
          }
          if(!current)throw new Error('fotograma');
          if(closed||GONE){current.close();current=null;throw new Error('salida');}
          return current;
        }finally{await ff.deleteFile(name).catch(()=>{});}
      },
      async close(){closed=true;vm?.close();current?.close();current=null;if(mounted){mounted=false;await (mem?ff0.deleteFile(mp):ff0.unmount(root)).catch(()=>{});}}
    });
    return p;
  }
  let RAW_BLOCKED=false;
  const RAW_QUOTA=e=>e?.name==='QuotaExceededError'||/quota|exceed.*storage/i.test(String(e?.message||e));
  function RAW_ERROR(e){if(RAW_QUOTA(e))RAW_BLOCKED=true;return Object.assign(new Error(e?.message||String(e)),{rawStorage:true,name:e?.name||'Error'});}
  function RAW_BUDGET(){return (navigator.deviceMemory&&navigator.deviceMemory<=2?64:128)*1024*1024;}
  async function RAW_SINK(ff,expected,forceMemory=false){
    let dir=null,handle=null,writer=null,fileName='',mounted=false,closing=null,closed=false,count=0;
    const names=[],root='/skraw';
    const sink={mode:'memory',budget:RAW_BUDGET(),
      async write(data){
        if(closed||GONE)throw new Error('salida');
        if(writer)try{await writer.write(data);}catch(e){throw RAW_ERROR(e);}
        else{const name='i'+String(count).padStart(6,'0')+'.raw';names.push(name);await ff.writeFile(name,new Uint8Array(data.buffer,data.byteOffset,data.byteLength));if(closed||GONE){await ff.deleteFile(name).catch(()=>{});throw new Error('salida');}}
        count++;
      },
      async seal(fps,size){
        if(closed||GONE)throw new Error('salida');
        if(writer){await writer.close();writer=null;if(closed||GONE)throw new Error('salida');const file=await handle.getFile();await ff.createDir(root).catch(()=>{});await ff.mount(window.FFmpegWASM.FFFSType.WORKERFS,{files:[file]},root);mounted=true;if(closed||GONE){mounted=false;await ff.unmount(root).catch(()=>{});throw new Error('salida');}
          return ['-f','rawvideo','-framerate',String(fps),'-pixel_format','rgba','-video_size',size+'x'+size,'-i',root+'/'+file.name];}
        return ['-f','image2','-framerate',String(fps),'-pixel_format','rgba','-video_size',size+'x'+size,'-c:v','rawvideo','-i','i%06d.raw'];
      },
      close(){
        if(closing)return closing;closed=true;
        closing=(async()=>{
          if(writer){const w=writer;writer=null;await w.abort().catch(()=>{});}
          if(mounted){mounted=false;await ff.unmount(root).catch(()=>{});}
          for(const name of names)await ff.deleteFile(name).catch(()=>{});
          if(dir&&fileName)await dir.removeEntry(fileName).catch(()=>{});
          RAW_ACTIVE.delete(sink);
        })();return closing;
      }
    };
    RAW_ACTIVE.add(sink);
                                                                                  
    if(!forceMemory&&!RAW_BLOCKED&&expected>32*1024*1024&&navigator.storage?.getDirectory)try{
      const estimate=await navigator.storage.estimate?.();
      if(estimate?.quota&&estimate.quota-(estimate.usage||0)<expected*1.15)throw new Error('espacio');
      dir=await(await navigator.storage.getDirectory()).getDirectoryHandle('sk-stickers-tmp',{create:true});
                                                                                      
      for await(const [name,h] of dir.entries())if(/^sk-[a-f0-9-]+\.(?:raw|pin)$/.test(name)&&h.kind==='file'){
        try{if(Date.now()-(await h.getFile()).lastModified>86400000)await dir.removeEntry(name);}catch{}
      }
      fileName='sk-'+crypto.randomUUID()+'.raw';handle=await dir.getFileHandle(fileName,{create:true});
      writer=await handle.createWritable();
      if(closed||GONE){await writer.abort().catch(()=>{});writer=null;await dir.removeEntry(fileName).catch(()=>{});throw new Error('salida');}
      sink.mode='opfs';
    }catch(e){
      if(RAW_QUOTA(e))RAW_BLOCKED=true;
      if(writer){await writer.abort().catch(()=>{});writer=null;}
      if(dir&&fileName)await dir.removeEntry(fileName).catch(()=>{});
      dir=null;handle=null;fileName='';if(GONE){await sink.close();throw e;}
    }
    return sink;
  }
  function WB_STEPS(fps,pf){
    const L=[[fps,50],[fps,30],[Math.min(fps,12),22],[Math.min(fps,10),10],[Math.min(fps,10),1]].filter((x,j,a)=>!j||x[0]!==a[j-1][0]||x[1]!==a[j-1][1]);
    return [...L.map(x=>[...x,DIM]),...(pf.s?L.map(x=>[...x,256]):[])];
  }
  async function WB_E1(it,base,ovs,fps,onp,pf,forceMemory=false){return FF_JOB(async()=>{
    const ff=await FF_L1(),c=document.createElement('canvas');c.width=c.height=DIM;
    const ctx=c.getContext('2d',{willReadFrequently:true}),lv=$('sc-lv'),ckEl=$('sc-ck'),lctx=lv.getContext('2d');
    const baseDur=base.dur||0,overlayDur=ovs.reduce((m,o)=>Math.max(m,o.an?.dur||0),0);
    const dur=Math.min(pf.max||VID_MAX,VID_MAX,baseDur||overlayDur||1/VID_FPS);
    fps=AN_MIX_FPS(base,ovs,dur);
    let sink=null,size=DIM,op=true,lm='';
    const log=({message})=>{lm=FF_LOG_LINE(lm,message);};ff.on('log',log);
    ckEl.style.display='none';lv.style.display='block';
    try{
      sink=await RAW_SINK(ff,Math.ceil(dur*fps-1e-8)*DIM*DIM*4,forceMemory);
                                                                                    
                                                                                       
      const bounded=sink.mode==='memory'||!!navigator.deviceMemory&&navigator.deviceMemory<=2;
      if(bounded&&Math.ceil(dur*fps-1e-8)*size*size*4>sink.budget){
        size=256;fps=Math.max(1,Math.min(fps,Math.floor(sink.budget/(size*size*4*dur))));
      }
      const n=Math.min(MAXFR,Math.max(1,Math.ceil(dur*fps-1e-8)));
      if(n*size*size*4>sink.budget&&bounded)throw new Error('No hay memoria suficiente para este tramo');
      const raw=size===DIM?c:document.createElement('canvas');raw.width=raw.height=size;
      const rx=raw===c?ctx:raw.getContext('2d',{willReadFrequently:true});
      for(let i=0;i<n;i++){
        if(GONE)throw new Error('salida');
        const time=i/fps;ctx.clearRect(0,0,DIM,DIM);
        DR_B1(ctx,await FRAME_GET(base,time,ff),it.crop);
        for(const o of ovs){const img=o.an?await FRAME_GET(o.an,time,ff,true):o.img;ctx.drawImage(img,o.x-o.s/2,o.y-o.s/2,o.s,o.s);}
        if(raw!==c){rx.clearRect(0,0,size,size);rx.drawImage(c,0,0,size,size);}
        const d=rx.getImageData(0,0,size,size).data;
        if(op)for(let q=3;q<d.length;q+=4)if(d[q]<255){op=false;break;}
        try{lctx.clearRect(0,0,DIM,DIM);lctx.drawImage(c,0,0,DIM,DIM);}catch{}
        await sink.write(d);onp?.((i+1)/n*.75);
      }
      await AN_F1(base);for(const o of ovs)await AN_F1(o.an);
      let input;try{input=await sink.seal(fps,size);}catch(e){if(sink.mode==='opfs')throw RAW_ERROR(e);throw e;}
      const st=WB_STEPS(fps,pf);let out=null;
      for(let j=0;j<st.length;j++){
        if(GONE)throw new Error('salida');
        const [f,q,z]=st[j],filter='fps='+f+(z!==size?',scale='+z+':'+z:'');
        lm='';const code=await ff.exec([...input,'-t',String(dur),'-vf',filter,'-c:v',op?'libwebp':'libwebp_anim','-f','webp','-quality',String(q),'-loop','0','-y','o.webp']);
        if(code!==0)throw new Error('webp '+code+' '+lm);
        out=await ff.readFile('o.webp');onp?.(.75+.25*(j+1)/st.length);
        if(out.byteLength<=pf.t)break;
        if(out.byteLength>pf.t*2.5)while(st[j+1]&&st[j+1][0]===f&&st[j+1][2]===z)j++;
      }
      if(!out?.byteLength)throw new Error('webp vacio');
      onp?.(1);return out.byteLength<=pf.t||pf.s?new Blob([out],{type:'image/webp'}):null;
    }finally{
      ff.off('log',log);await sink?.close();await ff.deleteFile('o.webp').catch(()=>{});
      c.width=c.height=1;lv.style.display='none';ckEl.style.display='';
    }
  });}

  function AN_F1(a){
    if(!a)return;
    if(a.close)return a.close();
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
      const src=o.an?.fr?.length?AN_AT(o.an,time,true):o.img;
      try{ctx.drawImage(src,o.x-o.s/2,o.y-o.s/2,o.s,o.s);}catch{}
    });
  }

  async function OV_P1(overlays,lg){
    const out=[];
    try{for(let i=0;i<overlays.length;i++){
      if(GONE)throw new Error('salida');
      const o=overlays[i],entry={img:o.img,an:null,x:o.x,y:o.y,s:o.s,lost:false};
      const log=m=>lg?.('ov'+(i+1)+':'+m);
      if(o.blob&&o.anim){
        const an=await AN_STREAM(o.blob,o.anim,null,log);
        if(an){
          const get=an.get;
          an.get=async(time,ff)=>{
            if(entry.lost)return entry.img;
            try{return await get(time,ff);}
            catch(e){if(GONE)throw e;entry.lost=true;await AN_F1(an);log('decode:'+DG_1(e));return entry.img;}
          };
          entry.an=an;
        }else entry.lost=true;
      }
      out.push(entry);
    }
    return out;}catch(e){for(const o of out)await AN_F1(o.an);throw e;}
  }

  function FF_LOG_LINE(previous,message){
    const text=String(message||'').replace(/\s+/g,' ').trim();
    if(!text||/^(?:Aborted\(\)|Conversion failed!?|Exiting normally|Last message repeated)/i.test(text))return previous;
    const relevant=s=>/error|invalid|fail|cannot|could not|not found|unsupported|not implemented|no such|memory|unable|matches no streams|does not contain any stream|permission|not readable/i.test(s);
    const generic=s=>/marking filters|nothing was written/i.test(s),rd=s=>/not ?readable|FileReaderSync|permission/i.test(s),take=text.slice(0,180);
    if(rd(text))return take;
    if(rd(previous))return previous;
    if(relevant(previous)&&!generic(previous))return previous;
    return relevant(text)||!relevant(previous)?take:previous;
  }
  async function VD_DIRECT(it,onp,pf){
    if(!it.isVid||it.ov?.length)throw new Error('video directo no aplicable');
    if(!Number.isFinite(it.du)||it.du<=0)throw new Error('duracion de video desconocida');
    const cut=TRIM_1(it),fps=VID_FPS,st=WB_STEPS(fps,pf);cut.d=Math.min(cut.d,pf.max||VID_MAX);
    const filters=['scale='+THM+':'+THM+':force_original_aspect_ratio=decrease'],cd=it.crop;
    if(cd){
      if(![cd.x,cd.y,cd.w,cd.h,cd.sw,cd.sh].every(Number.isFinite)||cd.sw<=0||cd.sh<=0||cd.w<=0||cd.h<=0)throw new Error('recorte de video invalido');
      const x=Math.max(0,Math.min(1,cd.x/cd.sw)),y=Math.max(0,Math.min(1,cd.y/cd.sh));
      const w=Math.min(1-x,cd.w/cd.sw),h=Math.min(1-y,cd.h/cd.sh);
      if(w<=0||h<=0)throw new Error('recorte de video vacio');
      const num=n=>String(+n.toFixed(12));
      filters.push('crop=w=iw*'+num(w)+':h=ih*'+num(h)+':x=iw*'+num(x)+':y=ih*'+num(y)+':exact=1');
    }
    filters.push('scale='+DIM+':'+DIM+':flags=bilinear','setsar=1');
    return FM_1(it.file,async(ff,p)=>{
      const name='vdirect.webp';let out=null,lm='',vc='',stage=0,last=0,full=false,probing=false,firstPTS=NaN;
      const log=({message})=>{
        lm=FF_LOG_LINE(lm,message);
        if(!vc){const mv=/Stream #\d+:\d+[^:]*: Video: ([a-z0-9_]+)/i.exec(message);if(mv)vc=mv[1];}
        if(probing&&!Number.isFinite(firstPTS)){const m=/\bn:\s*0\s+pts:.*?\bpts_time:\s*([-\d.e+]+)/.exec(message);if(m)firstPTS=Number(m[1]);}
      };
      const progress=({time})=>{
        if(!onp||GONE||probing)return;
        const ratio=Math.max(0,Math.min(1,(Number(time)||0)/(cut.d*1e6)));
        last=Math.max(last,Math.min(.99,(stage+ratio)/st.length));onp(last);
      };
      ff.on('log',log);ff.on('progress',progress);
      try{
        const begin=Math.max(0,cut.s-.5),offset=cut.s-begin;
        if(begin>0){
                                                                                           
                                                                                      
          probing=true;
          try{
            const code=await ff.exec(['-loglevel','info','-ss',String(begin),'-t',String(offset+cut.d),'-i',p,'-map','0:v:0','-an','-sn','-dn','-vf','showinfo=checksum=0','-frames:v','1','-f','null','-']);
            full=code!==0||!Number.isFinite(firstPTS)||firstPTS>offset+1e-5;
          }finally{probing=false;}
        }
        for(let j=0;j<st.length;j++){
          if(GONE)throw new Error('salida');
          stage=j;const [f,q,z]=st[j];out=null;
                                                                                      
                                                                                              
          for(const begin of new Set([full?0:Math.max(0,cut.s-.5),0])){
            if(GONE)throw new Error('salida');
            const offset=cut.s-begin,vf=[...filters,'tpad=stop_mode=clone:stop_duration='+String(cut.d+offset),'setpts=PTS-'+String(offset)+'/TB','fps='+fps+':start_time=0'];
            if(f!==fps)vf.push('fps='+f);
            if(z!==DIM)vf.push('scale='+z+':'+z);
            await ff.deleteFile(name).catch(()=>{});lm='';
            const code=await ff.exec(['-ss',String(begin),'-t',String(offset+cut.d),'-i',p,'-map','0:v:0','-an','-sn','-dn','-map_metadata','-1','-t',String(cut.d),'-vf',vf.join(','),'-frames:v',String(Math.max(1,Math.ceil(cut.d*f-1e-8))),'-c:v','libwebp','-f','webp','-quality',String(q),'-loop','0','-y',name]);
            if(code!==0)throw new Error('webp directo '+code+(vc?' ['+vc+'] ':' ')+lm);
            try{const data=await ff.readFile(name);if(data.byteLength>12)out=data;}catch{}
            if(out){if(begin===0&&cut.s>.5)full=true;break;}
          }
          if(!out?.byteLength)throw new Error('webp directo vacio'+(vc?' ['+vc+'] ':' ')+lm);
          if(out.byteLength<=pf.t)break;
          if(out.byteLength>pf.t*2.5)while(st[j+1]&&st[j+1][0]===f&&st[j+1][2]===z)j++;
        }
        if(GONE)throw new Error('salida');
        if(onp)onp(1);
        return out.byteLength<=pf.t||pf.s?new Blob([out],{type:'image/webp'}):null;
      }finally{
        ff.off('log',log);ff.off('progress',progress);
        await ff.deleteFile(name).catch(()=>{});
      }
    });
  }

  const FM_MEMORY=new WeakSet();
  const FM_LIMIT=()=>Math.max(MAX_SZ,RAW_BUDGET());
  const FM_READ_ERROR=e=>e?.name==='NotReadableError'||/NotReadableError|FileReaderSync.*readAsArrayBuffer|readAsArrayBuffer.*FileReaderSync/i.test(String(e?.message||e));
  async function FM_1(f,fn){return FF_JOB(async()=>{
    const allowed=Number.isFinite(f?.size)&&f.size>0&&f.size<=FM_LIMIT();
    let memory=allowed&&FM_MEMORY.has(f);
    for(let attempt=0;attempt<2;attempt++){
      if(GONE)throw new Error('salida');
      let ff=null,mounted=false,written=false,retry=false;
      const path=memory?'/sk-input'+(/\.[a-z0-9]{1,8}$/i.exec(f.name||'')?.[0]||'.bin'):'/vc/'+f.name;
      try{
        ff=await FF_L1();
        if(memory){
          const data=new Uint8Array(await f.arrayBuffer());
          if(GONE)throw new Error('salida');
          if(data.byteLength!==f.size)throw Object.assign(new Error('Lectura incompleta del archivo'),{name:'NotReadableError'});
          written=true;await ff.writeFile(path,data);
        }else{
          await ff.createDir('/vc').catch(()=>{});
          await ff.mount(window.FFmpegWASM.FFFSType.WORKERFS,{files:[f]},'/vc');mounted=true;
        }
        if(GONE)throw new Error('salida');
        return await fn(ff,path);
      }catch(e){
        retry=!memory&&allowed&&FM_READ_ERROR(e)&&!GONE&&attempt===0;
        FF_R1();
        if(!retry)throw e;
        FM_MEMORY.add(f);memory=true;
      }finally{
        if(mounted)await ff.unmount('/vc').catch(()=>{});
        if(written)await ff.deleteFile(path).catch(()=>{});
      }
    }
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
      const files=async()=>{const entries=await ff.listDir('/');return entries.map(e=>e.name).filter(name=>/^v\d{4}\.png$/.test(name)).sort();};
      try{
        const code=await ff.exec(['-ss',String(s),'-t',String(d),'-i',p,'-an','-vf','fps='+VID_FPS+','+scale,'-frames:v',String(n),'-y','v%04d.png']);
        if(code!==0)throw new Error('video '+code);
        for(const name of await files()){
          o.push(new Blob([await ff.readFile(name)],{type:'image/png'}));
          await ff.deleteFile(name);
        }
        if(!o.length)throw new Error('video');
        return o;
      }finally{for(const name of await files().catch(()=>[]))await ff.deleteFile(name).catch(()=>{});}
    });
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
    if(!it.isAnim)return !it.trim;
    try{
      const {du}=await AN_META(it.file,it.isAnim),cut=TRIM_1(it,du);
      return du<=VID_MAX+1e-8&&cut.s<1e-6&&Math.abs(cut.d-du)<.001;
    }catch{return false;}
  }

  async function FX_1(it,ovs,pf){
    if(pf.s&&it.isWebp&&it.file.size<=pf.t&&!it.crop&&!it.ov.length&&await AN_PASS(it))return it.file;
    if(it.isAnim&&it.trim&&!it.fp)throw new Error('No se pudo recuperar el fotograma del tramo elegido');
    it.fx=1;for(const o of ovs)if(o.an)o.lost=true;
    return await ST_E1(it,ovs,pf);
  }

  function WP_M(fr,w,h){
    const L4=n=>new Uint8Array([n&255,n>>>8&255,n>>>16&255,n>>>24&255]),L3=n=>new Uint8Array([n&255,n>>>8&255,n>>>16&255]),A=s=>new Uint8Array([...s].map(c=>c.charCodeAt(0))),ch=[];
    let al=0;
    for(const f of fr){
      const d=f.b,ps=[];let p=12,n=0;
      while(p+8<=d.length){
        const t=String.fromCharCode(d[p],d[p+1],d[p+2],d[p+3]),s=(d[p+4]|d[p+5]<<8|d[p+6]<<16)>>>0;
        if(t==='ALPH'||t==='VP8 '||t==='VP8L'){const q=new Uint8Array(8+s+(s&1));q.set(d.subarray(p,Math.min(p+8+s,d.length)));ps.push(q);n+=q.length;if(t!=='VP8 ')al=1;}
        p+=8+s+(s&1);
      }
      if(!ps.length)throw new Error('webp');
      ch.push(A('ANMF'),L4(16+n),L3(0),L3(0),L3(w-1),L3(h-1),L3(f.d),new Uint8Array([2]),...ps);
    }
    const vx=new Uint8Array([2|(al?16:0),0,0,0,...L3(w-1),...L3(h-1)]);
    return new Blob([A('RIFF'),L4(ch.reduce((a,x)=>a+x.length,0)+36),A('WEBP'),A('VP8X'),L4(10),vx,A('ANIM'),L4(6),new Uint8Array(6),...ch],{type:'image/webp'});
  }
  async function NA_1(it,ovs,pf,onp){
    const base=it.isVid?await VD_STREAM(it):await AN_STREAM(it.file,it.isAnim,it.trim,null);
    if(!base)return null;
    try{
      for(const o of ovs)if(o.an&&!o.an.fr?.length)o.lost=true;
      const dur=Math.min(pf.max||VID_MAX,VID_MAX,base.dur||ovs.reduce((m,o)=>Math.max(m,o.an?.dur||0),0));
      if(!(dur>0))return null;
      const c=document.createElement('canvas');c.width=c.height=DIM;
      const x=c.getContext('2d'),n=Math.max(1,Math.min(100,Math.round(dur*10))),st=dur/n,bs=[],tb=q=>new Promise(r=>c.toBlob(r,'image/webp',q));
      for(let i=0;i<n;i++){
        if(GONE)throw new Error('salida');
        const f=await FRAME_GET(base,i*st,null);
        x.clearRect(0,0,DIM,DIM);DR_B1(x,f,it.crop);DR_O1(x,ovs,i*st);
        const b=await tb(.7);
        if(!b||b.type!=='image/webp')return null;
        bs.push(b);onp?.((i+1)/n*.7);
      }
      let best=null;
      const LV=[[1,0],[1,.5],[1,.35],[2,.4],[2,.25],[3,.25],[4,.2]];
      for(let j=0;j<LV.length;j++){
        const [k,q]=LV[j],fr=[];
        for(let i=0;i<n;i+=k){
          if(GONE)throw new Error('salida');
          let b=bs[i];
          if(q){const bm=await createImageBitmap(b);x.clearRect(0,0,DIM,DIM);x.drawImage(bm,0,0);bm.close();b=await tb(q);if(!b)return null;}
          fr.push({b:new Uint8Array(await b.arrayBuffer()),d:Math.max(20,Math.round(st*1000*k))});
        }
        best=WP_M(fr,DIM,DIM);
        onp?.(.7+(j+1)/LV.length*.3);
        if(best.size<=pf.t)return best;
      }
      return null;
    }finally{await AN_F1(base);}
  }
  async function NV_1(it,ovs,pf,onp,lg){
    try{const o=await NA_1(it,ovs,pf,onp);if(o){lg?.('nativo:animado');return o;}lg?.('nativo:sin');}
    catch(e){if(GONE)throw e;lg?.('nativo:'+DG_1(e));}
    return FX_1(it,ovs,pf);
  }

  async function EX_1(it,onp,pf=PB,lg,forceMemory=false){
    await KF_1(it);const original=it;delete original.fx;delete original.fxOv;
    const cap=Math.min(VID_MAX,pf.max||VID_MAX);
                                                                                     
    if((it.isVid||it.isAnim)&&cap<VID_MAX){const cut=TRIM_1(it);it={...it,trim:{s:cut.s,d:Math.min(cap,cut.d)}};}
    if(!it.isVid&&it.isWebp&&it.w===DIM&&it.h===DIM&&it.file.size<=(it.isAnim?pf.t:pf.st)&&!it.crop&&!it.ov.length&&await AN_PASS(it))return it.file;
    if(JL&&(it.isVid||it.isAnim)){const ov=await OV_P1(it.ov,lg);try{return await NV_1(it,ov,pf,onp,lg);}finally{if(it.fx)original.fx=it.fx;original.fxOv=ov.filter(o=>o.lost).length;for(const o of ov)await AN_F1(o.an);}}
    if(!forceMemory&&it.isVid&&!it.ov.length)try{return await VD_DIRECT(it,onp,pf);}catch(e){if(GONE)throw e;JL_1(e,1);FF_R1();lg?.('direct:'+DG_1(e)+await DG_I(it,e));}
    let base=null,ovs=[],retried=false;
    try{
      if(it.isVid)base=await VD_STREAM(it);
      else if(it.isAnim){base=await AN_STREAM(it.file,it.isAnim,it.trim,lg);if(!base){if(it.trim&&!it.fp)throw new Error('No se pudo recuperar el fotograma del tramo elegido');it.fx=1;}}
      ovs=await OV_P1(it.ov,lg);
      if(!base&&it.isAnim&&it.trim&&!ovs.some(o=>o.an))return await ST_E1(it,ovs,pf);
      if(!base&&!ovs.some(o=>o.an))return await ST_E1(it,ovs,pf);
      if(!base)base={img:it.isAnim&&it.trim&&it.fp?await IMG_U1(it.fp):await IMG_L1(it.file)};
      const fps=base.fps||ovs.find(o=>o.an)?.an.fps||VID_FPS;
      try{return await WB_E1(it,base,ovs,fps,onp,pf,forceMemory);}catch(e){
        if(GONE)throw e;
        if(e.rawStorage&&!forceMemory){await AN_F1(base);for(const o of ovs)await AN_F1(o.an);lg?.('storage:'+DG_1(e));retried=true;return await EX_1(it,onp,pf,lg,true);}
        if(it.file&&FM_READ_ERROR(e)&&!FM_MEMORY.has(it.file)&&it.file.size>0&&it.file.size<=FM_LIMIT()){FM_MEMORY.add(it.file);FF_R1();await AN_F1(base);for(const o of ovs)await AN_F1(o.an);lg?.('mem:'+DG_1(e));retried=true;return await EX_1(it,onp,pf,lg,forceMemory);}
        if(!(it.isAnim||it.isVid))throw e;JL_1(e,1);FF_R1();lg?.('v:'+DG_1(e)+await DG_I(it,e));await AN_F1(base);return await NV_1(it,ovs,pf,onp,lg);
      }
    }finally{if(!retried){if(it.fx)original.fx=it.fx;original.fxOv=ovs.filter(o=>o.lost).length;}await AN_F1(base);for(const o of ovs)await AN_F1(o.an);}
  }


  function AU_1(a){
    return FM_1(a.f,async(ff,p)=>{
      let lm='',noAudio=false;
      const lh=({message})=>{lm=FF_LOG_LINE(lm,message);if(/matches no streams|does not contain any stream/i.test(message))noAudio=true;};
      ff.on('log',lh);
      try{
        for(const rate of [48,32,24,16]){
          if(GONE)throw new Error('salida');
          lm='';noAudio=false;
          const r=await ff.exec(['-ss',String(Math.max(0,Number(a.s)||0)),'-t',String(Math.min(AU_S,Math.max(.001,Number(a.d)||AU_S))),'-i',p,'-vn','-map','0:a:0','-map_metadata','-1','-ac','1','-ar','48000','-c:a','libopus','-b:a',rate+'k','-f','ogg','-y','a.ogg']);
          const o=r===0?await ff.readFile('a.ogg'):null;
          if(!o?.byteLength)throw Object.assign(new Error('audio '+r+' '+lm),{noAudio});
          if(o.byteLength<=AU_MX)return new Blob([o],{type:'audio/ogg'});
                                                                             
        }
        throw Object.assign(new Error('audio supera '+AU_MX+' bytes'),{audioSize:true});
      }finally{ff.off('log',lh);await ff.deleteFile('a.ogg').catch(()=>{});}
    });
  }
  const OG_T=(()=>{const t=[];for(let i=0;i<256;i++){let c=i<<24;for(let k=0;k<8;k++)c=(c&0x80000000?(c<<1)^0x04c11db7:c<<1)>>>0;t[i]=c;}return t;})();
  const OG_C=u=>{let c=0;for(let i=0;i<u.length;i++)c=((c<<8)^OG_T[((c>>>24)^u[i])&255])>>>0;return c;};
  function OG_P(sr,sq,gr,ty,pks){
    const lz=[];
    for(const p of pks){let n=p.length;while(n>=255){lz.push(255);n-=255;}lz.push(n);}
    const o=new Uint8Array(27+lz.length+pks.reduce((a,p)=>a+p.length,0)),dv=new DataView(o.buffer);
    o.set([79,103,103,83,0,ty]);
    dv.setUint32(6,gr%4294967296,true);dv.setUint32(10,Math.floor(gr/4294967296),true);dv.setUint32(14,sr,true);dv.setUint32(18,sq,true);
    o[26]=lz.length;o.set(lz,27);
    let q=27+lz.length;for(const p of pks){o.set(p,q);q+=p.length;}
    dv.setUint32(22,OG_C(o),true);
    return o;
  }
  function OG_M(pk,tot){
    const sr=(Math.random()*4294967295)>>>0,h=new Uint8Array(19),t=new Uint8Array([79,112,117,115,84,97,103,115,2,0,0,0,115,107,0,0,0,0]),out=[];
    h.set([79,112,117,115,72,101,97,100,1,1]);
    new DataView(h.buffer).setUint16(10,312,true);new DataView(h.buffer).setUint32(12,48000,true);
    out.push(OG_P(sr,0,0,2,[h]),OG_P(sr,1,0,0,[t]));
    let sq=2,cur=[],sg=0,g=312,lg=0;
    for(const p of pk){
      const ns=Math.floor(p.d.length/255)+1;
      if(sg+ns>255){out.push(OG_P(sr,sq++,g,0,cur));lg=g;cur=[];sg=0;}
      cur.push(p.d);sg+=ns;g+=p.n;
    }
    out.push(OG_P(sr,sq,Math.max(lg,Math.min(g,312+tot)),4,cur));
    return new Blob(out,{type:'audio/ogg'});
  }
  async function OG_S(b){
    const OC=window.OfflineAudioContext||window.webkitOfflineAudioContext;
    if(!OC)return true;
    try{
      const ab=await b.arrayBuffer(),c=new OC(1,1,48000),x=await new Promise((ok,no)=>{const q=c.decodeAudioData(ab,ok,no);q?.catch?.(no);}),d=x.getChannelData(0);
      let m=0;for(let i=0;i<d.length;i+=3)m=Math.max(m,Math.abs(d[i]));
      return m>.003;
    }catch{return true;}
  }
  async function OG_Q(b,a){
    const u=new Uint8Array(await b.arrayBuffer()),n=u.length,dv=new DataView(u.buffer);
    if(n<64||u[0]!==79||u[1]!==103||u[2]!==103||u[3]!==83)return 0;
    const h=27+u[26];
    if(String.fromCharCode(...u.subarray(h,h+8))!=='OpusHead')return 0;
    let i=n-27;
    for(;i>=0;i--)if(u[i]===79&&u[i+1]===103&&u[i+2]===103&&u[i+3]===83){let L=27+u[i+26];for(let j=0;j<u[i+26];j++)L+=u[i+27+j];if(i+L===n)break;}
    if(i<0||!(u[i+5]&4))return 0;
    const p=u.slice(i),c=dv.getUint32(i+22,true);
    p.fill(0,22,26);
    if(OG_C(p)!==c)return 0;
    const d=(dv.getUint32(i+6,true)+dv.getUint32(i+10,true)*4294967296-dv.getUint16(h+10,true))/48000;
    const s0=Math.max(0,Number(a.s)||0),w=Math.min(AU_S,Math.max(.001,Number(a.d)||AU_S)),e=Number(a.du)>0?Math.min(w,Math.max(.05,a.du-s0)):w;
    b.dg=+d.toFixed(2);
    if(!(d>=.05)||d>e+1)return 0;
    if(d<e*.5-.2)return 1;
    return await OG_S(b)?2:1;
  }
  async function AU_N(pcm,sr){
    if(sr!==48000||typeof AudioEncoder==='undefined'||typeof AudioData==='undefined')return null;
    for(const rate of [48,32,24,16]){
      const cfg={codec:'opus',sampleRate:48000,numberOfChannels:1,bitrate:rate*1000};
      let ok=false;
      try{ok=(await AudioEncoder.isConfigSupported(cfg)).supported;}catch{}
      if(!ok)return null;
      const pk=[];let er=null;
      const en=new AudioEncoder({output:c=>{const d=new Uint8Array(c.byteLength);c.copyTo(d);pk.push({d,n:Math.round((c.duration||20000)*48/1000)});},error:e=>{er=e;}});
      try{
        en.configure(cfg);
        for(let i=0;i<pcm.length&&!er;i+=4800){
          if(GONE)throw new Error('salida');
          while(en.encodeQueueSize>16)await new Promise(r=>setTimeout(r,5));
          const ad=new AudioData({format:'s16',sampleRate:48000,numberOfFrames:Math.min(4800,pcm.length-i),numberOfChannels:1,timestamp:Math.round(i/48000*1e6),data:pcm.subarray(i,i+4800)});
          en.encode(ad);ad.close();
        }
        if(!er)await en.flush();
      }catch(e){er=er||e;}finally{try{en.close();}catch{}}
      if(GONE)return null;
      if(er||!pk.length)return null;
      const o=OG_M(pk,pcm.length);
      if(o.size<=AU_MX)return o;
    }
    return null;
  }
  async function AU_B(a,m){
    const OC=window.OfflineAudioContext||window.webkitOfflineAudioContext;
    if(!OC||!a?.f||a.f.size>64*1024*1024||Number(a.du)>240)return null;
    const key=(Number(a.s)||0)+'|'+(Number(a.d)||0);
    if(a.pc?.k!==key){
      let buf;
      try{
        const ab=await a.f.arrayBuffer(),ctx=new OC(1,1,48000);
        buf=await new Promise((ok,no)=>{const q=ctx.decodeAudioData(ab,ok,no);q?.catch?.(no);});
      }catch{return null;}
      if(GONE)return null;
      const sr=buf.sampleRate,s0=Math.max(0,Math.floor((Number(a.s)||0)*sr)),n=Math.min(buf.length-s0,Math.floor(Math.min(AU_S,Math.max(.001,Number(a.d)||AU_S))*sr));
      if(n<=0)return null;
      const chs=buf.numberOfChannels,data=[],pcm=new Int16Array(n);
      for(let c=0;c<chs;c++)data.push(buf.getChannelData(c));
      for(let i=0;i<n;i++){let v=0;for(let c=0;c<chs;c++)v+=data[c][s0+i];pcm[i]=Math.max(-32768,Math.min(32767,Math.round(v/chs*32767)));}
      a.pc={k:key,pcm,sr};
    }
    const {pcm,sr}=a.pc;
    if(m)return AU_N(pcm,sr);
    return FF_JOB(async()=>{
      const ff=await FF_L1();
      try{
        await ff.writeFile('a.pcm',new Uint8Array(pcm.buffer,pcm.byteOffset,pcm.byteLength));
        for(const rate of [48,32,24,16]){
          if(GONE)throw new Error('salida');
          const r=await ff.exec(['-f','s16le','-ar',String(sr),'-ac','1','-i','a.pcm','-map_metadata','-1','-ar','48000','-c:a','libopus','-b:a',rate+'k','-f','ogg','-y','a.ogg']);
          const o=r===0?await ff.readFile('a.ogg'):null;
          if(!o?.byteLength)return null;
          if(o.byteLength<=AU_MX)return new Blob([o],{type:'audio/ogg'});
        }
        return null;
      }finally{await ff.deleteFile('a.pcm').catch(()=>{});await ff.deleteFile('a.ogg').catch(()=>{});}
    });
  }
  async function AU_2(a,lg){
    delete a.noTrack;let soft=null;
    const ck=async(o,t)=>{
      if(!o||GONE)return null;
      const v=await OG_Q(o,a);
      if(v===2){lg?.('au:'+o.size+'b/'+o.dg+'s');return o;}
      lg?.(t+':'+(v?'dudoso':'invalido')+' '+o.size+'b');
      if(v&&!soft)soft=o;
      return null;
    };
    for(let k=1;k<3&&!JA&&!soft;k++){
      try{const o=await ck(await AU_1(a),'a'+k);if(o){if(k>1)lg?.('audio:recuperado');return o;}}
      catch(e){
        if(GONE)return null;
        if(e?.noAudio){a.noTrack=true;if(k>1)lg?.('audio:sin pista');return null;}
        lg?.('a'+k+':'+DG_1(e));
        if(e?.audioSize){lg?.('audio:omitido');return null;}
        JL_1(e);
      }
      FF_R1();
    }
    for(const m of JA?[1]:[1,0]){
      if(soft&&m===0)break;
      try{const o=await ck(await AU_B(a,m),m?'an':'ab');if(o){lg?.(m?'audio:nativo':'audio:navegador');return o;}}
      catch(e){if(GONE)return null;lg?.((m?'an:':'ab:')+DG_1(e));JL_1(e);}
    }
    if(soft){lg?.('audio:dudoso');return soft;}
    lg?.('audio:omitido');return null;
  }
  async function DG_I(it,e){
    if(!it?.file||!FM_READ_ERROR(e))return '';
    let q='ok';try{await it.file.slice(0,1).arrayBuffer();}catch{q='fail';}
    return ' '+(it.file.size/1048576).toFixed(1)+'MB '+(it.file.type||'?')+' '+Math.round((Date.now()-(it.t0||Date.now()))/1000)+'s '+(it.pin?(it.pin.m?'m':it.pin.n?'o':'p0'):'p0')+' main='+q;
  }
  const DG_1=e=>{
    let text=String(e?.message||e).replace(/\s+/g,' ');
    if(FM_READ_ERROR(e))text='lectura';
    else if(RAW_QUOTA(e))text='cuota: '+text;
    else if(/out of bounds memory access|memory access out of bounds/i.test(text))text='wasm: '+text;
    return text.slice(0,140)+(document.hidden?' [oculta]':'');
  };

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
    const fits=async(b,k)=>!!b&&!!k&&k.w===DIM&&k.h===DIM&&b.size<=(k.a?LA:LS)&&(!k.a||await AN_META(b,'webp_anim').then(m=>m.du<=PA.max+1e-8).catch(()=>false));
    items.forEach(it=>{delete it.fx;delete it.fxOv;});
    for(let i=0;i<items.length;i++){
      const it=items[i];setProg(Math.round(i/items.length*80),'Preparando...');
      let b=it.o,k=b?await WI_1(b):null;
      if(!await fits(b,k)){try{b=await EX_1(it,p=>setProg(Math.round((i+p)/items.length*80)),PA);}catch{b=null;}k=b?await WI_1(b):null;}
      if(await fits(b,k))o.push({b,a:k.a});
    }
    if(GONE)return;
    if(o.some(x=>x.a)&&o.some(x=>!x.a))for(const x of o)if(!x.a){x.b=await D2_1(x.b).catch(()=>null);x.a=true;}
    const z=o.filter(x=>x.b).map((x,i)=>({n:(x.a?'animados/':'estaticos/')+N3(i+1)+'.webp',b:x.b}));
    if(z.length<3){ER_D1('La app Che😻Agana necesita al menos 3 stickers compatibles');return;}
    WV_1(await ZP_1(z),items.length-z.length,items.filter(it=>it.fx).length,items.reduce((n,it)=>n+(it.fxOv||0),0));
  }
  async function WV_1(zb,om,fx,fxOv=0){
    const b64=await new Promise((ok,no)=>{const r=new FileReader();r.onload=()=>ok(String(r.result).split(',')[1]);r.onerror=no;r.readAsDataURL(zb);});
    if(GONE)return;
    const t=$('SK_AT');
    APD.querySelector('.SK_DF').hidden=true;$('SK_AM').hidden=true;
    $('SK_AX').hidden=!om&&!fx&&!fxOv;$('SK_AX').textContent=[om?om+' no entran en el pack':'',fx?fx+' salieron fijos':'',fxOv?fxOv+' capas perdieron la animacion':''].filter(Boolean).join('\n');
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
  const SEND_REC=$('SK_SEND_REC'),SEND_MSG=$('SK_SEND_MSG'),SEND_RETRY=$('SK_SEND_RETRY'),SEND_CANCEL=$('SK_SEND_CANCEL');
  function SEND_CLEAR_UI(){PD.classList.remove('SK_RETRY');SEND_REC.hidden=true;SEND_MSG.textContent='';}
  function SEND_DROP(op=SEND_OP){
    if(!op)return;const own=SEND_OP===op;if(own)SEND_OP=null;
    const wake=op.wait;op.wait=null;op.form=null;op.items=[];wake?.(false);
    if(own&&!GONE)SEND_CLEAR_UI();
  }
  function SEND_WAIT(op,error){
    if(GONE||SEND_OP!==op)return Promise.resolve(false);
    PD.classList.add('SK_RETRY');SEND_REC.hidden=false;
    setProg(85,'El paquete esta preparado');SEND_MSG.textContent=error.message+' Tus archivos siguen en el pack.';
    return new Promise(resolve=>{op.wait=resolve;});
  }
  function SEND_RESUME(retry){const op=SEND_OP;if(!op?.wait)return;const wake=op.wait;op.wait=null;SEND_CLEAR_UI();wake(retry);}
  SEND_RETRY.onclick=()=>SEND_RESUME(true);SEND_CANCEL.onclick=()=>SEND_RESUME(false);
  async function SEND_TRY(op){
    if(GONE||SEND_OP!==op)throw SE_1('cancel','');
    return SEND_POST(op.form,{},op);
  }
  function PD_O(l){SEND_CLEAR_UI();setProg(0,l);if(!PD.open)PD.showModal();document.body.style.overflow='hidden';}
  function PD_C(){SEND_CLEAR_UI();if(PD.open)PD.close();document.body.style.overflow='';}
  PD.addEventListener('cancel',e=>{e.preventDefault();if(SEND_OP?.wait)SEND_RESUME(false);});

  $('sk-cf').onclick=async()=>{
    if(!P.length||PD.open||DG.open||SEND_OP||IMP_PENDING||KF_TASK.size||ED_W)return;
    SN_P();
    const items=[...P];
    PD_O('Procesando...');
    KH_1(items);
    let nA=0,nF=0,nX=0,nXO=0;
    if(MA){if(!window.__CS){PD_C();SA_1('Abri esta pagina desde la app Che😻Agana para cargar los stickers a WhatsApp.');return;}try{await AP_1(items);}catch(e){ER_D1('Error Stickers '+e.message);}finally{if(!GONE)PD_C();}return;}
    const op={items,form:null,wait:null};SEND_OP=op;let form=null;
    try{
      if(!await DS_1()){if(!GONE)SA_1();return;}
      if(GONE||SEND_OP!==op)return;
      form=new FormData();const urls=[],dg=[],ab=[];op.form=form;
      if(MU)for(let i=0;i<items.length;i++){
        if(GONE||SEND_OP!==op)return;
        const it=items[i];if(it.au&&(it.file||ID_OK)){ab[i]=await AU_2(it.au,s=>dg.push(N3(i+1)+s));if(!ab[i]&&!(it.au.v&&it.au.noTrack))nA++;}
      }
      for(let i=0;i<items.length;i++){
        if(GONE||SEND_OP!==op)return;
        const it=items[i],n=N3(i+1),b0=Math.round(i/items.length*80),b1=Math.round((i+1)/items.length*80);
        const lb='Procesando '+(i+1)+'/'+items.length;setProg(b0,lb);
        delete it.o;
        if(!ID_OK&&it.u&&!it.trim&&(!it.file||it.isAnim&&!it.crop&&!it.ov.length)){urls.push([i+1,it.u]);if(ab[i])form.append('files',ab[i],n+'.ogg');continue;}
        delete it.fx;delete it.fxOv;const diagStart=dg.length;
        try{const output=await EX_1(it,p=>{if(!GONE&&SEND_OP===op)setProg(Math.round(b0+(b1-b0)*p),lb);},PB,s=>dg.push(n+s));if(GONE||SEND_OP!==op)return;form.append('files',output,n+'.webp');}catch(e){if(GONE||SEND_OP!==op)return;nF++;dg.push(n+'x:'+DG_1(e));continue;}
        if(it.fx)nX++;nXO+=it.fxOv||0;
        if(dg.length>diagStart)dg.push(n+'ok:'+(it.fx?'fijo':it.isAnim||it.isVid||it.ov.some(o=>o.anim)&&!it.fxOv?'animado':'imagen')+(it.fxOv?';capas_fijas='+it.fxOv:''));
        if(ab[i])form.append('files',ab[i],n+'.ogg');
      }
      ab.length=0;
      if(GONE||SEND_OP!==op)return;
      if(nF===items.length)throw new Error('conversion');
      if(urls.length)form.append('urls',JSON.stringify(urls));
      if(dg.length)form.append('dg',(navigator.deviceMemory||'?')+'GB '+(navigator.hardwareConcurrency||'?')+'n preparados='+String(items.length-nF)+'/'+items.length+' sin_audio='+nA+' fijos='+nX+' capas_fijas='+nXO+' | '+dg.join(' | '));
      let jr=await SEND_TRY(op);if(GONE||SEND_OP!==op)return;
      op.form=null;form=null;
      const {sid,w}=jr||{};
      if(!SD_RX.test(sid||''))throw SE_1('response','El servidor respondio sin un identificador valido. No se reenvio automaticamente.');
      if(!w)jr=RS_1(jr);
      items.forEach(FR_1);P=P.filter(it=>!items.includes(it));UP_1();
      if(w){PD_C();try{jr=RS_1(await WT_1(sid,w,$('SK_WT')));}finally{if(!GONE){$('SK_WT').hidden=true;TR_R();}}}
      if(GONE)return;
      OK_1(jr);
      if(nF)ER_D1(nF+' no se pudieron convertir');
      if(nA)ER_D1(nA+' sin sonido'+(JA?JH_T:''));
      if(nX)ER_D1(nX+' salieron fijos'+(JL?JH_T:''));
      if(nXO)ER_D1(nXO+' capas perdieron la animacion');
    }catch(e){if(GONE||e.sendCode==='cancel')return;if(SEND_REMOTE(e)){PD_C();SA_1();}else ER_D1(ER_1(e)||(e.message==='conversion'?'No se pudieron convertir los archivos. Tu pack se conserva.':'No se pudo completar el envio. Tu pack se conserva.'));}
    finally{form=null;SEND_DROP(op);if(!GONE)PD_C();}
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
      let jr=await SEND_POST(JSON.stringify({pack}),{'Content-Type':'application/json'});const {sid,w}=jr||{};
      if(!SD_RX.test(sid||''))throw SE_1('response','');
      if(w){W.hidden=true;jr=await WT_1(sid,w,L);}
      else await new Promise((ok,no)=>{const t0=Date.now(),iv=setInterval(()=>{
        if(GONE){clearInterval(iv);no(new Error('salida'));return;}
        const e=(Date.now()-t0)/1000;
        if(e>=TG_W){clearInterval(iv);ok();return;}
        L.textContent='Preparando el pack... '+Math.ceil(TG_W-e)+'s';B.style.width=Math.round(100*e/TG_W)+'%';
      },500);});
      L.textContent='';W.hidden=true;
      OK_1(RS_1(jr));
    }catch(e){L.textContent='';W.hidden=true;if(GONE||e.sendCode==='cancel')return;if(SEND_REMOTE(e))SA_1();else ER_D1(ER_1(e)||'Error Telegram '+e.message);}
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
    GONE=true;FRAME_ACTIVE.forEach(p=>{Promise.resolve(p.close()).catch(()=>{});});RAW_ACTIVE.forEach(s=>{s.close().catch(()=>{});});IMP_STOP();SEND_NET.forEach(ac=>ac.abort());SEND_DROP();VMS.forEach(v=>v.close());
    KQ?.ac.abort();KL_LIFE.abort();KL_NET.forEach(ac=>ac.abort());KQ=null;R=[];RF=[];PS=[];
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