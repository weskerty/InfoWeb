<div class="DG_W1">
<style>
.DG_W1 section{padding:18px 0;border-top:1px solid var(--RD_L)}
.DG_W1 h2{display:flex;flex-wrap:wrap;align-items:center;gap:10px;margin:0 0 14px;font-size:1.15rem}
.DG_NB{display:inline-grid;place-items:center;width:28px;height:28px;border:1px solid var(--RD_L);border-radius:8px;font-size:.9rem}
.DG_SB,.DG_HT{margin:0 0 16px;color:var(--RD_MF);font-size:.95rem;line-height:1.5}
.DG_HT{margin:10px 0 0}
#DG_T1{box-sizing:border-box;width:100%;margin-bottom:10px}
.DG_R2{display:flex;gap:8px;align-items:center}
.DG_R2 input{flex:1;min-width:0}
.DG_R2 input+input{flex:0 0 7.5em}
.DG_C1{display:flex;flex-wrap:wrap;align-items:center;gap:6px;margin-top:10px}
.DG_C1 button{padding:5px 11px;font-size:.85rem}
.DG_LB{margin:14px 0 2px;color:var(--RD_MF);font-size:.85rem}
.DG_C1 .DG_LB{margin:0 2px 0 0}
.DG_IR{padding:12px 0;border-bottom:1px dashed var(--RD_L)}
.DG_FT{display:flex;flex-wrap:wrap;align-items:center;justify-content:space-between;gap:10px;margin-top:14px;font-weight:600}
.DG_GH{margin:14px 0 4px;color:var(--RD_F2)}
.DG_GR,.DG_PR{display:flex;align-items:center;gap:10px;padding:8px 0;border-top:1px solid var(--RD_L)}
.DG_GR span,.DG_PR span{flex:1;min-width:0;overflow-wrap:anywhere}
.DG_GR button{padding:4px 10px}
.DG_W1 small{display:block;color:var(--RD_MF);font-size:.8rem}
.DG_TR{display:flex;flex-wrap:wrap;align-items:center;gap:6px 8px;margin:8px 0;padding:12px 14px;border:1px solid var(--RD_L);border-radius:10px}
.DG_TR b{margin-left:auto}
.DG_AR{color:var(--RD_MF);font:500 .9rem var(--font)}
.DG_OK{color:var(--ok)}
.DG_WN{color:var(--warn)}
.DG_MS{min-height:1.2em;margin-top:6px;color:var(--warn);font-size:.85rem}
.DG_AC{display:flex;flex-wrap:wrap;gap:8px;margin-top:16px}
</style>
<h1>💸 Dividir Gastos</h1>
<div class="DG_SB">Anota quien pago cada cosa y te dice quien le paga a quien. Todo viaja dentro del link: mandalo al grupo y todos ven lo mismo.</div>
<section>
<h2><span class="DG_NB">1</span>Personas</h2>
<input id="DG_T1" placeholder="Nombre de la salida (opcional)" maxlength="60">
<div class="DG_R2"><input id="DG_P1" placeholder="Nombre de una persona" maxlength="30"><button id="DG_PB" type="button">➕ Agregar</button></div>
<div class="DG_C1" id="DG_PL"></div>
<div class="DG_HT" id="DG_H1">Agrega al menos 2 personas para empezar.</div>
<div class="DG_MS" id="DG_M1"></div>
</section>
<section id="DG_S2" hidden>
<h2><span class="DG_NB">2</span>Agregar gasto</h2>
<div class="DG_LB">Quien pago</div>
<div class="DG_C1" id="DG_PG"></div>
<div class="DG_LB">Productos</div>
<div id="DG_IT"></div>
<div class="DG_C1"><button id="DG_AI" type="button">➕ Otro producto</button></div>
<div class="DG_FT"><span id="DG_TO"></span><button id="DG_GA" class="view-all-button GL_C" type="button">Guardar gasto</button></div>
<div class="DG_MS" id="DG_M2"></div>
</section>
<section id="DG_S3" hidden>
<h2><span class="DG_NB">3</span>Gastos <span class="DG_AR" id="DG_GT"></span></h2>
<div id="DG_GL"></div>
</section>
<section id="DG_S4" hidden>
<h2><span class="DG_NB">4</span>Quien le paga a quien</h2>
<div id="DG_RS"></div>
<div class="DG_LB">Detalle por persona</div>
<div id="DG_DT"></div>
<div class="DG_AC"><button id="DG_B1" type="button">🔗 Copiar link</button><button id="DG_B3" type="button">📋 Copiar resumen</button><button id="DG_B4" type="button">🗑️ Nueva salida</button></div>
</section>

<script>
(function(){
const $=i=>document.getElementById(i);
const DG_F0=()=>({p:0,r:[{d:'',m:0,e:null}]});
let S={t:'',n:[],g:[]},F=DG_F0();
const DG_K='DG_L1',DG_RX=/#G1\.([A-Za-z0-9_-]+)$/;
const DG_M=n=>Math.round(n).toLocaleString('es-PY')+' Gs';
const DG_EL=(t,c,x)=>{const e=document.createElement(t);if(c)e.className=c;if(x!=null)e.textContent=x;return e};
const DG_BT=(x,f,l,pr)=>{const b=DG_EL('button',0,x);b.type='button';b.onclick=f;if(l)b.setAttribute('aria-label',l);if(pr!=null)b.setAttribute('aria-pressed',pr);return b};
const DG_MS=(i,t)=>{$(i).textContent=t};
async function DG_E(o){
  const b=new Uint8Array(await new Response(new Blob([JSON.stringify(o)]).stream().pipeThrough(new CompressionStream('deflate-raw'))).arrayBuffer());
  let s='';for(const x of b)s+=String.fromCharCode(x);
  return btoa(s).replace(/\+/g,'-').replace(/\//g,'_').replace(/=+$/,'');
}
async function DG_DE(t){
  const s=atob(t.replace(/-/g,'+').replace(/_/g,'/'));
  const o=JSON.parse(await new Response(new Blob([Uint8Array.from(s,c=>c.charCodeAt(0))]).stream().pipeThrough(new DecompressionStream('deflate-raw'))).text());
  if(!Array.isArray(o.n)||!Array.isArray(o.g))throw 0;
  const n=o.n.map(x=>String(x).slice(0,30)),ok=i=>Number.isInteger(i)&&i>=0&&i<n.length;
  return{t:String(o.t||'').slice(0,60),n,g:o.g.filter(g=>Array.isArray(g)&&ok(g[2])).map(g=>[String(g[0]).slice(0,60),Math.max(0,Math.round(+g[1]||0)),g[2],Array.isArray(g[3])?g[3].filter(ok):[]])};
}
async function DG_SV(){
  const d=await DG_E(S);
  history.replaceState(history.state,'',location.pathname+location.search+location.hash.replace(/#G1\.[A-Za-z0-9_-]*$/,'')+'#G1.'+d);
  try{localStorage.setItem(DG_K,d)}catch{}
}
function DG_CA(){
  const pg=S.n.map(()=>0),tc=S.n.map(()=>0);let tot=0;
  for(const[,m,p,e]of S.g){
    const q=e.length?e:S.n.map((_,i)=>i),base=Math.floor(m/q.length);let r=m-base*q.length;
    tot+=m;pg[p]+=m;
    for(const i of q){tc[i]+=base+(r>0?1:0);r--}
  }
  const b=pg.map((v,i)=>v-tc[i]),cr=b.map((v,i)=>[i,v]).filter(x=>x[1]>0).sort((a,z)=>z[1]-a[1]),de=b.map((v,i)=>[i,-v]).filter(x=>x[1]>0).sort((a,z)=>z[1]-a[1]),tr=[];
  let i=0,j=0;
  while(i<de.length&&j<cr.length){const v=Math.min(de[i][1],cr[j][1]);if(v>0)tr.push([de[i][0],cr[j][0],v]);de[i][1]-=v;cr[j][1]-=v;if(!de[i][1])i++;if(!cr[j][1])j++}
  return{pg,tc,b,tot,tr};
}
function DG_TX(){
  const{tot,tr}=DG_CA();
  return(S.t?S.t+'\n':'')+'Total '+DG_M(tot)+'\n'+(tr.length?tr.map(([d,c,v])=>`${S.n[d]} le paga a ${S.n[c]}: ${DG_M(v)}`).join('\n'):'Nadie le debe a nadie');
}
function DG_PX(i){
  if(S.g.some(g=>g[2]===i||!g[3].length||g[3].includes(i)))return DG_MS('DG_M1',S.n[i]+' esta en gastos: borralos primero');
  S.n.splice(i,1);S.g.forEach(g=>{if(g[2]>i)g[2]--;g[3]=g[3].map(k=>k>i?k-1:k)});
  F.r.forEach(r=>r.e=null);DG_U();
}
function DG_RP(){
  $('DG_T1').value=S.t;
  const pl=$('DG_PL'),pg=$('DG_PG');pl.textContent='';pg.textContent='';
  S.n.forEach((p,i)=>pl.append(DG_BT(p+' ✕',()=>DG_PX(i),'Quitar '+p)));
  $('DG_H1').hidden=S.n.length>1;$('DG_S2').hidden=S.n.length<2;
  if(F.p>=S.n.length)F.p=0;
  S.n.forEach((p,i)=>pg.append(DG_BT(p,()=>{F.p=i;[...pg.children].forEach((b,k)=>b.setAttribute('aria-pressed',k===i))},0,i===F.p)));
}
function DG_TO(){$('DG_TO').textContent='Total '+DG_M(F.r.reduce((s,r)=>s+r.m,0))}
function DG_RF(){
  const it=$('DG_IT');it.textContent='';
  F.r.forEach((r,k)=>{
    const w=DG_EL('div','DG_IR'),a=DG_EL('div','DG_R2'),c=DG_EL('div','DG_C1'),d=DG_EL('input'),m=DG_EL('input');
    d.placeholder='Producto';d.maxLength=60;d.value=r.d;d.oninput=()=>{r.d=d.value};
    m.placeholder='Precio Gs';m.inputMode='numeric';m.value=r.m?r.m.toLocaleString('es-PY'):'';
    m.oninput=()=>{const v=m.value.replace(/\D/g,'').slice(0,12);r.m=+v;m.value=v?r.m.toLocaleString('es-PY'):'';DG_TO()};
    a.append(d,m);
    if(F.r.length>1)a.append(DG_BT('✕',()=>{F.r.splice(k,1);DG_RF()},'Quitar producto'));
    c.append(DG_EL('span','DG_LB','Entre'));
    S.n.forEach((p,i)=>c.append(DG_BT(p,e=>{const s=r.e||new Set(S.n.keys());s.has(i)?s.delete(i):s.add(i);r.e=s.size===S.n.length?null:s;e.currentTarget.setAttribute('aria-pressed',s.has(i))},0,!r.e||r.e.has(i))));
    w.append(a,c);it.append(w);
  });
  DG_TO();
}
function DG_RG(){
  const gl=$('DG_GL');gl.textContent='';
  S.n.forEach((p,i)=>{
    const its=S.g.map((g,k)=>[g,k]).filter(([g])=>g[2]===i);if(!its.length)return;
    const h=DG_EL('div','DG_GH',p+' pago ');h.append(DG_EL('b',0,DG_M(its.reduce((s,[g])=>s+g[1],0))));gl.append(h);
    its.forEach(([[d,m,,e],k])=>{
      const r=DG_EL('div','DG_GR'),s=DG_EL('span',0,d);
      s.append(DG_EL('small',0,'Entre '+(e.length&&e.length<S.n.length?e.map(x=>S.n[x]).join(', '):'todos')));
      r.append(s,DG_EL('b',0,DG_M(m)),DG_BT('✕',()=>{S.g.splice(k,1);DG_U()},'Borrar '+d));gl.append(r);
    });
  });
}
function DG_RR(){
  const rs=$('DG_RS'),dt=$('DG_DT');rs.textContent='';dt.textContent='';
  $('DG_S3').hidden=$('DG_S4').hidden=!S.g.length;
  if(!S.g.length)return;
  const{pg,tc,b,tot,tr}=DG_CA();
  $('DG_GT').textContent='· '+DG_M(tot);
  if(!tr.length)rs.append(DG_EL('div','DG_TR DG_OK','✅ Nadie le debe a nadie'));
  tr.forEach(([d,c,v])=>{const r=DG_EL('div','DG_TR');r.append(DG_EL('span',0,S.n[d]),DG_EL('span','DG_AR','le paga a'),DG_EL('span',0,S.n[c]),DG_EL('b',0,DG_M(v)));rs.append(r)});
  S.n.forEach((p,i)=>{
    const r=DG_EL('div','DG_PR'),a=DG_EL('span',0,p);
    a.append(DG_EL('small',0,'Pago '+DG_M(pg[i])+' · le toca '+DG_M(tc[i])));
    r.append(a,DG_EL('b',b[i]>0?'DG_OK':b[i]<0?'DG_WN':0,b[i]>0?'recibe '+DG_M(b[i]):b[i]<0?'debe '+DG_M(-b[i]):'a mano'));dt.append(r);
  });
}
function DG_R(){DG_RP();DG_RF();DG_RG();DG_RR()}
function DG_U(){DG_MS('DG_M1','');DG_MS('DG_M2','');DG_R();DG_SV()}
const DG_PA=()=>{
  const v=$('DG_P1').value.trim().slice(0,30);if(!v)return;
  if(S.n.includes(v))return DG_MS('DG_M1',v+' ya esta');
  S.n.push(v);$('DG_P1').value='';DG_U();$('DG_P1').focus();
};
const DG_CP=(t,ok)=>async e=>{const b=e.currentTarget,x=b.textContent;try{await navigator.clipboard.writeText(t());b.textContent=ok;setTimeout(()=>{b.textContent=x},2000)}catch{}};
$('DG_T1').onchange=e=>{S.t=e.target.value.trim().slice(0,60);DG_U()};
$('DG_PB').onclick=DG_PA;
$('DG_P1').onkeydown=e=>{if(e.key==='Enter')DG_PA()};
$('DG_AI').onclick=()=>{F.r.push({d:'',m:0,e:null});DG_RF();$('DG_IT').lastChild.querySelector('input').focus()};
$('DG_GA').onclick=()=>{
  const v=F.r.filter(r=>r.m>0);
  if(!v.length)return DG_MS('DG_M2','Falta el precio');
  if(v.some(r=>r.e&&!r.e.size))return DG_MS('DG_M2','Cada producto necesita al menos una persona');
  v.forEach(r=>S.g.push([r.d.trim().slice(0,60)||'Gasto',r.m,F.p,r.e?[...r.e].sort((a,z)=>a-z):S.n.map((_,i)=>i)]));
  F.r=DG_F0().r;DG_U();
};
$('DG_B1').onclick=DG_CP(()=>location.href,'✅ Link copiado');
$('DG_B3').onclick=DG_CP(()=>DG_TX()+'\n'+location.href,'✅ Copiado');
$('DG_B4').onclick=()=>{if(confirm('Borrar esta salida?')){S={t:'',n:[],g:[]};F=DG_F0();DG_U()}};
if(navigator.share)$('DG_B3').before(DG_BT('📤 Compartir',()=>navigator.share({title:S.t||'Dividir Gastos',text:DG_TX(),url:location.href}).catch(()=>{})));
async function DG_L(w){
  for(let i=0;w&&i<20&&!DG_RX.test(location.hash);i++)await new Promise(r=>setTimeout(r,50));
  const h=location.hash.match(DG_RX);let t=h&&h[1];
  if(!t)try{t=localStorage.getItem(DG_K)}catch{}
  if(t)try{S=await DG_DE(t)}catch{DG_MS('DG_M1','Link danado')}
  DG_R();if(S.n.length)DG_SV();
}
const DG_HC=()=>{if(DG_RX.test(location.hash))DG_L()};
window.addEventListener('hashchange',DG_HC);
document.addEventListener('contentUnload',()=>window.removeEventListener('hashchange',DG_HC),{once:true});
DG_R();DG_L(1);
})();
</script>

</div>
