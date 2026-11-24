<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.cj-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 6px}
.cj-nt{color:rgba(255,255,255,.45);font-size:.8em;max-width:440px;margin:0 auto 16px;line-height:1.5}
.cj-dz{display:block;max-width:420px;margin:0 auto 12px;padding:22px 16px;border:2px dashed rgba(255,255,255,.2);border-radius:16px;cursor:pointer;color:rgba(255,255,255,.7);transition:border-color .2s,background .2s}
.cj-dz.on{border-color:rgba(56,189,248,.6);background:rgba(56,189,248,.06)}
.cj-op{display:flex;gap:12px;justify-content:center;align-items:center;flex-wrap:wrap;max-width:520px;margin:0 auto 12px;color:rgba(255,255,255,.75);font-size:.85em}
.cj-op select,.cj-op input[type=number]{background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);border-radius:8px;color:#fff;padding:4px 6px;font-family:inherit}
.cj-op input[type=number]{width:70px}
.cj-ac{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;margin:0 auto 10px}
.cj-ac:empty{display:none}
.cj-cd{display:flex;gap:12px;align-items:center;border-radius:14px;padding:10px 12px;margin:8px auto;max-width:560px;text-align:left;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06)}
.cj-cd img.cj-tb{width:64px;height:64px;object-fit:cover;border-radius:8px;flex:0 0 64px;background:#111}
.cj-in{flex:1;min-width:0;font-size:.82em;color:rgba(255,255,255,.6);line-height:1.5}
.cj-in b{display:block;color:#fff;font-size:1.05em;word-break:break-all}
.cj-ok{color:var(--ok)}
.cj-up{color:var(--warn)}
.cj-cd a{flex:0 0 auto;font-size:1.4em;text-decoration:none}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🗜️</div>
<div class="cj-st">Comprimir Fotos a JPG</div>
<div class="cj-nt">Achica fotos para WhatsApp y convierte cualquier imagen (PNG, WebP, AVIF) a JPG. Tambien borra los datos ocultos como la ubicacion GPS. Nada se sube.</div>
<label class="cj-dz" id="cj-dz">🖼️ Toca o arrastra fotos aca<input type="file" id="cj-in" accept="image/*" multiple hidden></label>
<div class="cj-op">
  <label>Tamano <select id="cj-mx"><option value="1280">1280 px</option><option value="1600" selected>1600 px</option><option value="2048">2048 px</option><option value="0">Original</option></select></label>
  <label>Calidad <input type="range" id="cj-q" min="40" max="95" value="80"> <span id="cj-qv">80</span></label>
  <label><input type="checkbox" id="cj-lk"> Max <input type="number" id="cj-kb" value="300" min="20" step="10"> KB</label>
</div>
<div class="cj-ac" id="cj-ac"></div>
<div id="cj-ls"></div>

<script>
(function(){
const $=i=>document.getElementById(i);
let CJ_O=[],CJ_U=[],CJ_R=[],CJ_G=0;
const CJ_SZ=n=>n<1048576?Math.round(n/1024)+' KB':(n/1048576).toFixed(1)+' MB';
const CJ_BL=(c,q)=>new Promise(r=>c.toBlob(r,'image/jpeg',q));
async function CJ_C1(f){
  const bm=await createImageBitmap(f);
  const mx=+$('cj-mx').value,ow=bm.width,oh=bm.height,c=document.createElement('canvas');
  let k=mx?Math.min(1,mx/Math.max(ow,oh)):1,q,b;
  const lim=$('cj-lk').checked?+$('cj-kb').value*1024:0;
  for(let n=0;n<6;n++,k*=.8){
    c.width=Math.max(1,Math.round(ow*k));c.height=Math.max(1,Math.round(oh*k));
    const x=c.getContext('2d');x.fillStyle='#fff';x.fillRect(0,0,c.width,c.height);x.imageSmoothingQuality='high';x.drawImage(bm,0,0,c.width,c.height);
    q=+$('cj-q').value/100;b=await CJ_BL(c,q);
    if(!lim||b.size<=lim)break;
    let lo=.1,hi=q,ok=null;
    for(let i=0;i<7;i++){const m=(lo+hi)/2,t=await CJ_BL(c,m);if(t.size<=lim){ok=[t,m];lo=m}else hi=m}
    if(!ok){const t=await CJ_BL(c,.1);if(t.size<=lim)ok=[t,.1]}
    if(ok){[b,q]=ok;break}
  }
  bm.close();
  const w=c.width,h=c.height;c.width=c.height=0;
  return{b,q,ow,oh,w,h};
}
async function CJ_P(){
  const g=++CJ_G;
  CJ_U.forEach(u=>URL.revokeObjectURL(u));CJ_U=[];CJ_R=[];
  $('cj-ls').textContent='';$('cj-ac').textContent='';
  for(const f of CJ_O){
    const d=document.createElement('div');d.className='cj-cd';
    const i=document.createElement('div');i.className='cj-in';
    const n=document.createElement('b');n.textContent=f.name;i.append(n,'Comprimiendo...');
    d.append(i);$('cj-ls').append(d);
    try{
      const r=await CJ_C1(f);
      if(g!==CJ_G)return;
      const nm=f.name.replace(/\.[^.]+$/,'')+'.jpg',u=URL.createObjectURL(r.b);CJ_U.push(u);
      CJ_R.push(new File([r.b],nm,{type:'image/jpeg'}));
      const t=document.createElement('img');t.className='cj-tb';t.src=u;t.alt='';d.prepend(t);
      i.textContent='';const n2=document.createElement('b');n2.textContent=nm;
      const s=document.createElement('span');s.className=r.b.size<f.size?'cj-ok':'cj-up';s.textContent=` ${r.b.size<f.size?'-'+Math.round((1-r.b.size/f.size)*100)+'%':'+'+Math.round((r.b.size/f.size-1)*100)+'%'}`;
      i.append(n2,`${CJ_SZ(f.size)} → ${CJ_SZ(r.b.size)}`,s,document.createElement('br'),`${r.ow}x${r.oh} → ${r.w}x${r.h} · calidad ${Math.round(r.q*100)}`);
      const a=document.createElement('a');a.href=u;a.download=nm;a.textContent='⬇️';a.title='Descargar';d.append(a);
    }catch{if(g===CJ_G)i.lastChild.textContent='Error Imagen (formato no soportado)'}
  }
  if(g!==CJ_G||!CJ_R.length)return;
  const ac=$('cj-ac');
  if(navigator.canShare?.({files:CJ_R})){const b=document.createElement('button');b.textContent='📤 Compartir '+(CJ_R.length>1?'todas':'');b.onclick=()=>navigator.share({files:CJ_R}).catch(()=>{});ac.append(b)}
  const b=document.createElement('button');b.textContent='⬇️ Descargar '+(CJ_R.length>1?'todas':'');
  b.onclick=async()=>{for(const a of $('cj-ls').querySelectorAll('a[download]')){a.click();await new Promise(r=>setTimeout(r,300))}};ac.append(b);
}
const CJ_F=fl=>{const a=[...fl].filter(f=>/^image\//.test(f.type)||/\.(jpe?g|png|webp|avif|gif|bmp|heic)$/i.test(f.name));if(a.length){CJ_O=CJ_O.concat(a);CJ_P()}};
const dz=$('cj-dz');
$('cj-in').onchange=e=>{CJ_F(e.target.files);e.target.value=''};
dz.ondragover=e=>{e.preventDefault();dz.classList.add('on')};
dz.ondragleave=()=>dz.classList.remove('on');
dz.ondrop=e=>{e.preventDefault();dz.classList.remove('on');CJ_F(e.dataTransfer.files)};
$('cj-q').oninput=e=>{$('cj-qv').textContent=e.target.value};
['cj-mx','cj-q','cj-lk','cj-kb'].forEach(i=>$(i).addEventListener('change',()=>CJ_O.length&&CJ_P()));
document.addEventListener('contentUnload',()=>{CJ_G++;CJ_U.forEach(u=>URL.revokeObjectURL(u));CJ_U=[]},{once:true});
(async()=>{
  try{
    const C={cacheName:'share-pending'},r=await caches.match('/__share_data',C);
    if(!r||Date.now()>+r.headers.get('X-Expires'))return;
    const b=(await r.json()).files.filter(x=>/^image\//.test(x.type));
    if(!b.length)return;
    const f=await Promise.all(b.map(async x=>new File([await(await caches.match(x.key,C)).blob()],x.name||'foto.jpg',{type:x.type})));
    await caches.delete('share-pending');
    CJ_F(f);
  }catch{}
})();
})();
</script>

</div>
