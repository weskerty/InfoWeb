<!-- Copie de https://www.reddit.com/r/webdev/comments/1v677vk/printmemoney_type_in_your_salary_and_watch_a/ -->

<div id="DS_root">
<h2>Cuanto Ganas?</h2>

<div class="DS_row">
<span>Gs</span>
<input id="DS_input" inputmode="numeric" value="2.800.000">
<span>/mes</span>
</div>

<button id="DS_btnStart" class="view-all-button">Iniciar</button>

<div id="DS_stage" class="hide">
<p class="DS_note">Esto es lo que ganrias si trabajaras 24/7 desde ahora</p>

<div class="DS_pair">
<div class="DS_side">
<div class="DS_label">Vos</div>
<div class="DS_workRow">👷 <span id="DS_workTime">00:00:00</span></div>
<div class="DS_printer">
<span class="DS_body">🖨️</span>
</div>
<div class="DS_bagRow"><span id="DS_youBags">💰 x0</span></div>
<div class="DS_billLine" id="DS_youBills"></div>
<div class="DS_rate" id="DS_youRate">Gs 0/s</div>
<div class="DS_counter">Gs <span id="DS_youCount">0</span></div>
</div>
<div class="DS_side">
<div class="DS_label">Elon Musk</div>
<div class="DS_printer">
<span class="DS_body">🖨️</span>
</div>
<div class="DS_bagRow"><span id="DS_elonBags">💰 x0</span></div>
<div class="DS_billLine" id="DS_elonBills"></div>
<div class="DS_rate" id="DS_elonRate">Gs 0/s</div>
<div class="DS_counter">Gs <span id="DS_elonCount">0</span></div>
</div>
</div>

<div class="DS_pauseRow">
<button id="DS_btnPause" class="back-button">Pausar</button>
<span class="DS_pauseNote">pero no trabajamos 24/7, asi que pausalo cuando no estes trabajando</span>
</div>

<p class="DS_note">Esto es lo que puedes comprar</p>
<div id="DS_milestones"></div>
<div id="DS_buyPop" class="hide"></div>
</div>

<img id="DS_richImg" class="hide" src="web/adjuntos/Contador_de_Jornales/imRich.avif" />

<style>
#DS_root{text-align:center}
.DS_row{display:flex;align-items:center;justify-content:center;gap:8px;margin:10px 0}
.DS_row input{width:160px;text-align:right}
.DS_note{margin:18px 0 10px;font-weight:600}
.DS_pair{display:flex;flex-wrap:wrap;justify-content:center;gap:24px}
.DS_side{width:200px}
.DS_label{font-weight:600;margin-bottom:6px}
.DS_printer{height:70px;display:flex;align-items:flex-end;justify-content:center}
.DS_body{font-size:2.6em;line-height:1}
.DS_bagRow{font-size:.9em;min-height:1.2em}
.DS_workRow{font-size:.85em;color:rgba(255,255,255,.7);margin-bottom:4px}
.DS_billLine{font-size:1em;min-height:1.3em;letter-spacing:1px;white-space:nowrap;overflow:hidden}
.DS_billLine span{display:inline-block;animation:DS_fall .3s ease-out}
@keyframes DS_fall{from{opacity:0;transform:translateY(-10px) scale(.5)}to{opacity:1;transform:translateY(0) scale(1)}}
.DS_rate{font-size:.8em;color:rgba(255,255,255,.55);margin-top:4px}
.DS_counter{margin-top:4px;font-size:1.3em;font-weight:700;word-break:break-all}
.DS_pauseRow{display:flex;flex-wrap:wrap;align-items:center;justify-content:center;gap:10px;margin:20px 0}
.DS_pauseNote{font-size:.82em;color:rgba(255,255,255,.55);max-width:280px;text-align:left}
#DS_milestones{display:flex;flex-wrap:wrap;gap:8px;justify-content:center}
.DS_chip{padding:6px 10px;border-radius:20px;background:rgba(255,255,255,.08);font-size:.82em;opacity:.4}
.DS_chip.hit{opacity:1;background:rgba(123,227,168,.18)}
#DS_buyPop{position:fixed;top:50%;left:50%;transform:translate(-50%,-50%);font-size:5em;z-index:50;animation:DS_popFx .9s ease-out forwards;pointer-events:none}
@keyframes DS_popFx{0%{opacity:0;transform:translate(-50%,-50%) scale(.3)}20%{opacity:1;transform:translate(-50%,-50%) scale(1.2)}70%{opacity:1;transform:translate(-50%,-50%) scale(1)}100%{opacity:0;transform:translate(-50%,-50%) scale(1)}}
</style>

<script>
(function(){
const GS_USD=6048;
const ELON_MES_USD=42860000000;
const elonSeg=(ELON_MES_USD*GS_USD)/30/24/3600;
const BILL_STEP=1000;
const BILL_PER_BAG=8;
let youSeg=0,youAcum=0,elonAcum=0,tId=null,paused=false,imgTId=null;
let youBillNext=BILL_STEP,elonBillNext=BILL_STEP;
let youLineCt=0,elonLineCt=0,youBags=0,elonBags=0,workSec=0;
const bought=new Set();
const MS=[
{n:"cocido",p:5000,e:"☕"},
{n:"1na milaneza con pure frio",p:25000,e:"🍛"},
{n:"recarga de gas",p:120000,e:"🔥"},
{n:"champium",p:350000,e:"👟"},
{n:"Nuevo Xiaomi Redmi Poco Ultra Max Leica 4k Full HD Android 29 con 67GB de RAM interna",p:2500000,e:"📱"},
{n:"alguna moto sin abs ni ninguna proteccion",p:10000000,e:"🏍"},
{n:"un terreno -1x-1",p:80000000,e:"🏡"},
{n:"coche que no pasa reglamento de seguridad",p:180000000,e:"🚗"}
];
function fmt(n){return Math.floor(n).toLocaleString("es-PY")}
function fmtHMS(s){
const h=String(Math.floor(s/3600)).padStart(2,"0");
const m=String(Math.floor(s%3600/60)).padStart(2,"0");
const sec=String(Math.floor(s%60)).padStart(2,"0");
return h+":"+m+":"+sec
}
function parseInp(v){return +v.replace(/\D/g,"")||0}
document.getElementById("DS_input").addEventListener("input",e=>{
const n=parseInp(e.target.value);
e.target.value=n?n.toLocaleString("es-PY"):""
});
function buildMilestones(){
const wrap=document.getElementById("DS_milestones");
wrap.innerHTML="";
MS.forEach((m,i)=>{
const c=document.createElement("span");
c.className="DS_chip";c.id="DS_ms"+i;
c.textContent=m.e+" "+m.n+" (Gs "+fmt(m.p)+")";
wrap.appendChild(c)
})
}
function popBuy(emoji){
const pop=document.getElementById("DS_buyPop");
pop.classList.remove("hide");
pop.textContent="";
void pop.offsetWidth;
pop.textContent=emoji;
pop.style.animation="none";
void pop.offsetWidth;
pop.style.animation=""
}
function checkMilestones(){
MS.forEach((m,i)=>{
const c=document.getElementById("DS_ms"+i);
if(youAcum>=m.p){
c.classList.add("hit");
if(!bought.has(i)){bought.add(i);popBuy(m.e)}
}
})
}
function addBills(side,n){
if(n<=0)return;
const lineEl=document.getElementById(side==="you"?"DS_youBills":"DS_elonBills");
const bagEl=document.getElementById(side==="you"?"DS_youBags":"DS_elonBags");
let ct=side==="you"?youLineCt:elonLineCt;
let bags=side==="you"?youBags:elonBags;
const animMax=BILL_PER_BAG;
const toAnim=Math.min(n,animMax*2);
const skip=n-toAnim;
if(skip>0){
ct+=skip;
bags+=Math.floor(ct/BILL_PER_BAG);
ct=ct%BILL_PER_BAG;
lineEl.textContent=""
}
for(let k=0;k<toAnim;k++){
ct++;
if(ct>BILL_PER_BAG){bags++;ct=1;lineEl.textContent=""}
const b=document.createElement("span");
b.textContent="💵";
lineEl.appendChild(b)
}
if(side==="you"){youLineCt=ct;youBags=bags}else{elonLineCt=ct;elonBags=bags}
bagEl.textContent="💰 x"+bags
}
document.getElementById("DS_btnStart").addEventListener("click",()=>{
const mensual=parseInp(document.getElementById("DS_input").value);
youSeg=mensual/240/3600;
document.getElementById("DS_youRate").textContent="Gs "+fmt(youSeg)+"/s";
document.getElementById("DS_elonRate").textContent="Gs "+fmt(elonSeg)+"/s";
document.getElementById("DS_stage").classList.remove("hide");
buildMilestones();
document.getElementById("DS_btnStart").disabled=true;
youBillNext=BILL_STEP;elonBillNext=BILL_STEP;youLineCt=0;elonLineCt=0;youBags=0;elonBags=0;workSec=0;
document.getElementById("DS_workTime").textContent="00:00:00";
document.getElementById("DS_youBags").textContent="💰 x0";
document.getElementById("DS_elonBags").textContent="💰 x0";
document.getElementById("DS_youBills").textContent="";
document.getElementById("DS_elonBills").textContent="";
document.getElementById("DS_richImg").classList.add("hide");
if(imgTId)clearTimeout(imgTId);
imgTId=setTimeout(()=>{document.getElementById("DS_richImg").classList.remove("hide")},10000);
if(tId)clearInterval(tId);
tId=setInterval(()=>{
if(!paused){
workSec+=0.1;
document.getElementById("DS_workTime").textContent=fmtHMS(workSec);
youAcum+=youSeg/10;
document.getElementById("DS_youCount").textContent=fmt(youAcum);
checkMilestones();
if(youAcum>=youBillNext){
const nNew=Math.floor((youAcum-youBillNext)/BILL_STEP)+1;
youBillNext+=nNew*BILL_STEP;
addBills("you",nNew)
}
}
elonAcum+=elonSeg/10;
document.getElementById("DS_elonCount").textContent=fmt(elonAcum);
if(elonAcum>=elonBillNext){
const nNew=Math.floor((elonAcum-elonBillNext)/BILL_STEP)+1;
elonBillNext+=nNew*BILL_STEP;
addBills("elon",nNew)
}
},100)
});
document.getElementById("DS_btnPause").addEventListener("click",e=>{
paused=!paused;
e.target.textContent=paused?"Reanudar":"Pausar"
});
})();
</script>
</div>