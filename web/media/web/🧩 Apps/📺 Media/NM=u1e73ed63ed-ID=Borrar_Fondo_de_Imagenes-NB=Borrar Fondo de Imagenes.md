<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.bf-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 6px}
.bf-nt{color:rgba(255,255,255,.45);font-size:.8em;max-width:460px;margin:0 auto 16px;line-height:1.5}
.bf-dz{display:block;max-width:420px;margin:0 auto 12px;padding:22px 16px;border:2px dashed rgba(255,255,255,.2);border-radius:16px;cursor:pointer;color:rgba(255,255,255,.7);transition:border-color .2s,background .2s}
.bf-dz.on{border-color:rgba(56,189,248,.6);background:rgba(56,189,248,.06)}
.bf-pn{max-width:560px;margin:0 auto 12px;padding:10px 12px;border-radius:14px;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.04);text-align:left}
.bf-pn summary{cursor:pointer;color:rgba(255,255,255,.8);font-weight:600}
.bf-op{display:flex;gap:10px 14px;flex-wrap:wrap;align-items:center;margin-top:8px;color:rgba(255,255,255,.75);font-size:.85em}
.bf-op select,.bf-op input[type=color]{background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);border-radius:8px;color:#fff;padding:4px 6px;font-family:inherit;max-width:100%}
.bf-in{color:rgba(255,255,255,.5);font-size:.78em;margin-top:6px;line-height:1.6}
.bf-in a{color:inherit}
.bf-ac{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;margin:0 auto 10px}
.bf-ac:empty{display:none}
.bf-ls{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:12px;max-width:900px;margin:0 auto}
.bf-cd{border-radius:14px;padding:10px;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06);text-align:left;min-width:0}
.bf-iw{position:relative}
.bf-iw .wait-anim{position:absolute;inset:0;margin:auto}
.bf-im{display:block;width:100%;height:240px;object-fit:contain;border-radius:8px;background:repeating-conic-gradient(#777 0 25%,#aaa 0 50%) 0 0/16px 16px}
.bf-nm{font-weight:700;color:#fff;word-break:break-all;margin-top:6px;font-size:.9em}
.bf-ms{color:rgba(255,255,255,.55);font-size:.78em;margin:2px 0 6px;line-height:1.4}
.bf-cd .bf-ac{justify-content:flex-start;margin:0}
</style>
<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">✂️</div>
<div class="bf-st">Borrar Fondo de Imagenes</div>
<div class="bf-nt">Quita el fondo de tus fotos en tu dispositivo, sin subirlas. Elegi el modelo segun tu equipo: la primera vez se descarga y despues queda guardado.</div>
<label class="bf-dz" id="bf-dz">🖼️ Toca o arrastra fotos aca<input type="file" id="bf-fi" accept="image/*" multiple hidden></label>
<details class="bf-pn" open><summary>🧠 Modelo</summary>
<div class="bf-op">
<label>Modelo <select id="bf-m"></select></label>
<label>Motor <select id="bf-dv"><option value="auto">Auto</option><option value="webgpu">WebGPU (placa de video)</option><option value="wasm">WASM (procesador)</option></select></label>
<label>Precision <select id="bf-d"></select></label>
<label>Tamano max <select id="bf-mx"><option value="1024">1024 px</option><option value="2048">2048 px</option><option value="4096" selected>4096 px</option><option value="0">Original</option></select></label>
</div>
<div class="bf-in" id="bf-mi"></div>
<div class="bf-in" id="bf-eq"></div>
</details>
<details class="bf-pn" open><summary>🎨 Resultado</summary>
<div class="bf-op">
<label>Fondo <select id="bf-bg"><option value="t">Transparente</option><option value="c">Color</option><option value="b">Desenfocado</option></select></label>
<input type="color" id="bf-cl" value="#ffffff" hidden>
<label>Umbral <input type="range" id="bf-u" min="0" max="95" step="5" value="0"> <span id="bf-uv">Suave</span></label>
<label>Suavizar borde <input type="range" id="bf-sv" min="0" max="10" value="0"> <span id="bf-svv">0</span> px</label>
<label><input type="checkbox" id="bf-rc"> Recortar al objeto</label>
<label>Formato <select id="bf-f"><option value="image/png">PNG</option><option value="image/webp">WebP</option><option value="image/jpeg">JPG</option></select></label>
<label id="bf-ql" hidden>Calidad <input type="range" id="bf-q" min="40" max="100" value="90"> <span id="bf-qv">90</span></label>
</div>
<div class="bf-in">Se aplica al instante, sin volver a procesar. JPG no tiene transparencia: sale con fondo blanco.</div>
</details>
<div class="bf-ac" id="bf-ac"></div>
<div class="bf-ls" id="bf-ls"></div>
<details class="bf-pn" id="bf-gd"><summary>💾 Modelos guardados</summary><div class="bf-in" id="bf-gl"></div></details>

<script>
(function(){
const $=i=>document.getElementById(i);
const WA=window.__CFG?.waitAnim||'';
const BF_M=[
['onnx-community/ormbg-ONNX','ormbg','Apache-2.0','General y rapido. Recomendado para empezar.',{q8:42,fp16:84,fp32:168}],
['onnx-community/BiRefNet_lite-ONNX','BiRefNet lite','MIT','Bordes mas finos. Pide mas de 1,5 GB de memoria libre.',{fp16:109,fp32:214}],
['onnx-community/BiRefNet-ONNX','BiRefNet','MIT','La mejor calidad. Solo PC con buena placa de video.',{fp16:467,fp32:928}],
['onnx-community/BiRefNet-portrait-ONNX','BiRefNet Retratos','MIT','Personas con calidad BiRefNet. Solo PC con buena placa de video.',{fp16:467,fp32:928}],
['onnx-community/BEN2-ONNX','BEN2','MIT','Bueno con pelo y bordes finos. Pesado, mejor con WebGPU.',{fp16:209}],
['onnx-community/MVANet-ONNX','MVANet','MIT','Pensado para detalles finos como rejas o ramas.',{q4f16:81,q8:135,fp16:202,fp32:402}],
['Xenova/modnet','MODNet','Apache-2.0','Solo personas. Muy liviano y rapido.',{q8:6,fp16:12,fp32:25}]
];
const BF_SRC=`import{pipeline,RawImage}from'https://cdn.jsdelivr.net/npm/@huggingface/transformers@4.3.2/+esm';
let S=null,K='';
self.onmessage=async e=>{const{id,m,d,dv,w,h,px}=e.data;
try{const k=m+'|'+d+'|'+dv;
if(K!==k){K='';const o=S;S=null;try{await o?.dispose()}catch{}
S=await pipeline('image-segmentation',m,{dtype:d,device:dv,progress_callback:p=>{if(p.status==='progress'&&p.total)self.postMessage({id,t:'p',f:p.file,l:p.loaded,n:p.total})}});K=k}
self.postMessage({id,t:'r'});
const t=performance.now(),[o]=await S(new RawImage(new Uint8ClampedArray(px),w,h,4)),a=new Uint8Array(o.mask.data);
self.postMessage({id,t:'ok',a,ms:performance.now()-t},[a.buffer]);
}catch(x){self.postMessage({id,t:'er',m:String(x&&x.message||x)})}};`;
const BF_K=['bf-m','bf-dv','bf-d','bf-mx','bf-bg','bf-cl','bf-u','bf-sv','bf-rc','bf-f','bf-q'];
let BF_W=null,BF_Q=Promise.resolve(),BF_N=0,BF_GA=false,BF_F16=false,BF_C=[],BF_PR={};
const BF_H={};
try{BF_PR=JSON.parse(localStorage.getItem('bf'))||{}}catch{}
const BF_SZ=n=>n<1048576?Math.round(n/1024)+' KB':(n/1048576).toFixed(1)+' MB';
const BF_MD=()=>BF_M.find(m=>m[0]===$('bf-m').value)||BF_M[0];
const BF_DV=()=>{const v=$('bf-dv').value;return v==='auto'?(BF_GA?'webgpu':'wasm'):v};
const BF_RD=(d,g)=>g?(BF_F16&&d.fp16?'fp16':d.fp32?'fp32':Object.keys(d)[0]):(d.q8?'q8':d.fp32?'fp32':Object.keys(d)[0]);
function BF_B(c,t,f,ti){const b=document.createElement('button');b.textContent=t;b.onclick=f;if(ti)b.title=ti;c.append(b);return b}
function BF_SV(){const o={};for(const k of BF_K){const e=$(k);o[k]=e.type==='checkbox'?e.checked:e.value}try{localStorage.setItem('bf',JSON.stringify(o))}catch{}}
function BF_DS(r){
  const m=BF_MD(),d=m[4];if(!(r in d))r=BF_RD(d,BF_DV()==='webgpu');
  $('bf-d').replaceChildren(...Object.keys(d).map(k=>new Option(`${k} · ${d[k]} MB`,k,k===r,k===r)));
  const i=$('bf-mi'),a=document.createElement('a');
  a.href='https://huggingface.co/'+m[0];a.target='_blank';a.rel='noopener';a.textContent='ver modelo';
  i.replaceChildren(`${m[3]} Licencia ${m[2]} · `,a);
}
function BF_EQ(){
  const n=navigator;
  $('bf-eq').textContent=`Tu equipo: WebGPU ${BF_GA?'si'+(BF_F16?' (fp16)':''):'no'} · ${n.hardwareConcurrency||'?'} nucleos${n.deviceMemory?' · RAM ~'+n.deviceMemory+' GB':''}. WASM usa un solo nucleo en esta web.`;
}
function BF_W1(){
  if(!BF_W){
    BF_W=new Worker(URL.createObjectURL(new Blob([BF_SRC],{type:'text/javascript'})),{type:'module'});
    BF_W.onmessage=e=>BF_H[e.data.id]?.(e.data);
  }
  return BF_W;
}
function BF_RN(c,m,d,dv){
  const id=++BF_N,pr={},px=c.x.getImageData(0,0,c.w,c.h).data.buffer;
  return new Promise((ok,er)=>{
    BF_H[id]=r=>{
      if(r.t==='p'){pr[r.f]=[r.l,r.n];let l=0,t=0;for(const k in pr){l+=pr[k][0];t+=pr[k][1]}c.st(`Descargando modelo ${Math.round(l/t*100)}% (${Math.round(t/1048576)} MB, una sola vez)`)}
      else if(r.t==='r')c.st(`Quitando fondo con ${dv==='webgpu'?'WebGPU':'WASM'}...`);
      else{delete BF_H[id];r.t==='ok'?ok(r):er(new Error(r.m))}
    };
    BF_W1().postMessage({id,m,d,dv,w:c.w,h:c.h,px},[px]);
  });
}
function BF_BZ(c,v){
  c.bz=v;c.im.style.opacity=v?.5:1;
  if(v&&WA&&!c.wi){c.wi=document.createElement('img');c.wi.className='wait-anim';c.wi.src=WA;c.wi.alt='';c.iw.append(c.wi)}
  else if(!v){c.wi?.remove();c.wi=null}
}
function BF_P1(c){
  BF_BZ(c,1);c.st('En espera...');
  BF_Q=BF_Q.then(async()=>{
    if(!BF_C.includes(c))return;
    const m=BF_MD(),au=$('bf-dv').value==='auto';let dv=BF_DV(),d=$('bf-d').value;
    try{
      c.st('Leyendo imagen...');
      const bm=await createImageBitmap(c.f),mx=+$('bf-mx').value,k=mx?Math.min(1,mx/Math.max(bm.width,bm.height)):1;
      if(c.cv)c.cv.width=0;
      c.a=null;c.w=Math.max(1,Math.round(bm.width*k));c.h=Math.max(1,Math.round(bm.height*k));
      c.cv=document.createElement('canvas');c.cv.width=c.w;c.cv.height=c.h;
      c.x=c.cv.getContext('2d');c.x.drawImage(bm,0,0,c.w,c.h);bm.close();
    }catch{BF_BZ(c,0);c.st('Error Imagen (formato no soportado)');return}
    try{
      c.st('Preparando modelo...');
      let r;
      try{r=await BF_RN(c,m[0],d,dv)}
      catch(e){if(!au||dv!=='webgpu')throw e;dv='wasm';d=BF_RD(m[4],0);c.st('WebGPU fallo, probando con WASM...');r=await BF_RN(c,m[0],d,dv)}
      c.a=r.a;c.i=`${m[1]} ${d} · ${dv==='webgpu'?'WebGPU':'WASM'} · ${(r.ms/1000).toFixed(1)} s`;
    }catch(e){c.st('Error Modelo '+(e&&e.message||'').slice(0,160))}
    BF_BZ(c,0);
    if(c.a&&BF_C.includes(c))await BF_R1(c);
  });
}
async function BF_R1(c){
  if(!c.a||c.bz)return;
  const g=++c.g,w=c.w,h=c.h,u=Math.round(+$('bf-u').value*2.55),sv=+$('bf-sv').value,bg=$('bf-bg').value,ty=$('bf-f').value;
  const id=new ImageData(w,h),D=id.data,A=c.a;
  for(let i=0;i<A.length;i++)D[i*4+3]=u?(A[i]>=u?255:0):A[i];
  let x0=0,y0=0,cw=w,ch=h;
  if($('bf-rc').checked){
    const t=u||128;let a=w,b=h,e=-1,f=-1;
    for(let y=0;y<h;y++)for(let x=0;x<w;x++)if(A[y*w+x]>=t){if(x<a)a=x;if(x>e)e=x;if(y<b)b=y;if(y>f)f=y}
    if(e>=0){const p=Math.round(Math.max(e-a,f-b)*.02)+sv*2;x0=Math.max(0,a-p);y0=Math.max(0,b-p);cw=Math.min(w,e+p+1)-x0;ch=Math.min(h,f+p+1)-y0}
  }
  const mk=document.createElement('canvas');mk.width=w;mk.height=h;mk.getContext('2d').putImageData(id,0,0);
  const o=document.createElement('canvas');o.width=cw;o.height=ch;
  const x=o.getContext('2d');
  if(sv)x.filter=`blur(${sv}px)`;
  x.drawImage(mk,-x0,-y0);x.filter='none';
  x.globalCompositeOperation='source-in';x.drawImage(c.cv,-x0,-y0);
  x.globalCompositeOperation='destination-over';
  if(bg==='b'){x.filter=`blur(${Math.max(4,Math.round(Math.max(w,h)/80))}px)`;x.drawImage(c.cv,-x0,-y0);x.filter='none';x.drawImage(c.cv,-x0,-y0)}
  else if(bg==='c'||ty==='image/jpeg'){x.fillStyle=bg==='c'?$('bf-cl').value:'#ffffff';x.fillRect(0,0,cw,ch)}
  const b=await new Promise(r=>o.toBlob(r,ty,+$('bf-q').value/100));
  o.width=o.height=mk.width=mk.height=0;
  if(g!==c.g||!b||c.bz||!BF_C.includes(c))return;
  if(c.ru)URL.revokeObjectURL(c.ru);
  c.ru=URL.createObjectURL(b);c.b=b;c.nm=c.f.name.replace(/\.[^.]+$/,'')+'-sin-fondo.'+(ty.split('/')[1]==='jpeg'?'jpg':ty.split('/')[1]);
  c.im.src=c.ru;
  c.st(`${c.i} · ${cw}x${ch} · ${BF_SZ(b.size)}`);
  if(!c.v){
    BF_B(c.ac,'⬇️',()=>BF_DL(c),'Descargar');
    c.v=BF_B(c.ac,'👁️',()=>{const on=c.im.src===c.fu;c.im.src=on?c.ru:c.fu;c.v.textContent=on?'👁️':'✨'},'Ver original');
    if(navigator.share)BF_B(c.ac,'📤',()=>{const f=new File([c.b],c.nm,{type:c.b.type});if(navigator.canShare?.({files:[f]}))navigator.share({files:[f]}).catch(()=>{})},'Compartir');
    c.ac.append(c.xb);
  }
  c.v.textContent='👁️';
}
function BF_DL(c){const a=document.createElement('a');a.href=c.ru;a.download=c.nm;a.click()}
async function BF_RA(){for(const c of BF_C)if(c.a)await BF_R1(c)}
function BF_X(c){
  BF_C=BF_C.filter(k=>k!==c);c.g++;
  if(c.cv)c.cv.width=0;
  URL.revokeObjectURL(c.fu);if(c.ru)URL.revokeObjectURL(c.ru);
  c.e.remove();BF_AC();
}
function BF_AC(){
  const ac=$('bf-ac');ac.textContent='';
  if(!BF_C.length)return;
  BF_B(ac,'🔄 Procesar de nuevo',()=>BF_C.forEach(BF_P1),'Con el modelo elegido');
  BF_B(ac,'⬇️ Descargar todas',async()=>{for(const c of BF_C)if(c.b){BF_DL(c);await new Promise(r=>setTimeout(r,300))}});
  if(navigator.share)BF_B(ac,'📤 Compartir todas',()=>{const f=BF_C.filter(c=>c.b).map(c=>new File([c.b],c.nm,{type:c.b.type}));if(f.length&&navigator.canShare?.({files:f}))navigator.share({files:f}).catch(()=>{})});
}
function BF_A1(f){
  const e=document.createElement('div');e.className='bf-cd';
  const im=document.createElement('img');im.className='bf-im';im.alt='';
  const iw=document.createElement('div');iw.className='bf-iw';iw.append(im);
  const n=document.createElement('div');n.className='bf-nm';n.textContent=f.name;
  const s=document.createElement('div');s.className='bf-ms';
  const ac=document.createElement('div');ac.className='bf-ac';
  e.append(iw,n,s,ac);$('bf-ls').prepend(e);
  const c={e,im,iw,ac,f,g:0,fu:URL.createObjectURL(f),st:t=>{s.textContent=t}};
  im.src=c.fu;
  c.xb=BF_B(ac,'✖️',()=>BF_X(c),'Quitar');
  BF_C.push(c);BF_AC();BF_P1(c);
}
async function BF_GL(){
  const l=$('bf-gl');l.textContent='Calculando...';
  try{
    const ca=await caches.open('transformers-cache'),T={};
    for(const q of await ca.keys()){
      const m=BF_M.find(k=>q.url.includes('/'+k[0]+'/'));if(!m)continue;
      const r=await ca.match(q),t=T[m[0]]??={n:m[1],s:0,q:[]};
      t.s+=+r?.headers.get('content-length')||(r?(await r.blob()).size:0);t.q.push(q);
    }
    const v=Object.values(T);l.textContent=v.length?'':'Ningun modelo guardado.';
    for(const t of v){const d=document.createElement('div');d.textContent=`${t.n} · ${BF_SZ(t.s)} `;BF_B(d,'🗑️',async()=>{for(const q of t.q)await ca.delete(q);BF_GL()},'Borrar');l.append(d)}
  }catch{l.textContent='Error Cache'}
}
const BF_F=fl=>{for(const f of fl)if(/^image\//.test(f.type)||/\.(jpe?g|png|webp|avif|gif|bmp|heic)$/i.test(f.name))BF_A1(f)};
$('bf-m').replaceChildren(...BF_M.map(m=>new Option(`${m[1]} (${m[2]})`,m[0])));
for(const k of BF_K){const e=$(k),v=BF_PR[k];if(v==null||k==='bf-d')continue;if(e.type==='checkbox')e.checked=v;else if(e.tagName!=='SELECT'||[...e.options].some(o=>o.value===v))e.value=v}
const BF_UI=()=>{const u=+$('bf-u').value;$('bf-uv').textContent=u?u+'%':'Suave';$('bf-svv').textContent=$('bf-sv').value;$('bf-qv').textContent=$('bf-q').value;$('bf-cl').hidden=$('bf-bg').value!=='c';$('bf-ql').hidden=$('bf-f').value==='image/png'};
BF_UI();BF_EQ();BF_DS(BF_PR['bf-d']);
['bf-m','bf-dv'].forEach(i=>$(i).addEventListener('change',()=>BF_DS()));
['bf-bg','bf-cl','bf-u','bf-sv','bf-rc','bf-f','bf-q'].forEach(i=>$(i).addEventListener('change',BF_RA));
['bf-u','bf-sv','bf-q','bf-bg','bf-f'].forEach(i=>['input','change'].forEach(t=>$(i).addEventListener(t,BF_UI)));
BF_K.forEach(i=>$(i).addEventListener('change',BF_SV));
$('bf-gd').ontoggle=e=>{if(e.target.open)BF_GL()};
const dz=$('bf-dz');
$('bf-fi').onchange=e=>{BF_F(e.target.files);e.target.value=''};
dz.ondragover=e=>{e.preventDefault();dz.classList.add('on')};
dz.ondragleave=()=>dz.classList.remove('on');
dz.ondrop=e=>{e.preventDefault();dz.classList.remove('on');BF_F(e.dataTransfer.files)};
document.addEventListener('contentUnload',()=>{BF_W?.terminate();BF_W=null;for(const c of BF_C){c.g++;URL.revokeObjectURL(c.fu);if(c.ru)URL.revokeObjectURL(c.ru);if(c.cv)c.cv.width=0}BF_C=[]},{once:true});
(async()=>{
  try{const a=await navigator.gpu?.requestAdapter();BF_GA=!!a;BF_F16=!!a?.features.has('shader-f16')}catch{}
  $('bf-dv').options[1].disabled=!BF_GA;
  if(!BF_GA&&$('bf-dv').value==='webgpu')$('bf-dv').value='auto';
  BF_EQ();BF_DS(BF_PR['bf-d']);
})();
(async()=>{
  try{
    const C={cacheName:'share-pending'},r=await caches.match('/__share_data',C);
    if(!r||Date.now()>+r.headers.get('X-Expires'))return;
    const b=(await r.json()).files.filter(x=>/^image\//.test(x.type));
    if(!b.length)return;
    const f=await Promise.all(b.map(async x=>new File([await(await caches.match(x.key,C)).blob()],x.name||'foto.jpg',{type:x.type})));
    await caches.delete('share-pending');
    BF_F(f);
  }catch{}
})();
})();
</script>

</div>
