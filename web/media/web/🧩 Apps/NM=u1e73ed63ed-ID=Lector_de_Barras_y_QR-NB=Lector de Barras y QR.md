<div class="QR_W1">
<style>
.QR_W1{text-align:center}
.QR_I1{font-size:2.6rem;line-height:1.2}
.qr-st{min-height:1.4em;margin:4px 0 20px;font:700 1.35rem/1.3 var(--font-h);color:var(--RD_F);transition:color .2s}
.qr-st.act{color:var(--RD_MF)}
.qr-st.ok{color:var(--ok)}
.qr-ac{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:14px 0}
.qr-area{max-width:360px;margin:0 auto;border:1px solid var(--RD_L);border-radius:16px;overflow:hidden;background:var(--RD_M)}
#qr-reader{position:relative;aspect-ratio:1}
#qr-reader video{display:block;width:100%!important;height:100%;object-fit:cover}
#qr-reader img{display:none!important}
.QS_G1{position:absolute;inset:12%;pointer-events:none;--c:rgba(255,255,255,.9);--l:26px;--w:4px;background:linear-gradient(var(--c) 0 0) 0 0/var(--l) var(--w),linear-gradient(var(--c) 0 0) 0 0/var(--w) var(--l),linear-gradient(var(--c) 0 0) 100% 0/var(--l) var(--w),linear-gradient(var(--c) 0 0) 100% 0/var(--w) var(--l),linear-gradient(var(--c) 0 0) 0 100%/var(--l) var(--w),linear-gradient(var(--c) 0 0) 0 100%/var(--w) var(--l),linear-gradient(var(--c) 0 0) 100% 100%/var(--l) var(--w),linear-gradient(var(--c) 0 0) 100% 100%/var(--w) var(--l);background-repeat:no-repeat}
.qr-rt{max-width:560px;max-height:200px;margin:0 auto;overflow-y:auto;text-align:left;word-break:break-all}
.qr-dt{margin:8px 0 0;color:var(--RD_MF);font-size:.8rem}
.qr-tk{position:fixed;bottom:24px;left:50%;z-index:999;padding:10px 20px;border:1px solid var(--RD_L);border-radius:12px;background:var(--rdm-bg);color:var(--RD_F);font-size:.9rem;white-space:nowrap;box-shadow:var(--RD_SH);opacity:0;pointer-events:none;translate:-50% 20px;transition:opacity .25s,translate .25s}
.qr-tk.show{opacity:1;translate:-50% 0}
#qr-cif{margin:0 44px 12px 0;padding-top:6px;text-align:left}
.qr-cw img{display:block;max-width:100%;max-height:60vh;margin:0 auto}
.QG_L1{display:flex;flex-direction:column;gap:16px;text-align:left}
.QG_V1{display:contents}
.qg-wr{position:sticky;top:8px;z-index:2;container-type:inline-size scroll-state;pointer-events:none}
.QG_F1{position:relative;width:min(300px,66vw);margin:0 auto;border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.45);transform-origin:0 0;transition:transform var(--GL_T)}
@container scroll-state(stuck:top){.QG_F1{transform:translateX(calc((min(300px,66vw) - 100cqw)/2)) scale(.34)}}
@supports not (container-type:scroll-state){.qg-wr{position:static}}
.qg-cv{display:block;width:100%;height:auto;border-radius:14px;background:#fff}
.qg-ov{position:absolute;inset:0;width:100%;height:100%;border-radius:14px;pointer-events:none}
.QG_O1{order:1;margin:0}
.QG_C1 .qr-ac{justify-content:flex-start}
.QG_LB{display:block;margin:0 0 6px;color:var(--RD_F2);font-size:.88rem}
#qg-t{width:100%}
.qg-dg{padding:10px 14px;border:1px solid var(--RD_L);border-radius:12px;color:var(--RD_F2);font-size:.82rem;line-height:1.55;white-space:pre-line;overflow-wrap:anywhere}
.qg-dg:empty{display:none}
.qg-row{display:grid;grid-template-columns:6.5em minmax(0,1fr) 3.2em;align-items:center;gap:2px 10px;margin:14px 0 0}
.qg-row label{color:var(--RD_F2);font-size:.88rem}
.qg-row :is(input,select){width:100%}
.qg-row select{grid-column:2/-1}
.qg-row span{color:var(--RD_MF);font-size:.82rem;text-align:right;font-variant-numeric:tabular-nums}
.qg-row small{grid-column:1/-1;color:var(--RD_MF);font-size:.78rem;line-height:1.4}
#qg:not(.QG_HI) .QG_IM{display:none}
@media(min-width:760px){
.QG_L1{display:grid;grid-template-columns:minmax(0,320px) minmax(0,1fr);gap:28px;align-items:start}
.QG_V1{display:flex;flex-direction:column;gap:14px;position:sticky;top:16px}
.qg-wr{position:relative;top:auto}
.QG_F1{width:100%;box-shadow:none}
}
</style>
<div class="QR_I1" aria-hidden="true">🔍</div>
<div class="qr-st" id="qr-st" role="status">Lector QR</div>
<div id="qr-idle">
<div class="BOTON-M1">
<button class="BOTON-M2" id="qr-cb" title="Camara"><div class="BOTON-M3"><div class="BOTON-M4">📷</div><p class="BOTON-M5">Camara</p></div></button>
<button class="BOTON-M2" id="qr-fb" title="Subir"><div class="BOTON-M3"><div class="BOTON-M4">📤</div><p class="BOTON-M5">Subir</p></div></button>
<button class="BOTON-M2" id="qg-ab" title="Crear"><div class="BOTON-M3"><div class="BOTON-M4">✨</div><p class="BOTON-M5">Crear</p></div></button>
</div>
<input type="file" id="qr-in" accept="image/*" hidden>
</div>
<div id="qr-sa" style="display:none">
<div class="qr-area"><div id="qr-reader"></div></div>
<div class="qr-ac"><button id="qr-cc">Cancelar</button></div>
</div>
<div id="qr-ra" style="display:none">
<code class="qr-rt" id="qr-rt"></code>
<div class="qr-dt" id="qr-dt"></div>
<div class="qr-ac">
<a class="RD_B1" id="qr-rl" href="#" target="_blank" rel="noopener noreferrer" style="display:none">🔗 Abrir enlace</a>
<button id="qr-cp">📋 Copiar</button>
<button id="qr-ns">🔄 Nuevo</button>
</div>
</div>
<div id="qg" class="QG_L1" style="display:none">
<button class="_nb l" id="qg-bk" aria-label="Volver" title="Volver">🔙</button>
<div class="QG_V1">
<div class="qg-wr"><div class="QG_F1"><canvas class="qg-cv" id="qg-cv" width="320" height="320"></canvas><canvas class="qg-ov" id="qg-ov"></canvas></div></div>
<div class="qr-ac QG_O1">
<button id="qg-pn">⬇️ PNG</button>
<button id="qg-sv">⬇️ SVG</button>
<button id="qg-mv" style="display:none">⬇️ MP4</button>
<button id="qg-gf" style="display:none">⬇️ GIF</button>
</div>
</div>
<div class="QG_C1">
<label class="QG_LB" for="qg-t">Texto o enlace</label>
<input id="qg-t" type="text" placeholder="https://..." autocomplete="off">
<div class="qg-row"><label for="qg-k">Tipo</label><select id="qg-k"><option value="qr">QR (lo lee cualquier camara)</option><option value="az">Aztec (mas correccion)</option></select></div>
<div class="qr-ac">
<button id="qg-ib">🖼 Imagen o video</button>
<button id="qg-rb" style="display:none">🗑 Quitar</button>
<button id="qg-tb">🔍 Probar escaneo</button>
<button id="qg-mp" style="display:none">🗺 Mapa</button>
</div>
<div class="qg-dg" id="qg-dg"></div>
<input type="file" id="qg-if" accept="image/*,video/*" hidden>
<details>
<summary>🔳 Codigo</summary>
<div id="qg-gq">
<div class="qg-row"><label for="qg-v">Densidad</label><select id="qg-v"><option value="0">Automatica</option><option value="5">v5 chico</option><option value="7">v7</option><option value="10">v10</option><option value="14">v14</option><option value="18">v18 denso</option></select><small>Mayor = mas espacio para que se note la imagen, pero mas dificil de escanear con camaras simples. Automatica elige el minimo necesario para el texto</small></div>
<div class="qg-row"><label for="qg-e">Correccion</label><select id="qg-e"><option value="H">Alta (30%)</option><option value="Q">Media (25%)</option><option value="M">Baja (15%)</option><option value="L">Minima (7%)</option></select><small>Mayor = el QR sigue leyendose aunque este sucio o tapado, pero ocupa mas espacio</small></div>
</div>
<div id="qg-ga" style="display:none">
<div class="qg-row"><small>Aztec: el nucleo central (diana) siempre queda solido y sin margen. La camara nativa del iPhone no lo lee, hace falta una app lectora</small></div>
<div class="qg-row"><label for="qg-ae">Correccion</label><input type="range" id="qg-ae" min="10" max="95" value="50"><span id="qg-ae-l">50%</span><small>Parte del simbolo reservada a correccion. Llega a 95% (repara casi la mitad). Mas = simbolo mas grande, con mas modulos para la imagen</small></div>
<div class="qg-row"><label for="qg-af">Forma</label><select id="qg-af"><option value="">Automatica</option><option value="compact">Compacto</option><option value="full">Completo</option></select><small>Compacto es mas chico pero admite pocos datos. Completo agrega la grilla de referencia</small></div>
</div>
<div class="qg-row"><label for="qg-qz">Margen</label><input type="range" id="qg-qz" min="0" max="4" value="1"><span id="qg-qz-l">1</span><small>Borde blanco alrededor, en bloques. Menor = imagen mas aprovechada. El estandar pide 4: con 0 o 1 puede fallar si se pega sobre un fondo oscuro o con dibujo</small></div>
<div class="qg-row"><label for="qg-sh">Forma</label><select id="qg-sh"><option value="ci">Circulo</option><option value="rd">Redondeado</option><option value="sq">Cuadrado</option><option value="ht">Halftone</option></select><small>Cuadrado es lo mas parecido a un QR normal, mas facil de leer para camaras viejas. Halftone: la imagen cubre todo el QR y solo el centro de cada bloque lleva el dato (Fantasma = cuanto manda la imagen)</small></div>
<div class="qg-row"><label for="qg-px">Salida</label><select id="qg-px"><option value="512">512 px</option><option value="1024" selected>1024 px</option><option value="2048">2048 px</option></select><small>Mayor = mas resolucion en el archivo final, mas pesado</small></div>
</details>
<details class="QG_IM">
<summary>🎨 Puntos y color</summary>
<div class="qg-row"><label for="qg-mn">Punto min</label><input type="range" id="qg-mn" min="10" max="80" value="35"><span id="qg-mn-l">35%</span><small>Mayor = los puntos claros de la imagen se ven mas grandes</small></div>
<div class="qg-row"><label for="qg-mx">Punto max</label><input type="range" id="qg-mx" min="60" max="110" value="100"><span id="qg-mx-l">100%</span><small>Mayor = los puntos oscuros se agrandan y pueden tocar al vecino, complicando la lectura</small></div>
<div class="qg-row"><label for="qg-gh">Fantasma</label><input type="range" id="qg-gh" min="0" max="100" value="70"><span id="qg-gh-l">70%</span><small>Mayor = se ve mas imagen de fondo entre los bloques del QR</small></div>
<div class="qg-row"><label for="qg-th">Umbral</label><input type="range" id="qg-th" min="0" max="90" value="15"><span id="qg-th-l">15%</span><small>Menor = mas partes de la imagen se unen entre bloques. Mayor = deja mas huecos en blanco</small></div>
<div class="qg-row"><label for="qg-tm">Zona calibracion</label><select id="qg-tm"><option value="0">Proteger (recomendado)</option><option value="1">Tambien pintar</option></select><small>La cruz (QR) o la grilla (Aztec) que usa la camara para medir se deja en blanco por seguridad. Tambien pintar mete imagen ahi, se ve mas completo pero con mas riesgo de fallar la lectura</small></div>
<div class="qg-row"><label for="qg-sa">Saturacion</label><input type="range" id="qg-sa" min="0" max="100" value="40"><span id="qg-sa-l">40%</span><small>Mayor = colores mas intensos y vivos</small></div>
<div class="qg-row"><label for="qg-co">Color</label><select id="qg-co"><option value="1">De la imagen</option><option value="0">Monocromo</option></select><small>Monocromo ignora los colores de la imagen, solo usa negro</small></div>
<div class="qg-row"><label for="qg-sd">Detalle img</label><input type="range" id="qg-sd" min="1" max="4" value="1"><span id="qg-sd-l">1x</span><small>Mayor = se nota mas la imagen dentro de cada bloque, sin agrandar el QR</small></div>
</details>
<details class="QG_IM">
<summary>🖼 Ajustar imagen</summary>
<div class="qg-row"><label for="qg-ix">Posicion X</label><input type="range" id="qg-ix" min="-100" max="100" value="0"><span id="qg-ix-l">0%</span><small>Mueve la imagen a la izquierda o derecha</small></div>
<div class="qg-row"><label for="qg-iy">Posicion Y</label><input type="range" id="qg-iy" min="-100" max="100" value="0"><span id="qg-iy-l">0%</span><small>Mueve la imagen hacia arriba o abajo</small></div>
<div class="qg-row"><label for="qg-iz">Zoom</label><input type="range" id="qg-iz" min="20" max="300" value="100"><span id="qg-iz-l">100%</span><small>Mayor = acerca la imagen (se ve mas grande y recortada)</small></div>
<div class="qg-row"><label for="qg-ir">Giro</label><input type="range" id="qg-ir" min="0" max="359" value="0"><span id="qg-ir-l">0°</span><small>Rota la imagen dentro del QR (el QR en si nunca gira)</small></div>
<div class="qg-row"><label for="qg-iw">Ancho img</label><input type="range" id="qg-iw" min="20" max="300" value="100"><span id="qg-iw-l">100%</span><small>Estira o achica la imagen solo a lo ancho</small></div>
<div class="qg-row"><label for="qg-ih">Alto img</label><input type="range" id="qg-ih" min="20" max="300" value="100"><span id="qg-ih-l">100%</span><small>Estira o achica la imagen solo a lo alto</small></div>
<div class="qr-ac"><button id="qg-irs">↺ Reiniciar posicion</button></div>
</details>
</div>
</div>
<dialog class="DX1" id="qr-cm">
<button data-x="1" id="qr-ccl" aria-label="Cerrar">✕</button>
<div class="qr-dt" id="qr-cif"></div>
<div class="qr-cw"><img id="qr-ci" src="" alt=""></div>
<div class="qr-ac"><button id="qr-cok">✂️ Recortar</button><button id="qr-csk">↩ Sin recorte</button></div>
</dialog>
<div class="qr-tk" id="qr-tk"></div>

<script>
(function(){
  const ZXW='https://cdn.jsdelivr.net/npm/zxing-wasm@3.1.7/dist/iife/reader/index.js';
  const CJS='web/js/lib/Cropper/cropper.min.js',CJF='https://cdn.jsdelivr.net/npm/cropperjs@1/dist/cropper.min.js';
  const CCS='web/js/lib/Cropper/cropper.min.css',CCF='https://cdn.jsdelivr.net/npm/cropperjs@1/dist/cropper.min.css';
  const QGL='https://cdn.jsdelivr.net/npm/qrcode-generator@2.0.4/dist/qrcode.js';
  const QGU='https://cdn.jsdelivr.net/npm/qrcode-generator@2.0.4/dist/qrcode_UTF8.js';
  const BWL='https://cdn.jsdelivr.net/npm/bwip-js@4.11.4/dist/bwip-js-min.js';
  const MBL='https://cdn.jsdelivr.net/npm/mediabunny@1.66.3/dist/bundles/mediabunny.min.mjs';
  const GFL='https://cdn.jsdelivr.net/npm/gifenc@1.0.3/dist/gifenc.esm.js';
  const QG_HOME='https://cheagana.com',QG_AU='cheagana.com';

  let _cam=null,_cp=null,_pf=null,_res='',_tt=null,_blobUrl=null;
  let QG_I=null,QG_IU=null,QG_TO=null,QG_M=null,QG_PD=null,QG_K=0,QG_VF=null,QG_VC=null,QG_CT=null,QG_AD=null;
  const _ld={};

  const $=id=>document.getElementById(id);
  const st=$('qr-st'),sa=$('qr-sa'),ra=$('qr-ra'),idle=$('qr-idle');
  const rt=$('qr-rt'),rl=$('qr-rl'),dt=$('qr-dt'),cb=$('qr-cb'),fb=$('qr-fb');
  const inEl=$('qr-in'),cm=$('qr-cm'),ci=$('qr-ci'),cif=$('qr-cif'),tk=$('qr-tk');
  const qg=$('qg'),qgc=$('qg-cv'),qgo=$('qg-ov'),dg=$('qg-dg'),mp=$('qg-mp');

  function QS_T(m){tk.textContent=m;tk.classList.add('show');clearTimeout(_tt);_tt=setTimeout(()=>tk.classList.remove('show'),2500);}

  function QS_SZ(raw){
    const t=raw.trim();
    try{const u=new URL(t);if(u.protocol==='http:'||u.protocol==='https:')return{text:t,url:u.href};}catch{}
    return{text:t,url:null};
  }

  function QS_ST(txt,mod){
    st.textContent=txt;
    st.className='qr-st'+(mod?' '+mod:'');
  }

  function QS_XI(r){try{return JSON.parse(r.extra||'{}');}catch{return{};}}

  function QS_DT(r){
    const u=QS_XI(r).UEC,p=[r.format];
    if(r.ecLevel)p.push('EC '+r.ecLevel);
    if(r.version)p.push('v'+r.version);
    if(typeof u==='number')p.push('EC libre '+Math.round(u*100)+'%');
    if(r.isInverted)p.push('invertido');
    if(r.isMirrored)p.push('espejo');
    return p.join('  ');
  }

  function QS_SR(r){
    const{text,url}=QS_SZ(r.text);
    _res=text;
    idle.style.display='none';sa.style.display='none';ra.style.display='';
    rt.textContent=text;dt.textContent=QS_DT(r);
    if(url){rl.href=url;rl.style.display='';}
    else{rl.style.display='none';rl.removeAttribute('href');}
    QS_ST('Resultado','ok');
    cb.disabled=false;fb.disabled=false;
  }

  function QS_LS(url){
    return _ld[url]||(_ld[url]=new Promise((res,rej)=>{
      const s=document.createElement('script');s.src=url;s.onload=res;
      s.onerror=()=>{delete _ld[url];s.remove();rej(new Error('carga'));};
      document.head.appendChild(s);
    }));
  }

  async function QS_LC(){
    if(window.Cropper)return;
    const l=document.createElement('link');l.rel='stylesheet';l.href=CCS;l.onerror=()=>{l.onerror=null;l.href=CCF;};document.head.appendChild(l);
    await QS_LS(CJS).catch(()=>QS_LS(CJF));
  }

  async function QS_LZ(){if(!window.ZXingWASM)await QS_LS(ZXW);}

  async function QS_DC(inp,fast){
    await QS_LZ();
    const r=await ZXingWASM.readBarcodes(inp,{tryHarder:!fast,tryDenoise:!fast,maxNumberOfSymbols:1});
    return r.find(v=>v.isValid)||null;
  }

  function QS_KK(){
    if(!_cam)return;
    _cam.on=false;clearTimeout(_cam.t);
    _cam.s.getTracks().forEach(t=>t.stop());_cam.v.remove();_cam=null;
  }

  async function QS_SC(){
    QS_KK();
    cb.disabled=true;fb.disabled=true;
    idle.style.display='none';ra.style.display='none';
    QS_ST('Iniciando camara...','act');
    try{
      await QS_LZ();
      const s=await navigator.mediaDevices.getUserMedia({video:{facingMode:{ideal:'environment'},width:{ideal:1280},height:{ideal:720},frameRate:{ideal:30}},audio:false});
      try{s.getVideoTracks()[0].applyConstraints({advanced:[{focusMode:'continuous'}]}).catch(()=>{});}catch{}
      const v=document.createElement('video');
      v.muted=true;v.playsInline=true;v.setAttribute('playsinline','');v.srcObject=s;
      const rd=$('qr-reader'),gd=document.createElement('div');gd.className='QS_G1';
      rd.innerHTML='';rd.append(v,gd);
      const k={s,v,on:true,t:0,i:0};_cam=k;
      sa.style.display='';
      await v.play();
      const c=document.createElement('canvas'),x=c.getContext('2d',{willReadFrequently:true});
      QS_ST('Apunta al codigo...','act');cb.disabled=false;fb.disabled=false;
      const lp=async()=>{
        if(!k.on)return;
        if(v.readyState>=2&&v.videoWidth){
          const vw=v.videoWidth,vh=v.videoHeight,s0=Math.min(vw,vh),hd=k.i++%3===2,z=Math.min(s0,hd?960:480);
          c.width=c.height=z;
          x.drawImage(v,(vw-s0)/2,(vh-s0)/2,s0,s0,0,0,z,z);
          let r=null;
          try{r=await QS_DC(x.getImageData(0,0,z,z),!hd);}catch{}
          if(!k.on)return;
          if(r){QS_KK();QS_SR(r);return;}
        }
        if(v.requestVideoFrameCallback)v.requestVideoFrameCallback(lp);else k.t=setTimeout(lp,30);
      };
      lp();
    }catch(e){
      QS_KK();
      sa.style.display='none';idle.style.display='';
      cb.disabled=false;fb.disabled=false;
      QS_T('Error camara: '+(e.name||e.message||e));QS_ST('Lector QR');
    }
  }

  async function QS_SB(input){
    idle.style.display='none';
    QS_ST('Procesando...','act');
    try{
      const r=await QS_DC(input);
      if(r){QS_SR(r);return;}
      QS_T('No se encontro codigo');
    }catch(e){QS_T('Error: '+(e.message||e));}
    QS_ST('Lector QR');
    idle.style.display='';
    cb.disabled=false;fb.disabled=false;
  }

  function QS_CX(){
    if(_cp){_cp.destroy();_cp=null;}
    if(_blobUrl){URL.revokeObjectURL(_blobUrl);_blobUrl=null;}
    cm.close();document.body.style.overflow='';
  }

  async function QS_HF(file){
    if(!file.type.startsWith('image/')){QS_T('Solo imagenes');return;}
    _pf=file;
    QS_KK();
    cb.disabled=true;fb.disabled=true;
    try{await QS_LC();}catch{}
    cif.textContent=file.name;
    cm.showModal();document.body.style.overflow='hidden';
    const url=URL.createObjectURL(file);
    _blobUrl=url;
    function QS_IC(){
      if(!window.Cropper)return;
      if(_cp){_cp.destroy();_cp=null;}
      _cp=new Cropper(ci,{viewMode:1,dragMode:'move',background:false,autoCropArea:.9,aspectRatio:NaN});
    }
    ci.onload=QS_IC;
    ci.src=url;
    if(ci.complete&&ci.naturalWidth)QS_IC();
  }

  $('qr-cok').onclick=()=>{
    if(!_cp){$('qr-ccl').onclick();return;}
    const canvas=_cp.getCroppedCanvas({imageSmoothingQuality:'high'});
    QS_CX();_pf=null;
    canvas.toBlob(b=>QS_SB(b),'image/png');
  };

  $('qr-csk').onclick=()=>{
    QS_CX();
    const f=_pf;_pf=null;
    if(f)QS_SB(f);
  };

  $('qr-ccl').onclick=()=>{
    QS_CX();
    _pf=null;cb.disabled=false;fb.disabled=false;
    if(!_res&&sa.style.display==='none'){idle.style.display='';QS_ST('Lector QR');}
  };

  cm.oncancel=e=>{e.preventDefault();$('qr-ccl').onclick();};

  $('qr-cc').onclick=()=>{
    QS_KK();
    sa.style.display='none';idle.style.display='';
    cb.disabled=false;fb.disabled=false;
    QS_ST('Lector QR');
  };

  cb.onclick=QS_SC;
  fb.onclick=()=>{
    if(QG_PD){const f=QG_PD;QG_PD=null;QS_HF(f);return;}
    inEl.click();
  };
  inEl.onchange=e=>{if(e.target.files[0])QS_HF(e.target.files[0]);inEl.value='';};

  $('qr-cp').onclick=async()=>{
    if(!_res)return;
    try{await navigator.clipboard.writeText(_res);QS_T('Copiado');}
    catch{QS_T('Error al copiar');}
  };

  $('qr-ns').onclick=()=>{
    QS_KK();
    sa.style.display='none';ra.style.display='none';idle.style.display='';
    rl.style.display='none';rl.removeAttribute('href');
    rt.textContent='';dt.textContent='';_res='';
    QS_ST('Lector QR');cb.disabled=false;fb.disabled=false;
  };

  function QG_PR(){
    return{k:$('qg-k').value,ae:+$('qg-ae').value,af:$('qg-af').value,
      ver:+$('qg-v').value,ecc:$('qg-e').value,sh:$('qg-sh').value,
      mn:+$('qg-mn').value/100,mx:+$('qg-mx').value/100,gh:+$('qg-gh').value/100,
      th:+$('qg-th').value/100,sat:+$('qg-sa').value/100,
      col:$('qg-co').value==='1',px:+$('qg-px').value,sd:+$('qg-sd').value,
      ix:+$('qg-ix').value/100,iy:+$('qg-iy').value/100,iz:+$('qg-iz').value/100,
      ir:+$('qg-ir').value*Math.PI/180,iw:+$('qg-iw').value/100,ih:+$('qg-ih').value/100,
      tm:$('qg-tm').value==='1',qz:+$('qg-qz').value};
  }

  function QG_A1(n){
    const v=(n-17)/4;
    if(v<2)return[];
    const k=Math.floor(v/7)+2,last=v*4+10;
    if(k===2)return[6,last];
    const st=Math.ceil((last-6)/(k-1)/2)*2,o=[6];
    for(let i=1;i<k;i++)o.push(last-(k-1-i)*st);
    return o;
  }

  function QG_K1(r,c,n){
    return(r<8&&c<8)||(r<8&&c>=n-8)||(r>=n-8&&c<8);
  }

  function QG_K2(r,c,n,al){
    if(r===6||c===6)return true;
    for(let i=0;i<al.length;i++)for(let j=0;j<al.length;j++){
      const ar=al[i],ac=al[j];
      if((ar<8&&ac<8)||(ar<8&&ac>n-9)||(ar>n-9&&ac<8))continue;
      if(Math.abs(r-ar)<=2&&Math.abs(c-ac)<=2)return true;
    }
    return false;
  }

  function QG_MQ(txt,P){
    let q=null;
    for(const v of[P.ver,0]){
      try{const z=qrcode(v,P.ecc);z.addData(txt);z.make();q=z;break;}catch{}
    }
    if(!q)return null;
    const n=q.getModuleCount(),al=QG_A1(n);
    return{n,q:P.qz,dk:(r,c)=>q.isDark(r,c),cr:(r,c)=>QG_K1(r,c,n),tm:(r,c)=>QG_K2(r,c,n,al)};
  }

  function QG_MA(txt,P){
    try{
      const o={bcid:'azteccode',text:txt,eclevel:P.ae};
      if(P.af)o.format=P.af;
      const a=bwipjs.raw(o)[0],n=a.pixx,c0=(n-1)/2;
      const at=(r,c)=>a.pixs[r*n+c];
      let full=true;
      for(let i=-6;i<=6&&full;i++)for(const[dr,dc]of[[-6,i],[6,i],[i,-6],[i,6]])if(!at(c0+dr,c0+dc)){full=false;break;}
      const cr=full?7:5;
      return{n,q:P.qz,dk:(r,c)=>at(r,c)===1,
        cr:(r,c)=>Math.max(Math.abs(r-c0),Math.abs(c-c0))<=cr,
        tm:(r,c)=>full&&((r-c0)%16===0||(c-c0)%16===0)};
    }catch{return null;}
  }

  function QG_G1(img,sz,P){
    const c=document.createElement('canvas');c.width=c.height=sz;
    const x=c.getContext('2d',{willReadFrequently:true});
    const iw=img.naturalWidth||img.videoWidth||img.displayWidth||img.width,ih=img.naturalHeight||img.videoHeight||img.displayHeight||img.height;
    const s=Math.max(sz/iw,sz/ih)*(P?P.iz:1);
    const dw=iw*s*(P?P.iw:1),dh=ih*s*(P?P.ih:1);
    x.translate(sz/2+(P?P.ix*sz/2:0),sz/2+(P?P.iy*sz/2:0));
    if(P&&P.ir)x.rotate(P.ir);
    x.drawImage(img,-dw/2,-dh/2,dw,dh);
    return x.getImageData(0,0,sz,sz);
  }

  function QG_P1(g,c,r){
    const i=(r*g.width+c)*4;
    return{r:g.data[i],g:g.data[i+1],b:g.data[i+2],a:g.data[i+3]};
  }

  function QG_B1(p,amt){
    const mx=Math.max(p.r,p.g,p.b),mn=Math.min(p.r,p.g,p.b);
    if(mx===mn)return p;
    const f=1+amt,md=(mx+mn)/2;
    const cl=v=>Math.max(0,Math.min(255,Math.round(md+(v-md)*f)));
    return{r:cl(p.r),g:cl(p.g),b:cl(p.b)};
  }

  function QG_D1(x,cx,cy,rad,sh,col){
    if(rad<=0)return;
    x.fillStyle=col;
    if(sh==='sq'||sh==='ht'){x.fillRect(cx-rad,cy-rad,rad*2,rad*2);return;}
    if(sh==='rd'&&x.roundRect){x.beginPath();x.roundRect(cx-rad,cy-rad,rad*2,rad*2,rad*.5);x.fill();return;}
    x.beginPath();x.arc(cx,cy,rad,0,6.2832);x.fill();
  }

  function QG_MD(p,L,P){
    if(!P.col)return{r:17,g:17,b:17};
    const b=QG_B1(p,P.sat);
    if(L>.72){const m=(L-.72)/.28*.8;return{r:Math.round(b.r*(1-m)),g:Math.round(b.g*(1-m)),b:Math.round(b.b*(1-m))};}
    return b;
  }

  function QG_RG(c){return'rgb('+c.r+','+c.g+','+c.b+')';}

  function QG_GH(sp,c,r,cell,q,sd,grid,P){
    const sub=cell/sd,srad=sub/2;
    for(let sy=0;sy<sd;sy++)for(let sx=0;sx<sd;sx++){
      const px=QG_P1(grid,c*sd+sx,r*sd+sy);
      if(!px||px.a<=60)continue;
      const d=1-(.299*px.r+.587*px.g+.114*px.b)/255;
      if(d<=P.th)continue;
      const k=(d-P.th)/(1-P.th);
      const cc=P.col?QG_B1(px,P.sat):{r:17,g:17,b:17};
      sp((c+q)*cell+sx*sub+sub,(r+q)*cell+sy*sub+sub,srad*Math.min(.84,.12+.84*P.gh*Math.pow(k,.55)),QG_RG(cc));
    }
  }

  function QG_LM(c,t){
    const L=(.299*c.r+.587*c.g+.114*c.b)/255;
    if(t<=L){const f=L?t/L:0;return{r:Math.round(c.r*f),g:Math.round(c.g*f),b:Math.round(c.b*f)};}
    const f=(t-L)/(1-L);
    return{r:Math.round(c.r+(255-c.r)*f),g:Math.round(c.g+(255-c.g)*f),b:Math.round(c.b+(255-c.b)*f)};
  }

  function QG_HT(sp,P,M,im){
    const n=M.n,q=M.q,cell=P.px/(n+q*2),s=cell/3,h=s/2+.3,k=(1-P.gh)*.5;
    const g=im?QG_G1(im,n*3,P):null;
    for(let r=0;r<n;r++)for(let c=0;c<n;c++){
      const d=M.dk(r,c),x0=(c+q)*cell,y0=(r+q)*cell;
      if(!g||M.cr(r,c)||(M.tm(r,c)&&!P.tm)){if(d)sp(x0+cell/2,y0+cell/2,cell/2+.3,'#111');continue;}
      for(let sy=0;sy<3;sy++)for(let sx=0;sx<3;sx++){
        let p=QG_P1(g,c*3+sx,r*3+sy);
        if(p.a<=60)p={r:255,g:255,b:255};
        if(P.col)p=QG_B1(p,P.sat);
        else{const v=Math.round(.299*p.r+.587*p.g+.114*p.b);p={r:v,g:v,b:v};}
        const L=(.299*p.r+.587*p.g+.114*p.b)/255;
        const t=sx===1&&sy===1?(d?Math.min(L,.28):Math.max(L,.78)):L+((d?0:1)-L)*k;
        sp(x0+sx*s+s/2,y0+sy*s+s/2,h,QG_RG(QG_LM(p,t)));
      }
    }
  }

  function QG_RD(sp,P,M,im=QG_I){
    if(P.sh==='ht')return QG_HT(sp,P,M,im);
    const n=M.n,q=M.q,cell=P.px/(n+q*2),maxR=cell/2,sd=P.sd||1;
    const grid=im?QG_G1(im,n*sd,P):null,gridM=im?(sd>1?QG_G1(im,n,P):grid):null;
    for(let r=0;r<n;r++)for(let c=0;c<n;c++){
      const cx=(c+q+.5)*cell,cy=(r+q+.5)*cell,crit=M.cr(r,c),dark=M.dk(r,c);
      if(dark&&crit){sp(cx,cy,maxR+.3,'#111','sq');continue;}
      if(dark){
        const p=gridM?QG_P1(gridM,c,r):null,has=!!p&&p.a>60;
        const L=has?(.299*p.r+.587*p.g+.114*p.b)/255:0;
        const cc=has?QG_MD(p,L,P):{r:17,g:17,b:17};
        sp(cx,cy,maxR*(has?Math.min(1.02,P.mn+(P.mx-P.mn)*(1-L)):.98),QG_RG(cc));
      }else if(!crit&&(!M.tm(r,c)||P.tm)&&P.gh>0&&grid)QG_GH(sp,c,r,cell,q,sd,grid,P);
    }
  }

  function QG_R1(){
    if(!QG_M)return;
    const P=QG_PR();
    qgc.width=qgc.height=P.px;
    const x=qgc.getContext('2d');
    x.fillStyle='#fff';x.fillRect(0,0,P.px,P.px);
    QG_RD((cx,cy,rad,col,s)=>QG_D1(x,cx,cy,rad,s||P.sh,col),P,QG_M);
  }

  function QG_SV1(){
    if(!QG_M)return '';
    const P=QG_PR(),px=P.px;
    const o=['<svg xmlns="http://www.w3.org/2000/svg" width="'+px+'" height="'+px+'" viewBox="0 0 '+px+' '+px+'"><metadata><rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:dc="http://purl.org/dc/elements/1.1/"><rdf:Description><dc:creator>'+QG_AU+'</dc:creator></rdf:Description></rdf:RDF></metadata><rect width="'+px+'" height="'+px+'" fill="#fff"/>'];
    const sp=(cx,cy,rad,col,s=P.sh)=>{
      if(s==='ci')o.push('<circle cx="'+cx.toFixed(1)+'" cy="'+cy.toFixed(1)+'" r="'+rad.toFixed(1)+'" fill="'+col+'"/>');
      else o.push('<rect x="'+(cx-rad).toFixed(1)+'" y="'+(cy-rad).toFixed(1)+'" width="'+(rad*2).toFixed(1)+'" height="'+(rad*2).toFixed(1)+'"'+(s==='rd'?' rx="'+(rad*.5).toFixed(1)+'"':'')+' fill="'+col+'"/>');
    };
    QG_RD(sp,P,QG_M);
    o.push('</svg>');
    return o.join('');
  }

  function QD_CL(){
    qgo.getContext('2d').clearRect(0,0,qgo.width,qgo.height);
    dg.textContent='';mp.style.display='none';
  }

  async function QD_RUN(){
    if(!QG_M){QS_T('Escribi algo primero');return;}
    const M=QG_M,n=M.n,q=M.q,W=Math.min(qgc.width,1024),cell=W/(n+q*2),txt=$('qg-t').value.trim(),tb=$('qg-tb');
    tb.disabled=true;dg.textContent='Analizando...';
    try{
      const wc=document.createElement('canvas');wc.width=wc.height=W;
      const wx=wc.getContext('2d',{willReadFrequently:true});
      wx.drawImage(qgc,0,0,W,W);
      const d0=wx.getImageData(0,0,W,W),r0=await QS_DC(d0);
      const L=[];
      for(let r=0;r<n;r++)for(let c=0;c<n;c++){
        const x0=Math.floor((c+q+.4)*cell),x1=Math.max(x0+1,Math.ceil((c+q+.6)*cell));
        const y0=Math.floor((r+q+.4)*cell),y1=Math.max(y0+1,Math.ceil((r+q+.6)*cell));
        let s=0,k=0;
        for(let y=y0;y<y1;y++)for(let x=x0;x<x1;x++){const i=(y*W+x)*4;s+=.299*d0.data[i]+.587*d0.data[i+1]+.114*d0.data[i+2];k++;}
        L.push(s/k);
      }
      let t=127;
      for(let i=0;i<12;i++){
        let a=0,ka=0,b=0,kb=0;
        for(const v of L){if(v<t){a+=v;ka++;}else{b+=v;kb++;}}
        const nt=((ka?a/ka:0)+(kb?b/kb:255))/2;
        if(Math.abs(nt-t)<.5)break;
        t=nt;
      }
      qgo.width=qgo.height=W;
      const ox=qgo.getContext('2d'),cand=[];
      let wd=0,wk=0;
      for(let r=0;r<n;r++)for(let c=0;c<n;c++){
        const cr=M.cr(r,c);
        if((L[r*n+c]<t)===!!M.dk(r,c)){if(!cr)cand.push(r*n+c);continue;}
        if(cr)wk++;else wd++;
        ox.fillStyle=cr?'rgba(255,140,0,.6)':'rgba(255,0,60,.5)';
        ox.fillRect((c+q)*cell,(r+q)*cell,cell,cell);
      }
      const tot=wd+cand.length;
      let lo=0;
      if(r0){
        let s=7;
        const rn=()=>(s=(s*1664525+1013904223)>>>0)/4294967296;
        for(let i=cand.length-1;i>0;i--){const j=Math.floor(rn()*(i+1));[cand[i],cand[j]]=[cand[j],cand[i]];}
        let hi=Math.floor(cand.length/2);
        while(hi-lo>Math.max(1,cand.length*.005)){
          const m=(lo+hi)>>1;
          wx.putImageData(d0,0,0);
          for(let i=0;i<m;i++){
            const v=cand[i],r=(v/n)|0,c=v%n;
            wx.fillStyle=M.dk(r,c)?'#fff':'#111';
            wx.fillRect(Math.floor((c+q)*cell),Math.floor((r+q)*cell),Math.ceil(cell),Math.ceil(cell));
          }
          dg.textContent='Margen '+Math.round(m/cand.length*100)+'%...';
          if(await QS_DC(wx.getImageData(0,0,W,W)))lo=m;else hi=m;
        }
      }
      const u=r0?QS_XI(r0).UEC:null,bad=wd+wk;
      const ln=[r0?'Lee: SI'+(r0.text===txt?'':' (texto distinto)')+(typeof u==='number'?(u>.5?' - holgado':u>.2?' - justo':' - al limite'):''):'Lee: NO'];
      if(r0)ln.push(QS_DT(r0));
      ln.push('Modulos mal: '+bad+'/'+n*n+' ('+(bad/n/n*100).toFixed(1)+'%) datos '+wd+' criticos '+wk);
      if(r0)ln.push('Margen: +'+(lo/tot*100).toFixed(1)+'% extra ('+lo+' modulos)');
      dg.textContent=ln.join('\n');
      mp.style.display='';qgo.style.display='';
    }catch(e){dg.textContent='Error: '+(e.message||e);}
    tb.disabled=false;
  }

  async function QG_LQ(){
    if(window.qrcode)return;
    await QS_LS(QGL);await QS_LS(QGU);
  }

  function QG_U1(){
    clearTimeout(QG_TO);
    QG_TO=setTimeout(async()=>{
      const k=++QG_K,t=$('qg-t').value.trim();
      ['mn','mx','gh','th','sa','ae'].forEach(i=>{$('qg-'+i+'-l').textContent=$('qg-'+i).value+'%';});
      $('qg-sd-l').textContent=$('qg-sd').value+'x';
      $('qg-qz-l').textContent=$('qg-qz').value;
      ['ix','iy','iz','iw','ih'].forEach(i=>{$('qg-'+i+'-l').textContent=$('qg-'+i).value+'%';});
      $('qg-ir-l').textContent=$('qg-ir').value+'°';
      QD_CL();
      const P=QG_PR(),az=P.k==='az';
      qg.classList.toggle('QG_HI',!!QG_I);
      $('qg-gq').style.display=az?'none':'';$('qg-ga').style.display=az?'':'none';
      if(!t){QG_M=null;const x=qgc.getContext('2d');qgc.width=qgc.height=320;x.clearRect(0,0,320,320);QS_ST('Crear QR');return;}
      if(az&&!window.bwipjs){
        QS_ST('Cargando Aztec...','act');
        try{await QS_LS(BWL);}catch{QS_T('No se pudo cargar Aztec');QS_ST('Crear QR');return;}
        if(k!==QG_K)return;
      }
      QG_M=az?QG_MA(t,P):QG_MQ(t,P);
      if(!QG_M){QS_ST('Texto muy largo','');QS_T(az?'No entra, baja la correccion':'No entra en ese tamano, subi la densidad');return;}
      QG_R1();
      QS_ST('Crear QR','ok');
    },90);
  }

  function QG_DL(blob,name){
    const u=URL.createObjectURL(blob),a=document.createElement('a');
    a.href=u;a.download=name;document.body.appendChild(a);a.click();a.remove();
    setTimeout(()=>URL.revokeObjectURL(u),15000);
  }

  function QG_IM1(f){
    const vd=!!f&&f.type.startsWith('video/');
    if(!f||(!vd&&!f.type.startsWith('image/'))){QS_T('Solo imagen o video');return;}
    if(QG_IU)URL.revokeObjectURL(QG_IU);
    QG_IU=URL.createObjectURL(f);
    if(QG_AD){QG_AD.close();QG_AD=null;}
    const ok=el=>{QG_I=el;QG_VF=vd?f:null;$('qg-rb').style.display='';$('qg-mv').style.display=vd?'':'none';$('qg-gf').style.display='none';QG_U1();};
    if(vd){
      const v=document.createElement('video');
      v.muted=true;v.playsInline=true;v.preload='auto';
      v.onloadedmetadata=()=>{v.currentTime=Math.min(1,(v.duration||0)/2);};
      v.onseeked=()=>{v.onseeked=null;ok(v);};
      v.onerror=()=>{QS_T('Video invalido');};
      v.src=QG_IU;
      return;
    }
    const im=new Image();
    im.onload=async()=>{
      ok(im);
      const d=await QG_AI(f);
      if(QG_I!==im){d?.close();return;}
      QG_AD?.close();QG_AD=d;
      $('qg-mv').style.display=$('qg-gf').style.display=d?'':'none';
    };
    im.onerror=()=>{QS_T('Imagen invalida');};
    im.src=QG_IU;
  }

  async function QG_AI(f){
    try{
      if(!window.ImageDecoder||!await ImageDecoder.isTypeSupported(f.type))return null;
      const d=new ImageDecoder({data:await f.arrayBuffer(),type:f.type});
      await d.completed;await d.tracks.ready;
      if(d.tracks.selectedTrack?.frameCount>1)return d;
      d.close();
    }catch{}
    return null;
  }

  async function QG_AF(fn){
    const d=QG_AD,k=d.tracks.selectedTrack.frameCount;
    for(let i=0;i<k;i++){
      const{image}=await d.decode({frameIndex:i});
      try{await fn(image,i,k);}finally{image.close();}
    }
  }

  function QG_CR(b){
    if(!QG_CT){QG_CT=new Uint32Array(256);for(let n=0;n<256;n++){let c=n;for(let k=0;k<8;k++)c=c&1?0xEDB88320^(c>>>1):c>>>1;QG_CT[n]=c>>>0;}}
    let c=~0;for(const v of b)c=QG_CT[(c^v)&255]^(c>>>8);
    return(~c)>>>0;
  }

  async function QG_PA(blob){
    const a=new Uint8Array(await blob.arrayBuffer()),d=new TextEncoder().encode('Author\0'+QG_AU);
    const ch=new Uint8Array(12+d.length),v=new DataView(ch.buffer);
    v.setUint32(0,d.length);ch.set([116,69,88,116],4);ch.set(d,8);
    v.setUint32(8+d.length,QG_CR(ch.subarray(4,8+d.length)));
    return new Blob([a.subarray(0,33),ch,a.subarray(33)],{type:'image/png'});
  }

  async function QG_VX(gf){
    if(!QG_M||!(gf?QG_AD:QG_VF||QG_AD))return;
    const b=$(gf?'qg-gf':'qg-mv'),nm=gf?'GIF':'Video';b.disabled=true;
    QD_CL();st.previousElementSibling.scrollIntoView({behavior:'smooth',block:'start'});
    QS_ST('Cargando conversor...','act');
    try{
      const MB=await import(gf?GFL:MBL);
      const P=QG_PR(),M=QG_M,px=Math.min(P.px,gf?512:1024),Q={...P,px};
      const c=document.createElement('canvas');c.width=c.height=px;
      const x=c.getContext('2d',{willReadFrequently:true});
      const sp=(cx,cy,rad,col,s)=>QG_D1(x,cx,cy,rad,s||Q.sh,col),pv=qgc.getContext('2d');
      let n=0,t=0,ok=0,r;
      const rd=async im=>{
        x.fillStyle='#fff';x.fillRect(0,0,px,px);
        QG_RD(sp,Q,M,im);
        pv.drawImage(c,0,0,qgc.width,qgc.height);
        if(n++%10===0){t++;try{if(await QS_DC(x.getImageData(0,0,px,px),true))ok++;}catch{}}
        return c;
      };
      const pg=(i,k)=>QS_ST(nm+' '+Math.round((i+1)/k*100)+'%','act');
      if(gf){
        const g=MB.GIFEncoder();
        await QG_AF(async(im,i,k)=>{
          await rd(im);
          const d=x.getImageData(0,0,px,px).data,pl=MB.quantize(d,256);
          g.writeFrame(MB.applyPalette(d,pl),px,px,{palette:pl,delay:(im.duration||1e5)/1e3});
          pg(i,k);
        });
        g.finish();
        r=[new Blob([g.bytes()],{type:'image/gif'}),'qr.gif','image/gif'];
      }else{
        const out=new MB.Output({format:new MB.Mp4OutputFormat(),target:new MB.BufferTarget()});
        if(QG_AD){
          const cs=new MB.CanvasSource(c,{codec:await MB.getFirstEncodableVideoCodec(out.format.getSupportedVideoCodecs(),{width:px,height:px}),bitrate:MB.QUALITY_HIGH});
          out.addVideoTrack(cs);out.setMetadataTags({artist:QG_AU});
          await out.start();
          let s=0;
          do await QG_AF(async(im,i,k)=>{const d=(im.duration||1e5)/1e6;await rd(im);await cs.add(s,d);s+=d;pg(i,k);});
          while(s<3);
          await out.finalize();
        }else{
          const cv=await MB.Conversion.init({
            input:new MB.Input({source:new MB.BlobSource(QG_VF),formats:MB.ALL_FORMATS}),output:out,tags:{artist:QG_AU},
            video:{forceTranscode:true,processedWidth:px,processedHeight:px,process:s=>rd(s.toCanvasImageSource())}
          });
          if(!cv.isValid)throw new Error('formato no soportado');
          cv.onProgress=p=>QS_ST('Video '+Math.round(p*100)+'%','act');
          QG_VC=cv;
          await cv.execute();
          QG_VC=null;
        }
        r=[new Blob([out.target.buffer],{type:'video/mp4'}),'qr.mp4','video/mp4'];
      }
      dg.textContent=nm+': lee '+ok+' de '+t+' cuadros muestreados';
      QS_ST('Crear QR','ok');
      await QG_OUT(...r);
    }catch(e){
      QG_VC=null;
      if(e&&e.name!=='ConversionCanceledError'&&e.name!=='AbortError'){QS_T('Error '+nm+': '+(e.message||e));QS_ST('Crear QR');}
    }
    QG_R1();
    b.disabled=false;
  }

  async function QG_ON(){
    QS_KK();
    QS_ST('Cargando...','act');
    try{await QG_LQ();}
    catch{QS_T('No se pudo cargar el generador');QS_ST('Lector QR');return;}
    idle.style.display='none';sa.style.display='none';ra.style.display='none';
    qg.style.display='';
    QS_ST('Crear QR');
    if(QG_PD){const f=QG_PD;QG_PD=null;if(!$('qg-t').value.trim())$('qg-t').value=QG_HOME;QG_IM1(f);}
    QG_U1();
  }

  async function QG_OUT(blob,name,type){
    QG_DL(blob,name);
    const f=new File([blob],name,{type});
    if(navigator.canShare&&navigator.canShare({files:[f]}))await navigator.share({files:[f]}).catch(()=>{});
  }

  function QG_PV(e){
    const its=e.clipboardData&&e.clipboardData.items;
    if(!its)return;
    for(let i=0;i<its.length;i++){
      if(!its[i].type||!its[i].type.startsWith('image/'))continue;
      const f=its[i].getAsFile();
      if(!f)continue;
      e.preventDefault();
      if(qg.style.display!=='none')QG_IM1(f);
      else{QG_PD=null;QS_HF(f);}
      return;
    }
  }

  function QG_OFF(){
    qg.style.display='none';idle.style.display='';
    QS_ST('Lector QR');
    cb.disabled=false;fb.disabled=false;
  }

  $('qg-ab').onclick=QG_ON;
  $('qg-bk').onclick=QG_OFF;
  $('qg-t').addEventListener('input',QG_U1);
  ['qg-k','qg-ae','qg-af','qg-v','qg-e','qg-sh','qg-mn','qg-mx','qg-gh','qg-th','qg-sa','qg-co','qg-px','qg-sd','qg-ix','qg-iy','qg-iz','qg-ir','qg-iw','qg-ih','qg-tm','qg-qz'].forEach(id=>{
    $(id).addEventListener('input',QG_U1);
  });
  $('qg-irs').onclick=()=>{
    ['qg-ix','qg-iy','qg-ir'].forEach(id=>{$(id).value=0;});
    ['qg-iz','qg-iw','qg-ih'].forEach(id=>{$(id).value=100;});
    QG_U1();
  };
  $('qg-ib').onclick=()=>$('qg-if').click();
  $('qg-if').onchange=e=>{const f=e.target.files[0];e.target.value='';QG_IM1(f);};
  $('qg-rb').onclick=()=>{
    QG_I=null;QG_VF=null;
    if(QG_AD){QG_AD.close();QG_AD=null;}
    if(QG_IU){URL.revokeObjectURL(QG_IU);QG_IU=null;}
    $('qg-rb').style.display='none';$('qg-mv').style.display='none';$('qg-gf').style.display='none';QG_U1();
  };
  $('qg-pn').onclick=()=>{
    if(!QG_M){QS_T('Escribi algo primero');return;}
    qgc.toBlob(async b=>{if(b)QG_OUT(await QG_PA(b),'qr.png','image/png');},'image/png');
  };
  $('qg-sv').onclick=()=>{
    if(!QG_M){QS_T('Escribi algo primero');return;}
    QG_OUT(new Blob([QG_SV1()],{type:'image/svg+xml'}),'qr.svg','image/svg+xml');
  };
  $('qg-tb').onclick=QD_RUN;
  $('qg-mv').onclick=()=>QG_VX();
  $('qg-gf').onclick=()=>QG_VX(1);
  mp.onclick=()=>{qgo.style.display=qgo.style.display==='none'?'':'none';};

  document.addEventListener('paste',QG_PV);

  const cont=document.getElementById('content');
  if(cont)cont.addEventListener('contentUnload',()=>{
    QS_KK();QS_CX();
    if(QG_VC)QG_VC.cancel().catch(()=>{});
    if(QG_AD){QG_AD.close();QG_AD=null;}
    document.removeEventListener('paste',QG_PV);
    if(QG_IU){URL.revokeObjectURL(QG_IU);QG_IU=null;}
    clearTimeout(_tt);clearTimeout(QG_TO);
  },{once:true});

  (async()=>{
    try{
      const C={cacheName:'share-pending'},r=await caches.match('/__share_data',C);
      if(!r||Date.now()>+r.headers.get('X-Expires'))return;
      const d=await r.json(),b=d.files[0];
      if(b&&b.type.startsWith('image/')){
        QG_PD=new File([await(await caches.match(b.key,C)).blob()],b.name||'imagen.png',{type:b.type});
        await caches.delete('share-pending');
        QS_ST('Imagen recibida: leer o crear','act');
        return;
      }
      const t=((d.url||'')+' '+(d.text||'')).trim();
      if(!t)return;
      await caches.delete('share-pending');
      await QG_ON();
      $('qg-t').value=t;
      QG_U1();
    }catch{}
  })();
})();
</script>


</br>

<a href="web/paginas/apps.html" class="back-button">← Volver a Applicaciones </a>

</br>

<div id="sh" data-t="Mira, genere un QR animado aqui"></div>