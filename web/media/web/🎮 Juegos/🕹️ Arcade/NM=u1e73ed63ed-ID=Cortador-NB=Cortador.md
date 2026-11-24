<canvas id="CF_C"></canvas>
<style>
#content{padding:0;margin:0;max-width:none;overflow:visible;z-index:auto;transform:none;filter:none;animation:none}
#content::before{display:none}
#disqus-container,#ad-slot{display:none!important}
#CF_C{position:fixed;inset:0;width:100%;height:100%;z-index:1;touch-action:none;user-select:none;-webkit-user-select:none;-webkit-touch-callout:none}
#compartir-enlace{position:relative;z-index:2;padding-top:24px}
</style>
<script>
!function(){
const a=document.getElementById('CF_C'),c=a.getContext('2d'),RD=Math.PI*2;
const EF=['\u{1F3ED}','\u2622\uFE0F','\u2623\uFE0F','\u{1F6E2}\uFE0F','\u{1F6AC}','\u{1F5D1}\uFE0F','\u{1F32B}\uFE0F','\u26FD','\u{1F525}','\u{1F697}','\u{1F964}','\u{1F50B}'],EC=['\u{1F431}','\u{1F408}','\u{1F63A}','\u{1F638}','\u{1F63B}','\u{1F640}','\u{1F639}','\u{1F63C}'];
const PK=a=>a[Math.random()*a.length|0];
let W,DR=1,E,Gv,Ob=[],PT=[],TR=[],pp=0,sc=0,lv=3,sp=.5,fl=0,id=0,lt=performance.now(),best=+localStorage.getItem('CF_B')||0,SM=new Map();
const SG=(e,s)=>{const z=Math.ceil(s*1.4*DR),o=new OffscreenCanvas(z,z),x=o.getContext('2d');x.font=`${s*DR}px sans-serif`;x.textAlign='center';x.textBaseline='middle';x.fillText(e,z/2,z/2);return o};
const GS=(e,s)=>{const k=e+s;let o=SM.get(k);if(!o)SM.set(k,o=SG(e,s));return o};
const vb=n=>navigator.vibrate&&navigator.vibrate(n);
const DS=(px,py,ax,ay,bx,by)=>{const dx=bx-ax,dy=by-ay,l=dx*dx+dy*dy||1,t=Math.max(0,Math.min(1,((px-ax)*dx+(py-ay)*dy)/l));return Math.hypot(px-ax-t*dx,py-ay-t*dy)};
function PC(V){let A=0,cx=0,cy=0;for(let i=0;i<V.length;i++){const p=V[i],q=V[(i+1)%V.length],f=p[0]*q[1]-q[0]*p[1];A+=f;cx+=(p[0]+q[0])*f;cy+=(p[1]+q[1])*f}const s=A/2;return[Math.abs(s),cx/(6*s),cy/(6*s)]}
function SL(V,p0,dl){
const A=[],B=[],tt=[],n=V.length,d=V.map(v=>dl[0]*(v[1]-p0[1])-dl[1]*(v[0]-p0[0]));
for(let i=0;i<n;i++){
const v=V[i],w=V[(i+1)%n],dv=d[i],dw=d[(i+1)%n],sa=dv>=0,S=sa?A:B,O=sa?B:A;
S.push(v);
if(sa!=(dw>=0)){const t=dv/(dv-dw),mx=v[0]+t*(w[0]-v[0]),my=v[1]+t*(w[1]-v[1]);S.push([mx,my]);O.push([mx,my]);tt.push((mx-p0[0])*dl[0]+(my-p0[1])*dl[1])}
}
return[A,B,tt];
}
function PS(x,y,n,col,s0){for(let i=0;i<n;i++){const g=Math.random()*RD,s=s0*(.3+Math.random());PT.push({x,y,vx:Math.cos(g)*s,vy:Math.sin(g)*s-s0*.3,l:.5+Math.random()*.4,col})}}
function RT(){if(sc>best){best=sc;localStorage.setItem('CF_B',best)}sc=0;lv=3;Ob=[];PT=[];sp=.5;fl=0}
function BM(o){vb([80,40,120]);PS(o.x,o.y,28,'#e33',E*.7);fl=1;return--lv<=0}
function SP(bm){
const r=Math.max(24,Math.min(60,Math.min(W,E)*.09)),h=E*(.55+Math.random()*.3);
const o={x:W*(.2+Math.random()*.6),y:E+r,vx:(Math.random()-.5)*W*.4,vy:-Math.sqrt(2*Gv*h),a:0,w:(Math.random()-.5)*6,r,e:PK(bm?EC:EF),f:bm?0:1,ox:0,oy:0,br:r*1.42,V:[[-r,-r],[r,-r],[r,r],[-r,r]],b:bm};
o.ar=PC(o.V)[0];
Ob.push(o);
}
function CT(p,q){
const dx=q.x-p.x,dy=q.y-p.y,l=Math.hypot(dx,dy),ux=dx/l,uy=dy/l,nx=-uy,ny=ux,sv=Math.min(l/Math.max(.008,(q.t-p.t)/1e3),E*2.5),s0=E*.12+sv*.05,s1=sv*.12,keep=[],nw=[];
let n=0,dead=0;
for(const o of Ob){
const mn=o.r*o.r*.2;
if(DS(o.x,o.y,p.x,p.y,q.x,q.y)>o.br||!o.b&&o.ar<mn*2){keep.push(o);continue}
const cs=Math.cos(o.a),sn=Math.sin(o.a),px=p.x-o.x,py=p.y-o.y,[A,B,tt]=SL(o.V,[px*cs+py*sn,-px*sn+py*cs],[ux*cs+uy*sn,-ux*sn+uy*cs]);
if(A.length<3||B.length<3||Math.max(...tt)<0||Math.min(...tt)>l){keep.push(o);continue}
if(o.b){if(BM(o))dead=1;continue}
const ch=[A,B].map(V=>{const[ar,cx,cy]=PC(V);return{V,ar,cx,cy}});
if(!(ch[0].ar>=mn)||!(ch[1].ar>=mn)){keep.push(o);continue}
n++;
PS(o.x,o.y,5,'#fff',E*.25);
ch.forEach((h,k)=>{
const s=k?-1:1,ox=h.cx*cs-h.cy*sn,oy=h.cx*sn+h.cy*cs,V=h.V.map(v=>[v[0]-h.cx,v[1]-h.cy]);
nw.push({...o,x:o.x+ox,y:o.y+oy,vx:o.vx-o.w*oy+s*nx*s0+ux*s1,vy:o.vy+o.w*ox+s*ny*s0+uy*s1,w:o.w+(Math.random()-.5)*2,V,ox:o.ox-h.cx,oy:o.oy-h.cy,ar:h.ar,f:0,br:Math.max(...V.map(v=>Math.hypot(v[0],v[1])))});
});
}
Ob=keep.concat(nw);
if(dead)return RT();
if(n){sc+=n*n;vb(15)}
}
function U(d){
sp-=d;
if(sp<=0){const bp=Math.min(.28,.08+sc*.004);for(let k=0;k<1+(sc>15&&Math.random()<.4);k++)SP(Math.random()<bp);sp=Math.max(.35,1-sc*.012)+Math.random()*.4}
const k=Math.max(0,1-.12*d);
for(const o of Ob){o.vy+=Gv*d;o.vx*=k;o.vy*=k;o.x+=o.vx*d;o.y+=o.vy*d;o.a+=o.w*d}
let dead=0;
Ob=Ob.filter(o=>{
if(o.y-o.br>E&&o.vy>0){if(o.f){vb(60);if(--lv<=0)dead=1}return false}
return o.x>-o.br*3&&o.x<W+o.br*3;
});
PT=PT.filter(p=>{p.vy+=Gv*d*.6;p.x+=p.vx*d;p.y+=p.vy*d;p.l-=d;return p.l>0});
fl=Math.max(0,fl-d*2);
if(dead)RT();
}
function DI(o){
c.save();
c.translate(o.x,o.y);
c.rotate(o.a);
if(o.ox||o.oy){c.beginPath();o.V.forEach((v,k)=>k?c.lineTo(v[0],v[1]):c.moveTo(v[0],v[1]));c.clip()}
const s=GS(o.e,o.r*1.6|0),z=s.width/DR;
c.drawImage(s,o.ox-z/2,o.oy-z/2,z,z);
c.restore();
}
function D(){
c.clearRect(0,0,W,E);
for(const o of Ob)DI(o);
for(const p of PT){c.globalAlpha=Math.min(1,p.l*2);c.fillStyle=p.col;c.fillRect(p.x-2,p.y-2,4,4)}
c.globalAlpha=1;
const n=performance.now();
TR=TR.filter(p=>n-p.t<180);
for(let i=1;i<TR.length;i++){
const k=1-(n-TR[i].t)/180;
c.strokeStyle=`rgba(255,255,255,${k})`;
c.lineWidth=2+k*6;
c.beginPath();
c.moveTo(TR[i-1].x,TR[i-1].y);
c.lineTo(TR[i].x,TR[i].y);
c.stroke();
}
if(fl){c.fillStyle=`rgba(255,60,60,${fl*.45})`;c.fillRect(0,0,W,E)}
c.fillStyle='#fff';
c.shadowColor='#000';
c.shadowBlur=6;
c.font=`bold ${Math.max(16,E*.04|0)}px sans-serif`;
c.textBaseline='top';
c.textAlign='left';
c.fillText(`${sc}  ${'\u2665'.repeat(lv)}`,16,16);
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
function RS(){DR=Math.min(2,devicePixelRatio||1);a.width=(W=innerWidth)*DR;a.height=(E=innerHeight)*DR;c.setTransform(DR,0,0,DR,0,0);Gv=E*1.4;SM.clear()}
const LS=[[window,'resize',RS],[document,'contentUnload',X]];
function X(){cancelAnimationFrame(id);LS.forEach(([t,e,f])=>t.removeEventListener(e,f))}
a.onpointerdown=e=>{pp={x:e.clientX,y:e.clientY,t:performance.now()};TR=[pp]};
a.onpointermove=e=>{
if(!e.buttons||!pp){pp=0;return}
const q={x:e.clientX,y:e.clientY,t:performance.now()};
TR.push(q);
if(Math.hypot(q.x-pp.x,q.y-pp.y)<14)return;
CT(pp,q);
pp=q;
};
a.onpointerup=a.onpointercancel=()=>{pp=0};
RS();
LS.forEach(([t,e,f])=>t.addEventListener(e,f));
id=requestAnimationFrame(LP);
}();
</script>