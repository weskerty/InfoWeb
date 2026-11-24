<canvas id="TW_C"></canvas>
<style>
#content{padding:0;margin:0;max-width:none;overflow:visible;z-index:auto;transform:none;filter:none;animation:none}
#content::before{display:none}
#disqus-container,#ad-slot{display:none!important}
#TW_C{position:fixed;inset:0;width:100%;height:100%;z-index:1;touch-action:none;user-select:none;-webkit-user-select:none;-webkit-touch-callout:none}
#compartir-enlace{position:relative;z-index:2;padding-top:24px}
</style>
<script>
!function(){
const a=document.getElementById('TW_C'),c=a.getContext('2d');
const RG=(s,n)=>Array.from({length:n},(_,i)=>String.fromCodePoint(s+i));
const EM=[...RG(0x1F345,59),...RG(0x1F400,63)];
let W=0,DR=1,E,h,p,L,Y0,Gv,B=[],bl=null,PY=0,cy=0,sg=1,go=0,sc=0,TL=0,TV=0,TF=0,tt=0,sw=0,id=0,lt=performance.now(),best=+localStorage.getItem('TW_B')||0,SM=new Map();
const SG=(e,s)=>{const z=Math.ceil(s*1.4*DR),o=new OffscreenCanvas(z,z),x=o.getContext('2d');x.font=`${s*DR}px sans-serif`;x.textAlign='center';x.textBaseline='middle';x.fillText(e,z/2,z/2);return o};
const GS=(e,s)=>{const k=e+s;let o=SM.get(k);if(!o)SM.set(k,o=SG(e,s));return o};
const DI=(o,x,y)=>{const z=o.width/DR;c.drawImage(o,x-z/2,y-z/2,z,z)};
const SH=document.getElementById('sh'),ST=()=>{const n=Math.max(best,sc);if(SH&&n)SH.dataset.t=`Arme una Torre de ${n} Pisos, Podras Superarme? Intentalo en`};
const vb=n=>navigator.vibrate&&navigator.vibrate(n);
const RE=()=>{let e;do e=EM[Math.random()*EM.length|0];while(B.length&&e==B[B.length-1].e);return e};
const MG=()=>Math.max(h*.28,h*.6-sc*.012*h);
const TP=()=>{let s=0;for(let k=B.length-1;k>0;k--){s+=B[k].ox;const m=s/(B.length-k)-B[k-1].ox;if(Math.abs(m)>h*.5)return m}return 0};
const CM=()=>B.length>1?B.slice(1).reduce((s,f)=>s+f.ox,0)/(B.length-1):0;
function NB(){sg=-sg;bl={e:RE(),ph:sg*Math.PI/2,A:Math.min(.95,.45+sc*.012),om:Math.min(3,1.5+sc*.03),x:W/2,y:0,vx:0,vy:0,a:0,w:0,f:0,lk:.2}}
function RT(){
if(sc>best){best=sc;localStorage.setItem('TW_B',best)}
sc=go=cy=TL=TV=TF=0;
B=[{e:RE(),ox:0}];
PY=Y0-2*h-L;
NB();
}
function DP(){if(go||!bl||bl.f||bl.lk>0)return;bl.f=1}
function LD(){
const T=B[B.length-1],dx=bl.x-W/2-T.ox-sw*(B.length-1),ad=Math.abs(dx);
if(ad<=MG()){
const pr=ad<=h*.12;
B.push({e:bl.e,ox:pr?T.ox:T.ox+dx});
const tp=TP();
if(tp){TF=Math.sign(tp);bl=null;go=1.8;vb(150);return}
sc+=pr?2:1;
ST();
vb(pr?[10,30,10]:12);
NB();
}else{
const s=dx>0?1:-1;
bl.f=2;
if(ad<h*1.2)bl.vy=-Math.abs(bl.vy)*.25;
bl.vx=s*Math.max(Math.abs(bl.vx),h*3);
bl.w=s*4;
go=1.2;
vb(80);
}
}
function U(d){
if(bl){
if(!bl.f){
bl.ph+=bl.om*d;
const th=bl.A*Math.sin(bl.ph),td=bl.A*bl.om*Math.cos(bl.ph);
bl.x=W/2+L*Math.sin(th);
bl.y=PY+L*Math.cos(th);
bl.a=th*.6;
bl.vx=L*Math.cos(th)*td;
bl.vy=-L*Math.sin(th)*td;
bl.lk-=d;
}else{
bl.vy+=Gv*d;
bl.x+=bl.vx*d;
bl.y+=bl.vy*d;
bl.a+=bl.w*d;
if(bl.f==1&&bl.vy>0&&bl.y>=Y0-B.length*p){bl.y=Y0-B.length*p;LD()}
}
}
tt+=d;
sw=TF?0:h*.015*Math.min(1,Math.abs(CM())/(h*.5))*Math.sin(tt*2.2);
if(TF){TV+=TF*3*d;TL+=TV*d}
PY+=(Y0-(B.length-1)*p-2*h-L-PY)*Math.min(1,d*6);
cy+=(Math.max(0,E*.72-(Y0-(B.length-1)*p))-cy)*Math.min(1,d*5);
if(go){go-=d;if(go<=0)RT()}
}
function D(){
c.clearRect(0,0,W,E);
c.save();
c.translate(W/2,Y0+cy);
c.rotate(TL);
B.forEach((f,i)=>{const y=Y0-i*p+cy;if(TF||y<E+h&&y>-h)DI(GS(f.e,h),f.ox+sw*i,-i*p)});
c.restore();
const px=W/2,py=PY+cy;
c.strokeStyle='rgba(255,255,255,.8)';
c.lineWidth=2;
c.beginPath();
c.moveTo(px,py);
if(bl&&!bl.f)c.lineTo(bl.x,bl.y+cy);
else c.lineTo(px,py+L);
c.stroke();
DI(GS('\u{1F3D7}\uFE0F',h*1.4|0),px,py-h*.4);
if(bl){
c.save();
c.translate(bl.x,bl.y+cy);
c.rotate(bl.a);
DI(GS(bl.e,h),0,0);
c.restore();
}
c.shadowColor='#000';
c.shadowBlur=6;
c.fillStyle='#fff';
c.font=`bold ${Math.max(16,E*.04|0)}px sans-serif`;
c.textBaseline='top';
c.textAlign='center';
c.fillText(sc,W/2,16);
if(!sc&&B.length==1)c.fillText('Toca para soltar',W/2,E*.93);
c.textAlign='right';
c.fillText(`Mejor ${best}`,W-16,16);
c.shadowBlur=0;
}
function LP(t){
id=requestAnimationFrame(LP);
if(!a.isConnected)return X();
const d=Math.max(0,Math.min((t-lt)/1e3,.05));
lt=t;
U(d);
D();
}
function RS(){
const ch=innerWidth!=W;
DR=Math.min(2,devicePixelRatio||1);
a.width=(W=innerWidth)*DR;
a.height=(E=innerHeight)*DR;
c.setTransform(DR,0,0,DR,0,0);
h=Math.max(34,Math.min(56,Math.min(W,E)*.09))|0;
p=h*.92;
L=E*.2;
Y0=E*.86;
Gv=E*2.2;
SM.clear();
if(ch)RT();
}
const kd=e=>{if(e.key==' '||e.key=='Enter')DP()};
const LS=[[window,'resize',RS],[window,'keydown',kd],[document,'contentUnload',X]];
function X(){cancelAnimationFrame(id);LS.forEach(([t,e,f])=>t.removeEventListener(e,f))}
a.onpointerdown=DP;
RS();
ST();
LS.forEach(([t,e,f])=>t.addEventListener(e,f));
id=requestAnimationFrame(LP);
}();
</script>

<div id="sh"></div>
