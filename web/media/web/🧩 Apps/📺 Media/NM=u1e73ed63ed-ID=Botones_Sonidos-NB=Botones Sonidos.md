<div style="text-align:center;position:relative;padding-top:0;margin-top:0" id="sb-app">
<style>
.SB0{font-size:2.8rem;line-height:1.2;margin:0 auto 4px}
.SB1{width:38px;height:38px;object-fit:cover;border-radius:9px;display:block;margin:0 auto;background:rgba(255,255,255,.07)}
.SB2{max-width:56px;overflow:hidden;text-overflow:ellipsis}
.SB3{position:fixed;left:50%;bottom:86px;transform:translateX(-50%);background:rgba(20,20,24,.95);border:1px solid rgba(255,255,255,.15);border-radius:999px;padding:8px 18px;z-index:10000;pointer-events:none;opacity:0;transition:opacity .2s}
.SB3.on{opacity:1}
.SB4{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:6px 0 16px}
.SB5{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.09);border-radius:var(--r-md);padding:14px;margin:0 0 14px;color:rgba(255,255,255,.7)}
.SB6{color:rgba(255,255,255,.5);font-size:.9em;margin:14px 0}
.SB7{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0}
.SB8{width:100%;max-width:150px;border-radius:var(--r-sm);margin:8px auto 0;display:none}
.SB9{font-size:.82rem;color:rgba(255,255,255,.55);margin:2px 0 0;word-break:break-word}
#sb-dlg label{display:block;text-align:left;font-size:.72rem;color:rgba(255,255,255,.55);letter-spacing:.03em;margin:10px 0 3px}
#sb-dlg input{width:100%;box-sizing:border-box}
#sb-dlg{max-width:380px;width:calc(100% - 28px)}
</style>
<div class="SB0">🔊</div>
<div class="SB4">Botones de Sonido</div>
<div id="sb-nos" class="SB5" style="display:none">Tu navegador no soporta el Sistema de Archivos Privado. La app no puede guardar.</div>
<div class="BS1" id="sb-list"></div>
<p class="SB6" id="sb-msg"></p>
<div class="SB7"><button id="sb-stop">⏹️ Parar todo</button></div>
<input type="file" id="sb-file" accept="audio/*" multiple style="display:none">
<dialog id="sb-dlg">
<h3 style="margin:0">Nuevo boton</h3>
<p class="SB9" id="sb-fi"></p>
<label for="sb-nb">Nombre</label>
<input id="sb-nb" maxlength="20" autocomplete="off" spellcheck="false">
<label for="sb-emo">Emoji (si no pones imagen)</label>
<input id="sb-emo" maxlength="8" autocomplete="off" placeholder="🔊">
<label for="sb-img">Imagen (opcional)</label>
<input type="file" id="sb-img" accept="image/*">
<img class="SB8" id="sb-prev" alt="">
<div class="SB7"><button id="sb-save">💾 Guardar</button><button id="sb-cancel">Cancelar</button></div>
</dialog>
<div class="SB3" id="sb-toast"></div>

<script>
(function(){
const $=i=>document.getElementById(i);
const L=$('sb-list'),MSG=$('sb-msg'),DLG=$('sb-dlg'),TST=$('sb-toast'),FI=$('sb-file');
const IMW=256,IMX=50*1024,QL=[.85,.7,.55,.4,.28,.18,.1],MXB=20*1024*1024;
const HAS=typeof navigator.storage?.getDirectory==='function'&&typeof FileSystemFileHandle?.prototype?.createWritable==='function';
let IT=[],QQ=[],PB=null,TT=null;

function tst(m){TST.textContent=m;TST.classList.add('on');clearTimeout(TT);TT=setTimeout(()=>TST.classList.remove('on'),2200)}
function nm(s){return String(s==null?'':s).replace(/[^\p{L}\p{N} .,\-_!?]/gu,'').replace(/\s+/g,' ').trim().slice(0,20)}
function emo(){return Array.from(String($('sb-emo').value||'').replace(/\p{C}/gu,'')).slice(0,3).join('')}

async function dir(){
  const r=await navigator.storage.getDirectory();
  const a=await r.getDirectoryHandle('Apps',{create:true});
  return a.getDirectoryHandle('BotonesSonidos',{create:true});
}
async function load(){
  if(!HAS)return;
  try{
    const f=await (await (await dir()).getFileHandle('items.json')).getFile();
    const j=JSON.parse(await f.text());
    if(Array.isArray(j.items))IT=j.items.filter(x=>x&&typeof x.id==='string'&&typeof x.nb==='string').map(x=>({
      id:x.id,nb:nm(x.nb),mime:typeof x.mime==='string'?x.mime:'',
      emo:String(x.emo||'').replace(/\p{C}/gu,'').slice(0,8),
      img:typeof x.img==='string'&&x.img.startsWith('data:image/webp;')?x.img:''}));
  }catch(e){}
}
async function save(){
  if(!HAS)return;
  try{
    const h=await (await dir()).getFileHandle('items.json',{create:true});
    const w=await h.createWritable();
    await w.write(JSON.stringify({v:1,items:IT.map(x=>({id:x.id,nb:x.nb,mime:x.mime,emo:x.emo,img:x.img}))}));
    await w.close();
  }catch(e){tst('Error al guardar')}
}
async function wr(id,b){
  const h=await (await dir()).getFileHandle('s-'+id,{create:true});
  const w=await h.createWritable();
  await w.write(b);
  await w.close();
}

function chk(b){
  return new Promise(ok=>{
    const u=URL.createObjectURL(b),a=new Audio();
    let d=false;
    const fin=v=>{if(d)return;d=true;URL.revokeObjectURL(u);ok(v)};
    a.onloadedmetadata=()=>fin(true);
    a.onerror=()=>fin(false);
    setTimeout(()=>fin(false),8000);
    a.src=u;
  });
}
async function shrink(file){
  const b=await createImageBitmap(file);
  const c=document.createElement('canvas');c.width=c.height=IMW;
  c.getContext('2d').drawImage(b,0,0,IMW,IMW);
  b.close();
  let d='';
  for(const q of QL){
    d=c.toDataURL('image/webp',q);
    if(d.length*.75<IMX)return d;
  }
  return d;
}

async function play(x){
  try{
    if(!x._a){
      const f=await (await (await dir()).getFileHandle('s-'+x.id)).getFile();
      x._u=URL.createObjectURL(f.slice(0,f.size,x.mime||'audio/mpeg'));
      x._a=new Audio(x._u);
    }
    x._a.currentTime=0;
    await x._a.play();
  }catch(e){tst('No se pudo reproducir '+x.nb)}
}
function stopAll(){IT.forEach(x=>{if(x._a){x._a.pause();x._a.currentTime=0}})}

function tile(ic,txt,img){
  const b=document.createElement('button');b.className='BS2';b.title=txt;
  const c=document.createElement('span');c.className='BS3';
  if(img){const m=document.createElement('img');m.className='SB1';m.src=img;m.alt='';c.appendChild(m)}
  else{const e=document.createElement('span');e.className='BS4';e.textContent=ic;c.appendChild(e)}
  const p=document.createElement('p');p.className='BS5 SB2';p.textContent=txt;
  c.appendChild(p);b.appendChild(c);
  return b;
}
function rL(){
  L.innerHTML='';
  const a=tile('➕','Agregar','');
  a.onclick=()=>FI.click();
  L.appendChild(a);
  IT.forEach(x=>{
    const t=tile(x.emo||'🔊',x.nb,x.img);
    t.onclick=()=>play(x);
    L.appendChild(t);
  });
  MSG.textContent=IT.length?'':'Todavia no hay botones. Toca Agregar y elegi un audio.';
}

function op(b,n){
  PB=b;
  $('sb-nb').value=nm(String(n||'').replace(/\.[a-z0-9]{1,8}$/i,''));
  $('sb-emo').value='';
  $('sb-img').value='';
  const p=$('sb-prev');p.removeAttribute('src');p.style.display='none';
  $('sb-fi').textContent=(n||'audio')+'  ·  '+Math.round(b.size/1024)+' KB';
  if(!DLG.open)DLG.showModal();
  $('sb-nb').focus();
}
function nxt(){if(QQ.length)op(QQ[0].b,QQ[0].n)}

async function take(b,n){
  if(!b)return false;
  if(b.size>MXB){tst('Audio muy pesado: '+n);return false}
  if(!await chk(b)){tst('No es un audio valido: '+n);return false}
  return true;
}
FI.onchange=async function(){
  const fs=Array.from(this.files||[]);this.value='';
  if(!fs.length)return;
  const q=[];
  for(const f of fs)if(await take(f,f.name))q.push({b:f,n:f.name});
  if(!q.length)return;
  QQ=QQ.concat(q);nxt();
};
$('sb-img').onchange=async function(){
  const f=this.files&&this.files[0];this.value='';
  if(!f)return;
  try{
    const d=await shrink(f);
    const p=$('sb-prev');p.src=d;p.style.display='';
    tst('Imagen lista: '+Math.round(d.length*.75/1024)+' KB');
  }catch(e){tst('No se pudo leer la imagen')}
};
$('sb-nb').oninput=function(){const v=nm(this.value);if(v!==this.value)this.value=v};
$('sb-emo').oninput=function(){const v=emo();if(v!==this.value)this.value=v};
$('sb-stop').onclick=stopAll;
$('sb-cancel').onclick=()=>{QQ.shift();DLG.close();if(QQ.length)setTimeout(nxt,150)};
DLG.addEventListener('close',()=>{PB=null});
$('sb-save').onclick=async()=>{
  const nb=nm($('sb-nb').value);
  if(!nb){tst('Falta el nombre');return}
  if(!PB){tst('Falta el audio');return}
  if(!HAS){tst('Este navegador no puede guardar');return}
  const b=PB,id='s'+Date.now().toString(36)+Math.random().toString(36).slice(2,6);
  const p=$('sb-prev');
  const img=p.style.display==='none'?'':(p.getAttribute('src')||'');
  try{await wr(id,b)}catch(e){tst('Error al guardar');return}
  IT.push({id:id,nb:nb,mime:b.type||'audio/mpeg',emo:emo(),img:img});
  QQ.shift();
  DLG.close();rL();tst('Agregado: '+nb);
  await save();
  if(QQ.length)setTimeout(nxt,150);
};

async function shr(){
  if(!window.caches)return;
  try{
    const c=await caches.open('share-pending');
    const m=await c.match('__share_data');
    if(!m)return;
    const exp=parseInt(m.headers.get('X-Expires')||0);
    if(exp&&Date.now()>exp)return;
    const j=await m.json();
    if(!j||!j.files||!j.files.length)return;
    const q=[];
    for(const f of j.files){
      if(!/^audio\//.test(f.type||''))continue;
      const r=await c.match(f.key);
      if(!r)continue;
      const rb=await r.blob(),b=rb.slice(0,rb.size,f.type);
      const n=f.name||'audio';
      if(await take(b,n))q.push({b:b,n:n});
    }
    if(!q.length)return;
    await fetch('/_share_clear',{method:'POST'}).catch(()=>{});
    await caches.delete('share-pending').catch(()=>{});
    QQ=QQ.concat(q);nxt();
  }catch(e){}
}

if(!HAS)$('sb-nos').style.display='';
if(navigator.storage&&navigator.storage.persist)navigator.storage.persist().catch(()=>{});
load().then(()=>{rL();return shr()});

document.addEventListener('contentUnload',function td(){
  clearTimeout(TT);
  IT.forEach(x=>{if(x._a){x._a.pause();x._a.src=''}if(x._u)URL.revokeObjectURL(x._u)});
  QQ=[];PB=null;
},{once:true});
})();
</script>

<br><br>
<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>
</div>
