<style>
#SB_W *{box-sizing:border-box}
.SB_NB{position:absolute;top:0;font-size:1.8rem;text-decoration:none;z-index:10}
.SB_NBL{left:0}
.SB_HD{margin-bottom:clamp(16px,3vw,32px)}
.SB_HD h2{font-size:clamp(1.6rem,5vw,2.8rem);font-weight:700;color:rgba(255,255,255,.95);letter-spacing:-.02em;border-bottom:2px solid #1a73e8;padding-bottom:.5rem;display:inline-block}
.SB_BR{display:flex;justify-content:center;margin-top:10px}
#SB_AB{padding:8px 18px;border-radius:20px;border:1px solid rgba(120,200,255,.35);background:rgba(120,200,255,.1);color:#9fd8ff;font-size:.8rem;letter-spacing:.05em;cursor:pointer;transition:background .2s,transform .15s}
#SB_AB:hover{background:rgba(120,200,255,.2);transform:translateY(-1px)}
.SB_FRM{display:none;flex-direction:column;gap:8px;margin:14px auto 0;max-width:520px;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);border-radius:16px;padding:14px;backdrop-filter:blur(10px)}
.SB_FRM textarea{resize:vertical;min-height:70px;max-height:220px;border-radius:10px;border:1px solid rgba(255,255,255,.18);background:rgba(0,0,0,.2);color:#fff;padding:10px;font-size:.9rem;font-family:inherit}
.SB_CNT{font-size:.7rem;color:rgba(255,255,255,.4);text-align:right}
.SB_LIMIT{font-size:.75rem;color:#ff9f9f;text-align:right;margin-top:4px}
.SB_FBR{display:flex;gap:8px;justify-content:flex-end}
.SB_FBR button{padding:7px 16px;border-radius:14px;border:1px solid rgba(120,200,255,.4);background:rgba(120,200,255,.15);color:#cfe9ff;cursor:pointer}
#SB_PCA{background:rgba(255,255,255,.08);border-color:rgba(255,255,255,.2);color:rgba(255,255,255,.7)}
.SB_GR{column-width:280px;column-gap:16px}
.SB_IT{position:relative;border-radius:18px;overflow:hidden;cursor:pointer;background:rgba(255,255,255,.07);border:1px solid rgba(255,255,255,.14);box-shadow:0 4px 20px rgba(0,0,0,.12);break-inside:avoid;margin-bottom:16px;padding:14px 16px;text-align:left;transition:transform .25s cubic-bezier(.2,.8,.2,1)}
.SB_IT:hover{transform:translateY(-3px)}
.SB_ROW{display:flex;gap:10px;align-items:flex-start}
.SB_AV{width:34px;height:34px;border-radius:50%;flex:none;background-size:cover;background-position:center;border:1px solid rgba(255,255,255,.2)}
.SB_NM{font-size:.7rem;color:rgba(255,255,255,.5);margin-bottom:4px}
.SB_TX{color:rgba(255,255,255,.92);font-size:.9rem;line-height:1.45;white-space:pre-wrap;word-break:break-word}
.SB_MT{margin-top:8px;font-size:.68rem;color:rgba(255,255,255,.35)}
.SB_EMP{text-align:center;padding:50px 20px;color:rgba(255,255,255,.4)}
.SB_DTS{display:flex;justify-content:center;gap:7px;padding:50px}
.SB_DT{width:7px;height:7px;border-radius:50%;background:rgba(255,255,255,.4);animation:SB_P .8s ease-in-out infinite}
.SB_DT:nth-child(2){animation-delay:.15s}
.SB_DT:nth-child(3){animation-delay:.3s}
@keyframes SB_P{0%,100%{opacity:.25;transform:scale(.8)}50%{opacity:1;transform:scale(1.1)}}
.SB_MO{position:fixed;inset:0;z-index:50;display:none;align-items:flex-end;justify-content:center;background:rgba(0,0,0,.5);backdrop-filter:blur(4px)}
.SB_MO.SB_MOP{display:flex}
.SB_MB{width:100%;max-width:560px;max-height:82vh;display:flex;flex-direction:column;background:rgba(24,24,28,.85);backdrop-filter:blur(20px);border:1px solid rgba(255,255,255,.15);border-radius:22px 22px 0 0;box-shadow:0 -8px 30px rgba(0,0,0,.4)}
body.low-perf :is(.SB_FRM,.SB_MO,.SB_MB){backdrop-filter:none}
@media(min-width:640px){.SB_MO{align-items:center}.SB_MB{border-radius:22px;max-height:78vh}}
.SB_MHD{display:flex;align-items:flex-start;gap:10px;padding:16px 16px 10px;border-bottom:1px solid rgba(255,255,255,.1)}
.SB_MX{margin-left:auto;background:none;border:none;color:rgba(255,255,255,.6);font-size:1.3rem;cursor:pointer;line-height:1;padding:2px 6px}
.SB_MBODY{overflow-y:auto;padding:12px 16px;display:flex;flex-direction:column;gap:10px;flex:1}
.SB_CB{background:rgba(255,255,255,.06);border-radius:14px;padding:9px 12px}
.SB_CMORE{align-self:center;background:none;border:1px solid rgba(255,255,255,.2);color:rgba(255,255,255,.6);border-radius:12px;padding:5px 14px;font-size:.75rem;cursor:pointer}
.SB_MFT{display:flex;gap:8px;padding:12px 16px;border-top:1px solid rgba(255,255,255,.1)}
.SB_MFT input{flex:1;border-radius:12px;border:1px solid rgba(255,255,255,.18);background:rgba(0,0,0,.25);color:#fff;padding:9px 12px;font-size:.85rem}
.SB_MFT button{border-radius:12px;border:1px solid rgba(120,200,255,.4);background:rgba(120,200,255,.15);color:#cfe9ff;padding:0 16px;cursor:pointer}
@media(max-width:480px){.SB_GR{column-width:100%}}
</style>

<a class="SB_NB SB_NBL" href="web/es.html">🏠</a>

<div style="text-align:center">
<div id="SB_W">
<div class="SB_HD">
<h2>SECRETOS</h2>
<div class="SB_BR"><button id="SB_AB">✍️ Añadir Nota</button></div>
<div class="SB_FRM" id="SB_PF">
<textarea id="SB_PTX" maxlength="2000" placeholder="Escribe algo..."></textarea>
<div class="SB_CNT"><span id="SB_PCT">0</span>/2000</div>
<div class="SB_FBR"><button id="SB_PCA">Cancelar</button><button id="SB_PSD">Publicar</button></div>
</div>
</div>
<div class="SB_DTS" id="SB_LD"><div class="SB_DT"></div><div class="SB_DT"></div><div class="SB_DT"></div></div>
<div class="SB_GR" id="SB_GD" style="display:none"></div>
</div>
</div>

<div class="SB_MO" id="SB_MD">
<div class="SB_MB">
<div class="SB_MHD">
<div class="SB_AV" id="SB_MAV"></div>
<div><div class="SB_NM" id="SB_MNM"></div><div class="SB_TX" id="SB_MTX"></div></div>
<button class="SB_MX" id="SB_MXB">✕</button>
</div>
<div class="SB_MBODY" id="SB_MBD"></div>
<div class="SB_MFT">
<input type="text" id="SB_MIN" maxlength="500" placeholder="Comentar..."/>
<button id="SB_MSD">Enviar</button>
</div>
</div>
</div>

<script>
(function(){
const SB_API='/api/secret';
const SB_PG=30;
let SB_off=0,SB_ac=null,SB_cur=null,SB_coff=0,SB_posts=[];

function SB_seed(id){let h=0;for(let i=0;i<id.length;i++)h=(h*31+id.charCodeAt(i))>>>0;return h;}
function SB_av(id){return `https://picsum.photos/seed/${SB_seed(id)}/64/64`;}
function SB_nm(id){return 'Anonimo#'+String(SB_seed(id)%10000).padStart(4,'0');}
function SB_esc(s){const d=document.createElement('div');d.textContent=s;return d.innerHTML;}
function SB_clean(t){return t.replace(/<[^>]*>/g,'').replace(/!\[[^\]]*\]\([^)]*\)/g,'').replace(/\[[^\]]*\]\([^)]*\)/g,'').trim();}
function SB_time(ts){const diff=(Date.now()-ts)/1000;if(diff<60)return 'ahora';if(diff<3600)return Math.floor(diff/60)+'m';if(diff<86400)return Math.floor(diff/3600)+'h';return new Date(ts).toLocaleDateString();}
function SB_fmtWait(s){const m=Math.ceil(s/60);return m<=1?'1 minuto':m<60?m+' minutos':Math.ceil(m/60)+'h';}

function SB_mkCmt(c){
  const w=document.createElement('div');w.className='SB_CB';
  const id=String(c.ts);
  w.innerHTML=`<div class="SB_ROW"><div class="SB_AV" style="background-image:url(${SB_av(id)})"></div>
  <div style="flex:1"><div class="SB_NM">${SB_nm(id)} · ${SB_time(c.ts)}</div>
  <div class="SB_TX">${SB_esc(c.txt)}</div></div></div>`;
  return w;
}

function SB_mkItem(p){
  const it=document.createElement('div');it.className='SB_IT';it.dataset.id=p.id;
  it.innerHTML=`<div class="SB_ROW">
  <div class="SB_AV" style="background-image:url(${SB_av(p.id)})"></div>
  <div style="flex:1"><div class="SB_NM">${SB_nm(p.id)}</div>
  <div class="SB_TX">${SB_esc(p.txt)}</div>
  <div class="SB_MT">${SB_time(p.ts)} · ${p.nc||0} comentarios</div></div></div>`;
  return it;
}

let SB_gfP=null;
let SB_tsP=null;
const SB_TS=()=>(window.TS1?Promise.resolve():SB_tsP||(SB_tsP=new Promise((ok,no)=>{const s=document.createElement('script');s.src='web/js/lib/Turnstile.js';s.onload=ok;s.onerror=()=>{SB_tsP=null;no()};document.head.appendChild(s)}))).then(()=>window.TS1()).catch(()=>null);
const SB_VE='Error verificacion, recarga la pagina';
const SB_GF=()=>window.GridFit?Promise.resolve(window.GridFit):SB_gfP||(SB_gfP=new Promise(r=>{const s=document.createElement('script');s.src='web/js/lib/GridFit.js';s.onload=s.onerror=()=>r(window.GridFit);document.head.appendChild(s)}));
async function SB_fetchPage(off){
  if(SB_ac)SB_ac.abort();
  SB_ac=new AbortController();
  try{const r=await fetch(`${SB_API}?off=${off}`,{signal:SB_ac.signal});return await r.json();}
  catch(e){return [];}
}

async function SB_render(off){
  const gd=document.getElementById('SB_GD'),ld=document.getElementById('SB_LD');
  const posts=await SB_fetchPage(off);
  if(ld)ld.style.display='none';
  gd.style.display='';
  gd.innerHTML='';
  SB_posts=posts;
  if(!posts.length&&off===0){gd.innerHTML='<div class="SB_EMP">🕳️ Sin publicaciones aun</div>';return;}
  posts.forEach(p=>gd.appendChild(SB_mkItem(p)));
  const nav=document.createElement('nav'),cp=Math.floor(off/SB_PG);
  const pn=()=>GridFit.PN1(nav,cp,cp+1+(posts.length<SB_PG?0:1),i=>{SB_off=i*SB_PG;SB_render(SB_off);gd.scrollIntoView({behavior:'smooth',block:'start'});},0);
  window.GridFit?pn():SB_GF().then(g=>{if(g)pn()});
  gd.appendChild(nav);
}

async function SB_loadCmts(pid,coff,append){
  const box=document.getElementById('SB_MBD');
  try{
    const r=await fetch(`${SB_API}?id=${encodeURIComponent(pid)}&coff=${coff}`);
    const d=await r.json();
    if(!append)box.querySelectorAll('.SB_CB,.SB_CMORE').forEach(n=>n.remove());
    let more=box.querySelector('.SB_CMORE');
    if(more)more.remove();
    (d.cmts||[]).forEach(c=>box.appendChild(SB_mkCmt(c)));
    if(d.cmts&&d.cmts.length===SB_PG){
      const b=document.createElement('button');b.className='SB_CMORE';b.textContent='Cargar mas';
      b.onclick=()=>SB_loadCmts(pid,coff+SB_PG,true);
      box.appendChild(b);
    }
  }catch(e){}
}

function SB_openModal(p){
  SB_cur=p;SB_coff=0;
  document.getElementById('SB_MAV').style.backgroundImage=`url(${SB_av(p.id)})`;
  document.getElementById('SB_MNM').textContent=SB_nm(p.id);
  document.getElementById('SB_MTX').textContent=p.txt;
  document.getElementById('SB_MBD').innerHTML='';
  document.getElementById('SB_MIN').value='';
  document.getElementById('SB_MD').classList.add('SB_MOP');
  SB_loadCmts(p.id,0,false);
}

function SB_closeModal(){
  document.getElementById('SB_MD').classList.remove('SB_MOP');
  SB_cur=null;
}

async function SB_sendCmt(){
  if(!SB_cur)return;
  const inp=document.getElementById('SB_MIN');
  const c=SB_clean(inp.value).slice(0,500);
  if(!c)return;
  try{
    const ts=await SB_TS();
    const r=ts&&await fetch(`${SB_API}?c=1`,{method:'POST',headers:{'content-type':'application/json','x-ts':ts},body:JSON.stringify({id:SB_cur.id,txt:c})});
    if(!r||r.status===403){SB_showLimit(document.querySelector('.SB_MFT'),0,SB_VE);return;}
    if(r.status===429){
      const d=await r.json().catch(()=>({}));
      SB_showLimit(document.querySelector('.SB_MFT'),d.retryAfter);
      return;
    }
    if(!r.ok)return;
    const row=await r.json();
    document.getElementById('SB_MBD').appendChild(SB_mkCmt(row));
    inp.value='';
  }catch(e){}
}

function SB_updCnt(){
  const t=document.getElementById('SB_PTX'),c=document.getElementById('SB_PCT');
  if(t&&c)c.textContent=t.value.length;
}

function SB_closeForm(){
  const pf=document.getElementById('SB_PF');
  pf.classList.remove('SB_FOPEN');
  pf.style.display='none';
  document.getElementById('SB_PTX').value='';
  SB_updCnt();
}

async function SB_publish(){
  const t=document.getElementById('SB_PTX');
  const c=SB_clean(t.value).slice(0,2000);
  if(!c)return;
  const btn=document.getElementById('SB_PSD');
  btn.disabled=true;
  try{
    const ts=await SB_TS();
    const r=ts&&await fetch(SB_API,{method:'POST',headers:{'content-type':'application/json','x-ts':ts},body:JSON.stringify({txt:c})});
    if(!r||r.status===403){SB_showLimit(document.querySelector('.SB_FBR'),0,SB_VE);btn.disabled=false;return;}
    if(r.status===429){
      const d=await r.json().catch(()=>({}));
      SB_showLimit(document.querySelector('.SB_FBR'),d.retryAfter);
      btn.disabled=false;return;
    }
    if(!r.ok){btn.disabled=false;return;}
    await r.json();
    SB_closeForm();
    SB_off=0;
    SB_render(0);
  }catch(e){}
  btn.disabled=false;
}

function SB_showLimit(container,retryAfter,tx){
  let el=container.querySelector('.SB_LIMIT');
  if(!el){el=document.createElement('div');el.className='SB_LIMIT';container.parentElement.insertBefore(el,container);}
  el.textContent=tx||(retryAfter?`Limite alcanzado, espera ${SB_fmtWait(retryAfter)}`:'Limite alcanzado, intenta mas tarde');
  clearTimeout(el._t);
  el._t=setTimeout(()=>el.remove(),8000);
}

function SB_onGridClick(e){
  const it=e.target.closest('.SB_IT');
  if(!it)return;
  const p=SB_posts.find(x=>x.id===it.dataset.id);
  if(p)SB_openModal(p);
}

function SB_onKey(e){
  if(e.key==='Escape'&&SB_cur)SB_closeModal();
}

function SB_init(){
  if(!document.getElementById('SB_W'))return;
  SB_off=0;SB_cur=null;
  const ab=document.getElementById('SB_AB'),pf=document.getElementById('SB_PF');
  ab.addEventListener('click',()=>{
    const open=pf.classList.toggle('SB_FOPEN');
    pf.style.display=open?'flex':'none';
  });
  document.getElementById('SB_PCA').addEventListener('click',SB_closeForm);
  document.getElementById('SB_PTX').addEventListener('input',SB_updCnt);
  document.getElementById('SB_PSD').addEventListener('click',SB_publish);
  document.getElementById('SB_GD').addEventListener('click',SB_onGridClick);
  document.getElementById('SB_MXB').addEventListener('click',SB_closeModal);
  document.getElementById('SB_MD').addEventListener('click',e=>{if(e.target.id==='SB_MD')SB_closeModal();});
  document.getElementById('SB_MSD').addEventListener('click',SB_sendCmt);
  document.getElementById('SB_MIN').addEventListener('keydown',e=>{if(e.key==='Enter')SB_sendCmt();});
  document.addEventListener('keydown',SB_onKey);
  SB_render(0);
}

function SB_cleanup(){
  if(SB_ac)SB_ac.abort();
  document.removeEventListener('keydown',SB_onKey);
  document.removeEventListener('contentLoaded',SB_init);
  SB_cur=null;SB_posts=[];
}

document.addEventListener('contentLoaded',SB_init);
document.addEventListener('contentUnload',SB_cleanup,{once:true});
})();
</script>