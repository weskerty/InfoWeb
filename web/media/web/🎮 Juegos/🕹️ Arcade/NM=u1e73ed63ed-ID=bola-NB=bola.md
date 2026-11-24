<canvas id="SK_C"></canvas>
<style>
#content{padding:0;margin:0;max-width:none;overflow:visible;z-index:auto;transform:none;filter:none;animation:none}
#content::before{display:none}
#disqus-container,#ad-slot{display:none!important}
#SK_C{position:fixed;inset:0;width:100%;height:100%;z-index:1;touch-action:none;user-select:none;-webkit-user-select:none;-webkit-touch-callout:none}
#compartir-enlace{position:relative;z-index:2;padding-top:24px}
</style>
<script>
!function(){
const a=document.getElementById('SK_C'),c=a.getContext('2d'),F=.7,L=document.body.classList.contains('low-perf')?33:99,ML=99/L,K={};
let W,E,S,x=0,y=0,z=0,v=0,g=0,sx=3,sw=3,R=[],J=0,T=0,N0=null,mx=0,tc=0,id=0,bf=0,ok=0,lt=performance.now();
const H=(q,s,l,al=1)=>c.fillStyle=`hsl(${q},${s}%,${l}%,${al})`;
const P=(px,py,d)=>{const k=S*F/d;return[W/2+(px-x+(d-3)**2/50*Math.cos((z+d)/49))*k,E/2-(py-2+d*d/50)*k,k]};
const jk=k=>k==' '||k=='ArrowUp'||k=='w';
function G(){for(;R.length<=(z+41|0);){const n=R.length,p=[];if(g<-8&&Math.random()<Math.min(.2,n/1e4))g=2+Math.min(4,n/400);if(Math.random()<.1){sw=2+Math.random()*3|0;sx=Math.max(0,Math.min(7-sw,sx-2+Math.random()*5|0))}g--;for(let j=7;j--;)p[j]=n+1<35|Math.random()>.9|g<0&sx<=j&j<sx+sw&Math.random()>Math.min(.2,z/1e4);R.push(p)}}
function Z(){x=y=z=v=g=0;sx=sw=3;R=[];G()}
function U(){
G();
if(y<=-4)return Z();
const k=(K.d|K.ArrowRight)-(K.a|K.ArrowLeft);
x+=T+(k?k*.1:mx/W/2-.25);
y+=v-=.006;
z+=Math.min(.5,.2+z/5e3);
if(y<0&y>-.3&R[z+3|0][Math.round(x+3)]){y=v=J;if(tc)J=0}
}
function D(){
c.clearRect(0,0,W,E);
for(let r=z+40|0;r>z;r--){
const t=[];
for(let i=7;i--;)if(R[r][i])t.push([i,P(i-3.5,0,r-z),P(i-2.5,0,r-z),P(i-3.5,0,r-z+1),P(i-2.5,0,r-z+1)]);
const q=99+(r>>7)*70,hh=(40-r+z)/30*S;
for(let j=2;j--;)for(const[i,[ax,ay],[bx,by],[ex,ey],[fx,fy]]of t){
const o=r+i&1;
if(j){H(q,60,30+o*9);c.fillRect(ex,ey,fx-ex,hh)}
else{H(q,60,9+o*5);c.fillRect(ax,ay,bx-ax,hh);H(q,60,60+o*30);c.beginPath();c.moveTo(ax,ay);c.lineTo(bx,by);c.lineTo(fx,fy);c.lineTo(ex,ey);c.fill()}
}
}
if(y>=0&R[z+3|0][Math.round(x+3)]){H(0,0,0,.5);const[px,py,s]=P(x,0,3);c.beginPath();c.ellipse(px,py,s/4,s/9,0,0,9);c.fill()}
for(let i=L;i--;){const k=i*ML;H(z/9-k/3,90,99-k*.7);const[px,py,s]=P(x+.1-k/1e3,y+.35-k/1e3,3);c.beginPath();c.ellipse(px,py,k*s/300,k*s/300,0,0,9);c.fill()}
}
function LP(t){
id=requestAnimationFrame(LP);
if(!a.isConnected)return X();
bf=Math.min(bf+t-lt,50);lt=t;
for(;bf>=16.67;bf-=16.67)U();
D();
}
function RS(){a.width=W=innerWidth;a.height=E=innerHeight;S=Math.min(E,W*.7)}
function OR(e){
if(e.gamma==null)return;
const n=screen.orientation?.angle||0,q=n==90?e.beta:n==270?-e.beta:n==180?-e.gamma:e.gamma;
if(N0==null)N0=q;
T=Math.max(-1,Math.min(1,(q-N0)/30))*.25;
}
const oc=()=>{N0=null},kd=e=>{K[e.key]=1;if(jk(e.key))J=.1},ku=e=>{K[e.key]=0;if(jk(e.key))J=0};
const LS=[[window,'keydown',kd],[window,'keyup',ku],[window,'resize',RS],[window,'deviceorientation',OR],[document,'contentUnload',X],...(screen.orientation?[[screen.orientation,'change',oc]]:[])];
function X(){cancelAnimationFrame(id);LS.forEach(([t,e,f])=>t.removeEventListener(e,f))}
const rp=()=>{
if(ok)return;
ok=1;
const D0=window.DeviceOrientationEvent;
if(D0&&typeof D0.requestPermission==='function')D0.requestPermission().then(r=>r==='granted'&&addEventListener('deviceorientation',OR)).catch(()=>{});
};
a.onpointerdown=e=>{tc=e.pointerType!=='mouse';J=.1;rp()};
a.onpointermove=e=>{tc=e.pointerType!=='mouse';mx=e.clientX};
a.onpointerup=a.onpointercancel=e=>{if(e.pointerType==='mouse')J=0;else mx=W/2};
RS();
mx=W/2;
Z();
LS.forEach(([t,e,f])=>t.addEventListener(e,f));
id=requestAnimationFrame(LP);
}();
</script>
