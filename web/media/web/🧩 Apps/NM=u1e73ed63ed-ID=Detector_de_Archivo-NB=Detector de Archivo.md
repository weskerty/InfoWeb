<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.da-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 6px}
.da-nt{color:rgba(255,255,255,.45);font-size:.8em;max-width:420px;margin:0 auto 16px;line-height:1.5}
.da-dz{display:block;max-width:420px;margin:0 auto 14px;padding:26px 16px;border:2px dashed rgba(255,255,255,.2);border-radius:16px;cursor:pointer;color:rgba(255,255,255,.7);transition:border-color .2s,background .2s}
.da-dz.on{border-color:rgba(56,189,248,.6);background:rgba(56,189,248,.06)}
.da-cd{border-radius:14px;padding:14px 16px;margin:10px auto;max-width:520px;text-align:left;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06)}
.da-cd.wr{border-color:rgba(251,191,36,.5)}
.da-nm{font-weight:700;color:#fff;word-break:break-all;margin-bottom:6px}
.da-av{color:var(--warn);font-size:.85em}
.da-av:empty{display:none}
.da-h{font-size:.72em;letter-spacing:.08em;color:rgba(255,255,255,.45);margin:12px 0 4px;text-transform:uppercase}
.da-r{display:flex;gap:10px;font-size:.85em;line-height:1.5}
.da-r b{flex:0 0 105px;color:rgba(255,255,255,.55);font-weight:500}
.da-r span{color:#fff;word-break:break-word;min-width:0}
.da-mono{font-family:monospace;font-size:.9em;word-break:break-all!important;user-select:all}
.da-cd .wait-anim{width:40px;height:40px}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🔎</div>
<div class="da-st">Detector de Archivo</div>
<div class="da-nt">Descubre que es realmente un archivo, sin importar su nombre o extension. Nada se sube: todo pasa en tu dispositivo.</div>
<label class="da-dz" id="da-dz">📂 Toca o arrastra archivos aca<input type="file" id="da-in" multiple hidden></label>
<div id="da-ls"></div>

<script>
(function(){
const $=i=>document.getElementById(i);
const WMV='https://cdn.jsdelivr.net/npm/wasmagic@1.0.12/',MAX=32*1048576,HMAX=200*1048576,WA=window.__CFG?.waitAnim||'';
const DA_LZ=f=>{let p=null;return()=>p||(p=f().catch(e=>{p=null;throw e}))};
const DA_W1=DA_LZ(async()=>{
  const{WASMagic:W}=await import(WMV+'+esm');
  const[d,m,x]=await Promise.all([32,1040,16777216].map(flags=>W.create({locateFile:f=>WMV+'dist/'+f,flags})));
  return{d,m,x};
});
const DA_M1=DA_LZ(async()=>(await import('https://cdn.jsdelivr.net/npm/magika@1.0.0/+esm')).Magika.create());
const DA_SZ=n=>{const u=['B','KB','MB','GB'];let i=0;while(n>=1024&&i<3){n/=1024;i++}return(i?n.toFixed(1):n)+' '+u[i]};
const DA_HX=a=>[...a].map(x=>x.toString(16).padStart(2,'0'));
function DA_H(c,t){const h=document.createElement('div');h.className='da-h';h.textContent=t;c.append(h)}
function DA_R(c,k,v,mn){
  const r=document.createElement('div');r.className='da-r';
  const b=document.createElement('b');b.textContent=k;
  const s=document.createElement('span');s.textContent=v;if(mn)s.className='da-mono';
  r.append(b,s);c.append(r);
}
async function DA_A1(f){
  const c=document.createElement('div');c.className='da-cd';
  const n=document.createElement('div');n.className='da-nm';n.textContent=f.name;
  const av=document.createElement('div');av.className='da-av';av.textContent='Analizando...';
  c.append(n,av);$('da-ls').prepend(c);
  const ext=((f.name.match(/\.([^.]+)$/)||[])[1]||'').toLowerCase();
  DA_M1().catch(()=>{});
  try{
    const b=new Uint8Array(await f.slice(0,MAX).arrayBuffer());
    const E=await DA_W1();
    const ds=E.d.detect(b).split('\\012- ').map(t=>t.trim()).filter(Boolean).reduce((a,t)=>(t[0]===','&&a.length?a[a.length-1]+=t:a.push(t),a),[]).filter((t,i,a)=>t!=='data'||a.length===1);
    const xs=E.x.detect(b);
    DA_H(c,'Archivo');
    DA_R(c,'Tamano',`${DA_SZ(f.size)} (${f.size.toLocaleString('es-PY')} bytes)`);
    DA_R(c,'Extension',ext?'.'+ext:'(sin extension)');
    DA_R(c,'Segun nombre',f.type||'(desconocido)');
    if(f.lastModified)DA_R(c,'Modificado',new Date(f.lastModified).toLocaleString('es-PY'));
    DA_H(c,'libmagic (comando file)');
    ds.forEach((t,i)=>DA_R(c,i?'Tambien':'Tipo',t));
    DA_R(c,'MIME',E.m.detect(b));
    if(xs&&xs!=='???')DA_R(c,'Extensiones',xs.split('/').map(e=>'.'+e).join(' '));
    DA_H(c,'Magika (IA de Google)');
    const mb=document.createElement('div');
    if(WA){const w=document.createElement('img');w.className='wait-anim';w.src=WA;w.alt='';mb.append(w)}
    c.append(mb);
    DA_H(c,'Bytes');
    DA_R(c,'Inicio (hex)',DA_HX(b.slice(0,32)).join(' '),1);
    if(f.size<=HMAX){
      const h=DA_HX(new Uint8Array(await crypto.subtle.digest('SHA-256',await f.arrayBuffer()))).join('');
      DA_R(c,'SHA-256',h,1);
      const a=document.createElement('a');a.className='view-all-button';a.href='https://www.virustotal.com/gui/file/'+h;a.target='_blank';a.rel='noopener noreferrer';a.textContent='🛡️ Buscar virus en VirusTotal';
      c.append(a);
    }
    av.textContent='';
    await new Promise(r=>setTimeout(r,50));
    let p=null;
    try{p=(await(await DA_M1()).identifyBytes(b)).prediction}catch{}
    mb.textContent='';
    if(p){
      DA_R(mb,'Tipo',p.output.label);
      DA_R(mb,'Confianza',Math.round(p.score*100)+'%');
      DA_R(mb,'Contenido',p.output.is_text?'Texto':'Binario');
      if(p.dl?.label&&p.dl.label!=='undefined'&&p.dl.label!==p.output.label)DA_R(mb,'Modelo crudo',p.dl.label);
      const o=Object.entries(p.scores_map||{}).sort((a,z)=>z[1]-a[1]).slice(1,4).filter(e=>e[1]>=.01);
      if(o.length)DA_R(mb,'Alternativas',o.map(([k,v])=>`${k} ${Math.round(v*100)}%`).join(', '));
    }else DA_R(mb,'Tipo','Error Magika');
    if(ext&&xs&&xs!=='???'&&!xs.split('/').includes(ext)&&p?.output.label!==ext){c.classList.add('wr');av.textContent=`⚠️ El contenido no coincide con la extension .${ext}`}
  }catch(e){av.textContent='Error Detector '+(e&&e.name||'')}
}
const DA_F=fl=>{for(const f of fl)DA_A1(f)};
const dz=$('da-dz');
$('da-in').onchange=e=>{DA_F(e.target.files);e.target.value=''};
dz.ondragover=e=>{e.preventDefault();dz.classList.add('on')};
dz.ondragleave=()=>dz.classList.remove('on');
dz.ondrop=e=>{e.preventDefault();dz.classList.remove('on');DA_F(e.dataTransfer.files)};
(async()=>{
  try{
    const d=await fetch('/_share_pending').then(r=>r.json());
    if(!d?.blobs?.length)return;
    await fetch('/_share_clear',{method:'POST'});
    DA_F(d.blobs.map(b=>new File([new Uint8Array(b.data)],b.name||'archivo',{type:b.type||''})));
  }catch{}
})();
})();
</script>

</div>
