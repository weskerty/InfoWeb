<div style="text-align:center;position:relative;padding-top:0;margin-top:0" id="rt-app">
<style>
#rt-app{--rh:clamp(52px,13vw,84px);--rg:clamp(2px,.7vw,6px)}
.RT0{font-size:2.8rem;line-height:1.2;margin:0 auto 4px}
.RT1{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:6px 0 16px}
.RT2{list-style:none;padding:0;margin:0 0 14px;display:flex;flex-wrap:wrap;gap:6px;justify-content:center}
.RT3{display:inline-flex;align-items:center;gap:5px;max-width:100%;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.11);border-radius:999px;padding:3px 11px 3px 7px;font-size:.85rem}
.RT3::before{content:none}
.RT4{font-size:1rem;line-height:1;flex:0 0 auto}
.RT6{font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.RTn{animation:RT_p1 .5s ease}
@keyframes RT_p1{from{opacity:0;transform:translateY(-6px)}to{opacity:1;transform:none}}
.RT7{display:flex;align-items:stretch;gap:clamp(8px,2.5vw,18px);justify-content:center;margin:0 0 10px}
.RT8{flex:1 1 auto;min-width:0;background:linear-gradient(160deg,rgba(255,255,255,.16),rgba(255,255,255,.04) 55%,rgba(255,255,255,.12));border:1px solid rgba(255,255,255,.18);border-radius:var(--r-md);padding:clamp(8px,2vw,16px);box-shadow:0 8px 28px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.12)}
.RT9{display:flex;gap:var(--rg);justify-content:center}
.RTa{flex:1 1 0;min-width:0;height:var(--rh);overflow:hidden;position:relative;container-type:inline-size;background:linear-gradient(#0d0e12,#1c1e26 45%,#0d0e12);box-shadow:inset 0 0 0 1px rgba(255,255,255,.12);border-radius:6px}
.RTa::after{content:'';position:absolute;inset:0;pointer-events:none;background:linear-gradient(rgba(0,0,0,.62),transparent 34%,transparent 66%,rgba(0,0,0,.62))}
.RTb{will-change:transform}
.RTb.go{animation:RT_s1 var(--sd) linear infinite}
@keyframes RT_s1{to{transform:translateY(var(--sy))}}
.RTc{height:var(--rh);display:flex;align-items:center;justify-content:center;font-size:min(calc(var(--rh)*.6),88cqw);font-weight:700;color:#fff;line-height:1}
.RTd{filter:blur(1.6px)}
.RTe{background:transparent;border:0;padding:0;cursor:pointer;display:flex;flex-direction:column;align-items:center;width:clamp(32px,8vw,50px);flex:0 0 auto}
.RTf{width:clamp(24px,6.5vw,38px);height:clamp(24px,6.5vw,38px);border-radius:50%;background:radial-gradient(circle at 34% 30%,#ff8f8f,#c0392b 62%,#7b1d13);box-shadow:0 4px 12px rgba(0,0,0,.45),inset 0 -2px 4px rgba(0,0,0,.35);transition:transform .2s cubic-bezier(.3,1.4,.5,1)}
.RTg{width:6px;flex:1 1 auto;background:linear-gradient(90deg,#5b6270,#e5e7eb 45%,#5b6270);border-radius:3px;transform-origin:bottom;transition:transform .2s cubic-bezier(.3,1.4,.5,1)}
.RTe.dn .RTf{transform:translateY(calc(var(--rh)*.55))}
.RTe.dn .RTg{transform:scaleY(.45)}
.RTe:disabled{cursor:not-allowed;opacity:.45}
.RTi{color:rgba(255,255,255,.55);font-size:.9em;margin:0 0 14px}
.RTj{width:100%;box-sizing:border-box;resize:vertical;font-size:1rem;line-height:1.5;min-height:150px}
.RTk{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-top:10px}
body.low-perf .RTd{filter:none}
body.low-perf .RTf,body.low-perf .RTg{transition:none}
@media (prefers-reduced-motion:reduce){.RTd{filter:none}.RTn{animation:none}.RTf,.RTg{transition:none}}
</style>
<div class="RT0">🎰</div>
<div class="RT1">Tragamonedas de Sorteo</div>
<div id="rt-win"></div>
<div class="RT7">
<div class="RT8"><div class="RT9" id="rt-reels"></div></div>
<button class="RTe" id="rt-lev" title="Bajar la palanca"><span class="RTf"></span><span class="RTg"></span></button>
</div>
<p class="RTi" id="rt-msg">Carga nombres abajo, uno por linea</p>
<details open>
<summary>👥 Participantes</summary>
<section>
<textarea class="RTj" id="rt-list" spellcheck="false" placeholder="Un nombre por linea&#10;&#10;Maria Gonzalez&#10;Juan Perez&#10;Ana Lopez"></textarea>
<div class="RTk"><button id="rt-rst">🔄 Reiniciar sorteo</button><button id="rt-clr">🗑️ Vaciar todo</button></div>
</section>
</details>

<script>
(function(){
const A=document.getElementById('rt-app');
if(!A||A.dataset.on)return;
A.dataset.on='1';
const G=document.getElementById('rt-reels'),T=document.getElementById('rt-list'),
LV=document.getElementById('rt-lev'),W=document.getElementById('rt-win'),M=document.getElementById('rt-msg');
const AB='ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789',RM=16,CY=8,LC=14;
const MD=['🥇','🥈','🥉','4️⃣','5️⃣','6️⃣','7️⃣','8️⃣','9️⃣','🔟'];
const RDM=matchMedia('(prefers-reduced-motion:reduce)').matches;
let TM=[],RB=null,SPN=false,WN=[],NR=0;

function rnd(n){const a=new Uint32Array(1),lim=4294967296-4294967296%n;let x;do{crypto.getRandomValues(a);x=a[0]}while(x>=lim);return x%n}
function chr(){return AB[rnd(AB.length)]}
function nms(){return T.value.split('\n').map(s=>s.trim()).filter(Boolean)}

function pod(nw){
  W.innerHTML='';
  if(!WN.length)return;
  const o=document.createElement('ol');o.className='RT2';
  WN.forEach((n,i)=>{
    const li=document.createElement('li');
    li.className='RT3'+(nw&&i===WN.length-1?' RTn':'');
    li.title=n;
    const a=document.createElement('span');a.className='RT4';a.textContent=MD[i]||(i+1)+'.';
    const c=document.createElement('span');c.className='RT6';c.textContent=n;
    li.append(a,c);o.appendChild(li);
  });
  W.appendChild(o);
}

function cnt(){
  const n=nms().length;
  M.textContent=n?n+(n===1?' participante en juego':' participantes en juego'):'Carga nombres abajo, uno por linea';
  LV.disabled=SPN||!n;
}

function rcn(){let m=0;nms().forEach(n=>{if(n.length>m)m=n.length});return Math.max(3,Math.min(RM,m||6))}
function cel(c){const d=document.createElement('div');d.className='RTc';d.textContent=c;return d}
function bld(n){
  G.innerHTML='';NR=n;
  const r=[];
  for(let i=0;i<n;i++){
    const w=document.createElement('div');w.className='RTa';
    const s=document.createElement('div');s.className='RTb';
    s.appendChild(cel(chr()));
    w.appendChild(s);G.appendChild(w);r.push(s);
  }
  return r;
}

function lnd(s,i,H,tx,pd,LD){
  const m=/matrix\([^)]*,\s*(-?[\d.]+)\)/.exec(getComputedStyle(s).transform),y0=m?parseFloat(m[1]):0;
  const b=s.children.length,j=i-pd;
  for(let q=0;q<LC;q++)s.appendChild(cel(chr()));
  s.appendChild(cel(chr()));
  s.appendChild(cel(j>=0&&j<tx.length?tx[j]:''));
  s.style.transition='none';
  s.style.transform='translateY('+y0+'px)';
  s.classList.remove('go');
  void s.offsetHeight;
  s.style.transition='transform '+LD+'ms cubic-bezier(.215,.61,.355,1)';
  s.style.transform='translateY(-'+(b+LC+1)*H+'px)';
  TM.push(setTimeout(()=>s.classList.remove('RTd'),LD*.5));
}

function spin(){
  if(SPN)return;
  const a=nms();
  if(!a.length)return;
  SPN=true;LV.disabled=true;
  LV.classList.add('dn');
  TM.push(setTimeout(()=>LV.classList.remove('dn'),240));
  const k=rnd(a.length),win=a[k],up=win.toUpperCase();
  const n=rcn(),tx=up.slice(0,n),pd=Math.floor((n-tx.length)/2);
  const st=bld(n),H=parseFloat(getComputedStyle(G.querySelector('.RTc')).height);
  const SB=RDM?400:4000,SG=RDM?0:Math.min(800,9000/n),LD=RDM?400:2500;
  st.forEach((s,i)=>{
    s.innerHTML='';
    for(let q=0;q<CY*2;q++)s.appendChild(cel(chr()));
    s.style.setProperty('--sy','-'+CY*H+'px');
    s.style.setProperty('--sd',(260+i*4)+'ms');
    if(!RDM)s.classList.add('RTd');
    s.classList.add('go');
    TM.push(setTimeout(()=>lnd(s,i,H,tx,pd,LD),SB+i*SG));
  });
  TM.push(setTimeout(()=>{
    WN.push(win);
    T.value=a.filter((_,i)=>i!==k).join('\n');
    SPN=false;pod(true);cnt();
  },SB+(n-1)*SG+LD+90));
}

LV.onclick=spin;
T.addEventListener('input',()=>{
  cnt();
  clearTimeout(RB);
  RB=setTimeout(()=>{if(!SPN&&rcn()!==NR)bld(rcn())},400);
});
document.getElementById('rt-rst').onclick=()=>{
  if(SPN||!WN.length)return;
  T.value=WN.concat(nms()).join('\n');
  WN=[];pod();cnt();bld(rcn());
};
document.getElementById('rt-clr').onclick=()=>{
  if(SPN||!confirm('Borrar la lista y los ganadores?'))return;
  T.value='';WN=[];pod();cnt();bld(rcn());
};

pod();cnt();bld(rcn());

document.addEventListener('contentUnload',function td(){TM.forEach(clearTimeout);TM=[];clearTimeout(RB)},{once:true});
})();
</script>

</div>
