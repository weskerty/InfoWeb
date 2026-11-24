<style>
.EJ1{display:flex;flex-direction:column;gap:6px;margin:14px 0}
.EJ2 h2{display:flex;justify-content:space-between;align-items:baseline;gap:10px}
.EJ3{font-size:.55em;font-weight:400;color:rgba(255,255,255,.45);letter-spacing:.06em;flex-shrink:0}
.EJ4{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:10px;margin-top:10px}
.EJ5{display:flex;gap:11px;padding:12px;border-radius:14px;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.09);transition:border-color .2s}
.EJ5:hover{border-color:rgba(255,255,255,.18)}
.EJ6{width:52px;height:52px;border-radius:10px;object-fit:cover;flex-shrink:0}
.EJ7{flex:1;min-width:0;display:flex;flex-direction:column;gap:9px;justify-content:center}
.EJ8{font-size:.85em;color:rgba(255,255,255,.6);line-height:1.45;margin:0;overflow-wrap:break-word}
.EJ9{display:flex;gap:6px;flex-wrap:wrap}
.EJ0{color:rgba(255,255,255,.4);font-size:.9em;text-align:center;padding:30px 0}
</style>

<h1 style="margin:0 0 6px;font-size:1.4em;font-weight:700;color:#fff">🎮 Encuentra Jugadores</h1>
<p style="margin:0 0 14px;font-size:.88em;color:rgba(255,255,255,.45)">Gente buscando con quien jugar.</p>

<div id="EJ_W1" class="EJ1"><p class="EJ0">Cargando...</p></div>

<a href="web/paginas/AgregarPublico.html" class="back-button"> Subir Peticion ➡️</a>
<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>



<script>
(function(){
const W=document.getElementById('EJ_W1');
if(!W)return;
const U1='web/Publico/jugadores/data.json';

function EJ_E1(s){const d=document.createElement('div');d.textContent=s==null?'':String(s);return d.innerHTML;}
function EJ_K1(s){return s.normalize('NFD').replace(/[\u0300-\u036f]/g,'').toLowerCase().replace(/\s+/g,' ').trim();}

function EJ_P1(rel){
  const fn=rel.split('/').pop();
  const mNB=fn.match(/NB=(.+)\.\w+$/);
  const mNM=fn.match(/NM=(\d+)/);
  if(!mNB||!mNM)return null;
  const mCH=fn.match(/CH=([^-]+)/);
  const p=mNB[1].split(';');
  const juego=(p[0]||'').trim();
  if(!juego)return null;
  return{juego,desc:(p[1]||'').trim(),tel:mNM[1],ch:mCH?mCH[1]:'WA',img:rel};
}

function EJ_G1(l){
  const m=new Map();
  l.forEach(e=>{
    const k=EJ_K1(e.juego);
    let g=m.get(k);
    if(!g){g={n:new Map(),it:[]};m.set(k,g);}
    g.n.set(e.juego,(g.n.get(e.juego)||0)+1);
    g.it.push(e);
  });
  return[...m.values()].map(g=>({
    nombre:[...g.n].sort((a,b)=>b[1]-a[1]||a[0].localeCompare(b[0]))[0][0],
    it:g.it
  })).sort((a,b)=>b.it.length-a.it.length||a.nombre.localeCompare(b.nombre));
}

const EJ_B1={
  WA:(n,m)=>`<a class="lk lk-wa" href="https://wa.me/${n}?text=${m}" target="_blank" rel="noopener noreferrer">WhatsApp</a>`,
  TG:(n,m)=>`<a class="lk lk-tg" href="https://t.me/+${n}?text=${m}" target="_blank" rel="noopener noreferrer">Telegram</a>`,
  SM:(n,m)=>`<a class="lk" href="sms:+${n}?body=${m}">SMS</a>`
};

function EJ_C1(e){
  const n=String(e.tel).replace(/\D/g,'');
  const m=encodeURIComponent(`Hola, te vi en Che Agana buscando gente para jugar ${e.juego}`);
  const acts=n?e.ch.split('.').map(c=>EJ_B1[c]?EJ_B1[c](n,m):'').join(''):'';
  return`<div class="EJ5">
    ${e.img?`<img class="EJ6" src="${encodeURI(e.img)}" alt="" loading="lazy" onerror="this.style.display='none'">`:''}
    <div class="EJ7">
      ${e.desc?`<p class="EJ8">${EJ_E1(e.desc)}</p>`:''}
      ${acts?`<div class="EJ9">${acts}</div>`:''}
    </div>
  </div>`;
}

function EJ_S1(g){
  const d=document.createElement('div');
  d.className='EJ2';
  d.innerHTML=`<h2>${EJ_E1(g.nombre)}<span class="EJ3">${g.it.length}</span></h2><div class="EJ4">${g.it.map(EJ_C1).join('')}</div>`;
  return d;
}

fetch(U1)
  .then(r=>r.ok?r.json():null)
  .then(d=>{
    const files=d?((d.galleries||{}).jugadores||[]):[];
    const l=files.map(EJ_P1).filter(Boolean);
    W.innerHTML='';
    if(!l.length){W.innerHTML='<p class="EJ0">Sin jugadores publicados todavia.</p>';return;}
    const f=document.createDocumentFragment();
    EJ_G1(l).forEach(g=>f.appendChild(EJ_S1(g)));
    W.appendChild(f);
  })
  .catch(()=>{W.innerHTML='<p class="EJ0">Error al cargar jugadores.</p>';});
})();
</script>
