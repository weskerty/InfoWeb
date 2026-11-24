<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.vl-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 6px}
.vl-nt{color:rgba(255,255,255,.45);font-size:.8em;max-width:440px;margin:0 auto 14px;line-height:1.5}
.vl-bt{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin:0 auto 14px}
.vl-gr{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;max-width:440px;margin:0 auto 10px}
.vl-k{border-radius:14px;padding:12px 8px;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06)}
.vl-k small{display:block;color:rgba(255,255,255,.5);font-size:.75em;letter-spacing:.06em;text-transform:uppercase}
.vl-k b{display:block;color:#fff;font-size:1.7em;font-weight:700;line-height:1.3}
.vl-k span{color:rgba(255,255,255,.5);font-size:.8em}
.vl-ms{color:rgba(255,255,255,.65);font-size:.85em;min-height:1.3em;margin:6px auto}
.vl-bx{border-radius:14px;padding:12px 14px;margin:10px auto;max-width:440px;text-align:left;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06);font-size:.88em;color:#fff}
.vl-bx:empty{display:none}
.vl-h{font-size:.72em;letter-spacing:.08em;color:rgba(255,255,255,.45);margin:0 0 6px;text-transform:uppercase}
.vl-r{display:flex;justify-content:space-between;gap:10px;padding:3px 0}
.vl-c0,.vl-c1{color:var(--err)}
.vl-c2{color:var(--warn)}
.vl-c3,.vl-c4{color:var(--ok)}
.vl-ms .wait-anim{width:32px;height:32px;display:inline-block;vertical-align:middle}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🚀</div>
<div class="vl-st">Test de Velocidad</div>
<div class="vl-nt">Mide tu internet contra la red de Cloudflare. El completo puede gastar mas de 100 MB: con datos moviles usa el rapido (unos 25 MB).</div>
<div class="vl-bt"><button id="vl-rp">⚡ Rapido</button><button id="vl-cp">🔬 Completo</button><button id="vl-pa" hidden>⏹️ Detener</button></div>
<div class="vl-gr">
  <div class="vl-k"><small>Bajada</small><b id="vl-dl">-</b><span>Mbps</span></div>
  <div class="vl-k"><small>Subida</small><b id="vl-ul">-</b><span>Mbps</span></div>
  <div class="vl-k"><small>Latencia</small><b id="vl-lt">-</b><span>ms</span></div>
  <div class="vl-k"><small>Jitter</small><b id="vl-jt">-</b><span>ms</span></div>
</div>
<div class="vl-ms" id="vl-ms"></div>
<div class="vl-bx" id="vl-sc"></div>
<div class="vl-bx" id="vl-hi"></div>

<script>
(function(){
const $=i=>document.getElementById(i);
const WA=window.__CFG?.waitAnim||'',VL_K='VL_H1';
const VL_Q=[{type:'latency',numPackets:1},{type:'download',bytes:1e5,count:1,bypassMinDuration:true},{type:'latency',numPackets:10},{type:'download',bytes:1e6,count:4},{type:'upload',bytes:1e5,count:4},{type:'download',bytes:1e7,count:2},{type:'upload',bytes:1e6,count:3}];
const VL_N={bad:'Mala',poor:'Pobre',average:'Regular',good:'Buena',great:'Excelente'};
const VL_T={latency:'Midiendo latencia...',download:'Midiendo bajada...',upload:'Midiendo subida...'};
let VL_E=null,VL_I='';
const VL_F=(v,d)=>v==null||isNaN(v)?'-':(+v).toFixed(d);
const VL_EL=(t,c,x)=>{const e=document.createElement(t);if(c)e.className=c;if(x!=null)e.textContent=x;return e};
function VL_HG(){try{return JSON.parse(localStorage.getItem(VL_K))||[]}catch{return[]}}
function VL_HR(){
  const h=VL_HG(),b=$('vl-hi');b.textContent='';if(!h.length)return;
  b.append(VL_EL('div','vl-h','Historial'));
  h.forEach(r=>{const d=VL_EL('div','vl-r');d.append(VL_EL('span',0,new Date(r.t).toLocaleString('es-PY',{day:'2-digit',month:'2-digit',hour:'2-digit',minute:'2-digit'})),VL_EL('span',0,`⬇️ ${VL_F(r.d,1)} ⬆️ ${VL_F(r.u,1)} · ${VL_F(r.l,0)} ms`));b.append(d)});
  const x=VL_EL('button',0,'🗑️ Borrar historial');x.style.marginTop='8px';x.onclick=()=>{try{localStorage.removeItem(VL_K)}catch{}VL_HR()};b.append(x);
}
function VL_S(s){
  $('vl-dl').textContent=VL_F(s.download/1e6,1);$('vl-ul').textContent=VL_F(s.upload/1e6,1);
  $('vl-lt').textContent=VL_F(s.latency,0);$('vl-jt').textContent=VL_F(s.jitter,1);
}
function VL_M(t,w){const m=$('vl-ms');m.textContent='';if(w&&WA){const i=VL_EL('img','wait-anim');i.src=WA;i.alt='';m.append(i,' ')}m.append(t)}
function VL_B(on){$('vl-rp').hidden=$('vl-cp').hidden=on;$('vl-pa').hidden=!on}
async function VL_NET(){
  try{
    const t=Object.fromEntries((await(await fetch('https://speed.cloudflare.com/cdn-cgi/trace',{cache:'no-store'})).text()).trim().split('\n').map(l=>l.split('=')));
    VL_I=[t.colo&&'Servidor Cloudflare '+t.colo+(t.loc?' ('+t.loc+')':''),t.ip&&'tu IP '+t.ip].filter(Boolean).join(' · ');
  }catch{VL_I=''}
}
async function VL_GO(q){
  VL_B(1);VL_S({});$('vl-sc').textContent='';VL_M('Preparando...',1);
  try{
    const[{default:ST}]=await Promise.all([import('https://cdn.jsdelivr.net/npm/@cloudflare/speedtest@1.15.0/dist/speedtest.js'),VL_NET()]);
    VL_E=new ST({autoStart:false,logAimApiUrl:null,...(q?{measurements:VL_Q}:{})});
    VL_E.onResultsChange=({type})=>{VL_S(VL_E.results.getSummary());if(VL_T[type])VL_M(VL_T[type],1)};
    VL_E.onError=()=>{};
    VL_E.onFinish=r=>{
      const s=r.getSummary();VL_S(s);VL_B(0);VL_E=null;VL_M(VL_I||'Listo');
      const b=$('vl-sc');b.textContent='';
      if(s.download){
        const d=s.download/1e6,u=s.upload/1e6||0,l=s.latency||999,j=s.jitter||0;
        const c=[['📺 Video',d>=25?4:d>=10?3:d>=3?2:0,d>=25?'4K':d>=10?'HD':d>=3?'calidad baja':'se corta'],['🎮 Juegos en linea',l<30&&j<10?4:l<60?3:l<100?2:0,Math.round(l)+' ms'],['📞 Videollamadas',u>=5&&l<50?4:u>=2&&l<100?3:u>=1&&l<200?2:0,VL_F(u,1)+' Mbps subida']];
        b.append(VL_EL('div','vl-h','Alcanza para'));
        for(const[k,i,x]of c){const r=VL_EL('div','vl-r');r.append(VL_EL('span',0,k),VL_EL('b','vl-c'+i,VL_N[['bad','poor','average','good','great'][i]]+' · '+x));b.append(r)}
      }
      if(s.download){try{localStorage.setItem(VL_K,JSON.stringify([{t:Date.now(),d:s.download/1e6,u:s.upload/1e6,l:s.latency},...VL_HG()].slice(0,10)))}catch{}VL_HR()}
    };
    VL_E.play();
  }catch{VL_B(0);VL_E=null;VL_M('Error Velocidad (sin conexion?)')}
}
$('vl-rp').onclick=()=>VL_GO(1);
$('vl-cp').onclick=()=>VL_GO(0);
$('vl-pa').onclick=()=>{VL_E?.pause();VL_E=null;VL_B(0);VL_M('Detenido')};
document.addEventListener('contentUnload',()=>{VL_E?.pause();VL_E=null},{once:true});
VL_HR();
})();
</script>

</div>
