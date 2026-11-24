<canvas id="CC_C"></canvas>
<style>
#content{padding:0;margin:0;max-width:none;overflow:visible;z-index:auto;transform:none;filter:none;animation:none}
#content::before{display:none}
#disqus-container,#ad-slot{display:none!important}
#CC_C{position:fixed;inset:0;width:100%;height:100%;z-index:1;touch-action:none;user-select:none;-webkit-user-select:none;-webkit-touch-callout:none}
#compartir-enlace{position:relative;z-index:2;padding-top:24px}
</style>
<script>
!function(){
const a=document.getElementById('CC_C'),c=a.getContext('2d');
const EM=['\u{1F353}','\u{1F34A}','\u{1F34B}','\u{1F347}','\u{1F34F}','\u{1F36C}'];
let W=0,DR=1,E,R,C,cs,bx,by,Gv,T=[],st='',pr=null,sel=null,ds=null,sc=0,mv=0,cas=0,lk=0,PP=[],id=0,lt=performance.now(),best=+localStorage.getItem('CC_B')||0,SPR=[],dv=1;
const SG=(e,s)=>{const z=Math.ceil(s*1.4*DR),o=new OffscreenCanvas(z,z),x=o.getContext('2d');x.font=`${s*DR}px sans-serif`;x.textAlign='center';x.textBaseline='middle';x.fillText(e,z/2,z/2);return o};
const DI=(o,x,y,k)=>{const z=o.width/DR*k;c.drawImage(o,x-z/2,y-z/2,z,z)};
const vb=n=>navigator.vibrate&&navigator.vibrate(n);
const RN=()=>Math.random()*EM.length|0;
const GX=j=>bx+j*cs+cs/2,GY=i=>by+i*cs+cs/2;
const TY=()=>T.map(r=>r.map(t=>t?t.e:-1));
const NT=(e,i,j,y)=>({e,x:GX(j),y,tx:GX(j),ty:GY(i),vy:0,fl:1,al:1,dy:0});
function FM(m){
const s=new Set();
for(let i=0;i<R;i++)for(let j=0;j<C;j++){
const v=m[i][j];
if(v<0)continue;
if(j<C-2&&m[i][j+1]==v&&m[i][j+2]==v){s.add(i*C+j);s.add(i*C+j+1);s.add(i*C+j+2)}
if(i<R-2&&m[i+1][j]==v&&m[i+2][j]==v){s.add(i*C+j);s.add((i+1)*C+j);s.add((i+2)*C+j)}
}
return s;
}
function HM(m){
for(let i=0;i<R;i++)for(let j=0;j<C;j++)for(const[di,dj]of[[0,1],[1,0]]){
const i2=i+di,j2=j+dj;
if(i2>=R||j2>=C)continue;
const t=m[i][j];
m[i][j]=m[i2][j2];
m[i2][j2]=t;
const ok=FM(m).size>0;
m[i2][j2]=m[i][j];
m[i][j]=t;
if(ok)return true;
}
return false;
}
function BD(){
let m;
do{
m=Array.from({length:R},()=>Array(C).fill(0));
for(let i=0;i<R;i++)for(let j=0;j<C;j++)do m[i][j]=RN();while((j>1&&m[i][j-1]==m[i][j]&&m[i][j-2]==m[i][j])||(i>1&&m[i-1][j]==m[i][j]&&m[i-2][j]==m[i][j]));
}while(!HM(m));
T=m.map((row,i)=>row.map((e,j)=>NT(e,i,j,GY(i)-(R+1)*cs-(R-i)*cs*.2)));
st='fall';
}
function RT(){
if(sc>best){best=sc;localStorage.setItem('CC_B',best)}
sc=cas=0;
mv=30;
sel=ds=null;
PP=[];
BD();
}
function SX(i1,j1,i2,j2){
const p=T[i1][j1],q=T[i2][j2];
T[i1][j1]=q;
T[i2][j2]=p;
p.tx=GX(j2);p.ty=GY(i2);
q.tx=GX(j1);q.ty=GY(i1);
}
function SW(i1,j1,i2,j2){pr=[i1,j1,i2,j2];SX(i1,j1,i2,j2);st='swap';vb(8)}
function CR(s){
let sx=0,sy=0;
s.forEach(k=>{const t=T[k/C|0][k%C];t.dy=1;sx+=t.tx;sy+=t.ty});
const n=s.size,p=(n*10+(n-3)*5)*cas;
sc+=p;
PP.push({x:sx/n,y:sy/n,t:'+'+p,l:.9});
vb(12);
st='clear';
}
function GR(){
for(let j=0;j<C;j++){
let w=R-1;
for(let i=R-1;i>=0;i--){
const t=T[i][j];
if(t){if(i!=w){T[w][j]=t;T[i][j]=null;t.ty=GY(w);t.fl=1;t.vy=0}w--}
}
for(let i=w,k=1;i>=0;i--,k++)T[i][j]=NT(RN(),i,j,GY(0)-k*cs);
}
st='fall';
}
function U(d){
let mg=0;
for(const row of T)for(const t of row){
if(!t)continue;
if(t.dy){t.al=Math.max(0,t.al-d*5);if(t.al>0)mg=1;continue}
if(t.fl){t.vy+=Gv*d;t.y+=t.vy*d;if(t.y>=t.ty){t.y=t.ty;t.vy=0;t.fl=0}else mg=1}
else{
const k=Math.min(1,d*16);
t.x+=(t.tx-t.x)*k;
t.y+=(t.ty-t.y)*k;
if(Math.abs(t.tx-t.x)<.5&&Math.abs(t.ty-t.y)<.5){t.x=t.tx;t.y=t.ty}else mg=1;
}
}
for(const p of PP){p.y-=cs*.8*d;p.l-=d}
PP=PP.filter(p=>p.l>0);
lk-=d;
if(mg||PP.length||st!='idle'&&(st!='over'||lk>-.2))dv=1;
if(mg)return;
if(st=='swap'){
const s=FM(TY());
if(s.size){mv--;cas=1;CR(s)}else{SX(pr[0],pr[1],pr[2],pr[3]);st='back';vb(20)}
}else if(st=='back')st='idle';
else if(st=='clear'){
for(let i=0;i<R;i++)for(let j=0;j<C;j++)if(T[i][j]&&T[i][j].dy)T[i][j]=null;
GR();
}else if(st=='fall'){
const m=TY(),s=FM(m);
if(s.size){cas++;CR(s)}
else{
cas=0;
if(mv<=0){st='over';lk=.6}
else if(HM(m))st='idle';
else BD();
}
}
}
function D(){
c.clearRect(0,0,W,E);
c.textAlign='center';
c.textBaseline='middle';
if(sel){c.fillStyle='rgba(255,255,255,.28)';c.beginPath();c.arc(GX(sel[1]),GY(sel[0]),cs*.46,0,7);c.fill()}
for(const row of T)for(const t of row){
if(!t)continue;
c.globalAlpha=t.dy?t.al:1;
DI(SPR[t.e],t.x,t.y,t.dy?.4+.6*t.al:1);
}
c.globalAlpha=1;
c.shadowColor='#000';
c.shadowBlur=6;
c.font=`bold ${cs*.5|0}px sans-serif`;
c.fillStyle='#ffe066';
for(const p of PP){c.globalAlpha=Math.min(1,p.l*2);c.fillText(p.t,p.x,p.y)}
c.globalAlpha=1;
if(st=='over'){c.shadowBlur=0;c.fillStyle='rgba(0,0,0,.5)';c.fillRect(0,0,W,E);c.shadowBlur=6}
c.fillStyle='#fff';
c.font=`bold ${Math.max(16,E*.035|0)}px sans-serif`;
c.textBaseline='top';
c.textAlign='left';
c.fillText(`Mov ${mv}`,16,16);
c.textAlign='center';
c.fillText(sc,W/2,16);
c.textAlign='right';
c.fillText(`Mejor ${best}`,W-16,16);
if(st=='over'){c.textAlign='center';c.textBaseline='middle';c.fillText('Fin',W/2,E*.42);c.fillText(`Puntos ${sc}`,W/2,E*.5);if(lk<=0)c.fillText('Toca para reiniciar',W/2,E*.58)}
c.shadowBlur=0;
}
function LP(t){
id=requestAnimationFrame(LP);
if(!a.isConnected)return X();
const d=Math.max(0,Math.min((t-lt)/1e3,.05));
lt=t;
U(d);
if(dv){dv=0;D()}
}
function RS(){
const ch=innerWidth!=W,o=innerWidth<innerHeight;
DR=Math.min(2,devicePixelRatio||1);
a.width=(W=innerWidth)*DR;
a.height=(E=innerHeight)*DR;
c.setTransform(DR,0,0,DR,0,0);
C=o?7:9;
R=o?9:7;
cs=Math.floor(Math.min(W*.96/C,E*.78/R));
bx=(W-C*cs)/2;
by=(E-R*cs)/2+E*.04;
Gv=cs*45;
SPR=EM.map(e=>SG(e,cs*.8|0));
dv=1;
if(ch||T.length!=R||T[0].length!=C)RT();
else T.forEach((row,i)=>row.forEach((t,j)=>{if(t){t.tx=t.x=GX(j);t.ty=t.y=GY(i)}}));
}
function CL(x,y){
const j=Math.floor((x-bx)/cs),i=Math.floor((y-by)/cs);
return i<0||j<0||i>=R||j>=C?null:[i,j];
}
const LS=[[window,'resize',RS],[document,'contentUnload',X]];
function X(){cancelAnimationFrame(id);LS.forEach(([t,e,f])=>t.removeEventListener(e,f))}
a.onpointerdown=e=>{
dv=1;
if(st=='over'){if(lk<=0)RT();return}
if(st!='idle')return;
const q=CL(e.clientX,e.clientY);
if(!q)return;
if(sel&&Math.abs(sel[0]-q[0])+Math.abs(sel[1]-q[1])==1){SW(sel[0],sel[1],q[0],q[1]);sel=ds=null;return}
sel=sel&&sel[0]==q[0]&&sel[1]==q[1]?null:q;
ds=sel?{x:e.clientX,y:e.clientY}:null;
};
a.onpointermove=e=>{
if(!ds||!sel||st!='idle')return;
const dx=e.clientX-ds.x,dy=e.clientY-ds.y;
if(Math.max(Math.abs(dx),Math.abs(dy))<cs*.4)return;
const v=Math.abs(dy)>Math.abs(dx),i2=sel[0]+(v?Math.sign(dy):0),j2=sel[1]+(v?0:Math.sign(dx));
const s=sel;
sel=ds=null;
if(i2>=0&&j2>=0&&i2<R&&j2<C)SW(s[0],s[1],i2,j2);
};
a.onpointerup=a.onpointercancel=()=>{ds=null};
RS();
LS.forEach(([t,e,f])=>t.addEventListener(e,f));
id=requestAnimationFrame(LP);
}();
</script>