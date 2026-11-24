<style>
*{margin:0;padding:0;box-sizing:border-box}
#gameCanvas{display:block;cursor:none;position:fixed;top:0;left:0;z-index:1}
#muteBtn{position:fixed;top:calc(16px + env(safe-area-inset-top,0px));right:calc(16px + env(safe-area-inset-right,0px));z-index:20;background:rgba(0,0,0,.65);border:1px solid rgba(255,255,255,.22);border-radius:8px;color:#fff;font-size:18px;padding:5px 11px;cursor:pointer;pointer-events:all;transition:background .2s}
#muteBtn:hover{background:rgba(255,255,255,.15)}
#vtKills{display:block;position:fixed;top:calc(16px + env(safe-area-inset-top,0px));left:50%;transform:translateX(-50%);background:rgba(0,0,0,.55);border:1px solid rgba(255,255,255,.18);border-radius:8px;padding:5px 14px;color:#fff;font-size:12px;letter-spacing:2px;z-index:15;pointer-events:none;white-space:nowrap;font-family:system-ui,-apple-system,'Segoe UI',Arial,sans-serif}
#vtNet{display:block;position:fixed;top:calc(16px + env(safe-area-inset-top,0px));left:calc(16px + env(safe-area-inset-left,0px));background:rgba(0,0,0,.55);border:1px solid rgba(255,255,255,.18);border-radius:8px;padding:5px 12px;color:rgba(255,255,255,.7);font-size:11px;letter-spacing:1px;z-index:15;pointer-events:none;white-space:nowrap;font-family:system-ui,-apple-system,'Segoe UI',Arial,sans-serif}
#mapBadge{display:none;position:fixed;top:calc(62px + env(safe-area-inset-top,0px));left:50%;transform:translateX(-50%);background:rgba(0,0,0,.72);border:1px solid rgba(255,200,0,.32);border-radius:20px;padding:5px 20px;color:rgba(255,200,0,.92);font-size:12px;letter-spacing:3px;z-index:15;pointer-events:none;transition:opacity .5s;font-family:system-ui,-apple-system,'Segoe UI',Arial,sans-serif}
#mobile-controls{display:block;position:fixed;bottom:env(safe-area-inset-bottom,0px);left:0;width:100%;height:220px;z-index:15;pointer-events:none}
.stick-zone{position:absolute;bottom:calc(20px + env(safe-area-inset-bottom,0px));width:170px;height:170px;pointer-events:all;touch-action:none}
#left-zone{left:calc(24px + env(safe-area-inset-left,0px))}
#right-zone{right:calc(24px + env(safe-area-inset-right,0px))}
.stick-base{position:absolute;top:0;left:0;width:100%;height:100%;background:rgba(255,255,255,.06);border:2px solid rgba(255,255,255,.2);border-radius:50%}
.stick-nub{position:absolute;width:52px;height:52px;background:rgba(255,255,255,.3);border:2px solid rgba(255,255,255,.5);border-radius:50%;top:50%;left:50%;transform:translate(-50%,-50%);pointer-events:none;transition:background .1s}
#right-nub{background:rgba(255,80,80,.4);border-color:rgba(255,130,130,.7)}
#right-nub.firing{background:rgba(255,200,0,.7)}
.stick-label{position:absolute;bottom:-20px;width:100%;text-align:center;font-size:10px;color:rgba(255,255,255,.3);font-family:Arial,sans-serif;letter-spacing:1px;text-transform:uppercase}
</style>

<canvas id="gameCanvas"></canvas>
<div id="vtKills">KILLS 0</div>
<div id="vtNet">NET: conectando...</div>
<button id="muteBtn" title="Mute">🔊</button>
<div id="mapBadge"></div>
<div id="mobile-controls">
  <div class="stick-zone" id="left-zone">
    <div class="stick-base"></div>
    <div class="stick-nub" id="left-nub"></div>
    <div class="stick-label">MOVER</div>
  </div>
  <div class="stick-zone" id="right-zone">
    <div class="stick-base"></div>
    <div class="stick-nub" id="right-nub"></div>
    <div class="stick-label">APUNTAR Y DISPARAR</div>
  </div>
</div>

<script>
!function(){
'use strict';
const $=(()=>{const c={};return id=>c[id]||(c[id]=document.getElementById(id));})();
const contentEl=document.getElementById('content');
const ctPrev=contentEl?contentEl.getAttribute('style'):null;
const bodyOverflowPrev=document.body.style.overflow;
if(contentEl){
  contentEl.style.position='fixed';
  contentEl.style.inset='0';
  contentEl.style.padding='0';
  contentEl.style.margin='0';
  contentEl.style.maxWidth='none';
  contentEl.style.background='transparent';
  contentEl.style.backdropFilter='none';
  contentEl.style.webkitBackdropFilter='none';
  contentEl.style.boxShadow='none';
  contentEl.style.border='none';
  contentEl.style.transform='none';
  contentEl.style.overflow='hidden';
}
document.body.style.overflow='hidden';
const adSlotEl=document.getElementById('ad-slot');
const adSlotPrev=adSlotEl?adSlotEl.style.display:null;
if(adSlotEl)adSlotEl.style.display='none';
const disqusEl=document.getElementById('disqus-container');
const disqusPrev=disqusEl?disqusEl.style.display:null;
if(disqusEl)disqusEl.style.display='none';

const canvas=$('gameCanvas');
const ctx=canvas.getContext('2d');
function normAngle(a){ while(a>Math.PI)a-=Math.PI*2; while(a<-Math.PI)a+=Math.PI*2; return a; }

const TUNE={
  TANK_OBS_R:24, TANK_SEP:48, BULLET_HIT_R:28, MISSILE_HIT_R:46,
  AI_RETREAT_DIST:150, AI_HUNT_DIST:350, AI_FLANK_MAX:760,
  ENGINE_SND_EVERY:8, TANK_BASE_SPEED:2.8, TANK_BASE_FIRE:45, CRUSH_R:62,
  TOUCH_DEAD:0.20, TOUCH_FIRE:0.15, TOUCH_AIM_SPD:0.22
};

let roster=[], localEntry=null, aiEntry=null;
let touchMode=true, usingGamepad=false, padPrev=[[]];
let mouseX=0, mouseY=0, rightActive=false;
let engineFrames=0, gameFrame=0;
let hitstopSteps=0, shakeT=0, shakeDur=1, shakeMag=0;
const keys={};
const REDUCED_MOTION=(()=>{try{return matchMedia('(prefers-reduced-motion: reduce)').matches;}catch(e){return false;}})();
let optImpact=!REDUCED_MOTION;
function buzz(pattern){ if(!optImpact) return; try{ if(navigator.vibrate) navigator.vibrate(pattern); }catch(e){} }
function addShake(mag,frames){ if(!optImpact) return; if(mag>shakeMag||shakeT<=0){shakeMag=mag;shakeDur=frames;} shakeT=Math.max(shakeT,frames); }
function addHitstop(steps){ if(!optImpact) return; hitstopSteps=Math.max(hitstopSteps,steps); }
const hasTouch='ontouchstart' in window || navigator.maxTouchPoints>0;
const optDifficulty=hasTouch?'easy':'normal';
const AI_DIFF={
  easy:{aim:0.55,jit:0.15,react:28,move:0.85},
  normal:{aim:0.80,jit:0.065,react:13,move:1.0},
  hard:{aim:1.05,jit:0.015,react:4,move:1.05}
};
const optFieldL=15;
const fieldIsDark=()=>optFieldL<10;

let isMuted=false;
try{ if(localStorage.getItem('vt_muted')==='1') isMuted=true; }catch(e){}
function onMuteClick(){
  isMuted=!isMuted;
  try{ localStorage.setItem('vt_muted',isMuted?'1':'0'); }catch(e){}
  $('muteBtn').textContent=isMuted?'🔇':'🔊';
}
$('muteBtn').addEventListener('click',onMuteClick);
$('muteBtn').textContent=isMuted?'🔇':'🔊';

let audioCtx=null;
let MASTER=null;
function masterBus(ac){
  if(!MASTER || MASTER.ctx!==ac){
    const g=ac.createGain(); g.gain.value=0.5;
    g.connect(ac.destination);
    MASTER={ctx:ac, node:g};
  }
  return MASTER.node;
}
function getAudio() {
  if (!audioCtx) {
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    audioCtx.onstatechange = ()=>{ try{
      if(audioCtx.state!=='running' && !document.hidden) audioCtx.resume();
    }catch(e){} };
  }
  return audioCtx;
}

const NOISE_BUFS={};
function noiseBuf(ac,key,dur,pow){
  if(!NOISE_BUFS[key]){
    const len=Math.floor(ac.sampleRate*dur), buf=ac.createBuffer(1,len,ac.sampleRate), d=buf.getChannelData(0);
    for(let i=0;i<len;i++) d[i]=(Math.random()*2-1)*Math.pow(1-i/len,pow);
    NOISE_BUFS[key]=buf;
  }
  return NOISE_BUFS[key];
}

let musicGain=null, musicTimer=null, musicStep=0, musicNextT=0;
const MUS_STEP_NORMAL=0.13, MUS_STEP_FRENZY=0.098;
const MUS_STEPS=128;

const N={E2:82.41,D2:73.42,G2:98.0,A2:110.0,B1:61.74,C2:65.41,
         E3:164.81,G3:196.0,B3:246.94,C3:130.81,D3:146.83,FS3:185.0,A3:220.0,
         D4:293.66,E4:329.63,FS4:369.99,G4:392.0,A4:440.0};
const OST=[N.E2,N.E2,N.D2,N.E2,N.E2,N.E2,N.G2,N.D2];
const HORNS=[
  [0,[N.E3,N.G3,N.B3],1],[1,[N.C3,N.E3,N.G3],1],[2,[N.D3,N.FS3,N.A3],1],[3,[N.E3,N.G3,N.B3,N.E2],1],
];
const LEAD=[
  [0,N.E4,2,0],[0,N.G4,2,4],[0,N.FS4,2,8],[0,N.E4,2,12],
  [1,N.G4,2,0],[1,N.A4,2,4],[1,N.G4,1,8],[1,N.FS4,1,10],[1,N.D4,2,12],
  [2,N.E4,2,0],[2,N.D4,2,4],[2,N.E4,2,8],[2,N.G4,2,12],
  [3,N.FS4,1,0],[3,N.G4,1,2],[3,N.FS4,2,4],[3,N.D4,2,8],[3,N.E4,2,12],
  [6,N.G4,2,0],[6,N.FS4,2,4],[6,N.E4,2,8],[6,N.D4,2,12],
  [7,N.E4,3,0],[7,N.D4,1,6],[7,N.E4,2,8],[7,N.G4,2,12],
];
const GTR_A=[N.E2,N.E2,N.G2,N.E2,N.D2,N.D2,N.E2,N.G2];
const GTR_B=[N.E2,N.G2,N.A2,N.G2,N.E2,N.D2,N.E2,N.E2];
const GTR_CURVE=(()=>{ const c=new Float32Array(256);
  for(let i=0;i<256;i++){ const x=i*2/256-1; c[i]=Math.tanh(3.2*x); } return c; })();

const reap=(s,...ns)=>{ s.onended=()=>{ try{s.disconnect()}catch(e){} for(const n of ns){ try{n.disconnect()}catch(e){} } }; };
function musicMasterGain(ac){
  if(!musicGain){ musicGain=ac.createGain(); musicGain.gain.value=0.16; musicGain.connect(masterBus(ac)); }
  return musicGain;
}
function musKick(ac,t,big){
  const o=ac.createOscillator(),g=ac.createGain();
  o.type='sine';
  o.frequency.setValueAtTime(big?130:110,t); o.frequency.exponentialRampToValueAtTime(34,t+0.22);
  g.gain.setValueAtTime(big?0.9:0.6,t); g.gain.exponentialRampToValueAtTime(0.001,t+0.28);
  o.connect(g); g.connect(musicMasterGain(ac)); o.start(t); o.stop(t+0.3); reap(o,g);
  if(big){
    const src=ac.createBufferSource(); src.buffer=noiseBuf(ac,'taiko',0.18,2.5);
    const f=ac.createBiquadFilter(); f.type='lowpass'; f.frequency.value=260;
    const ng=ac.createGain(); ng.gain.setValueAtTime(0.5,t); ng.gain.exponentialRampToValueAtTime(0.001,t+0.18);
    src.connect(f); f.connect(ng); ng.connect(musicMasterGain(ac)); src.start(t); src.stop(t+0.18); reap(src,f,ng);
  }
}
function musSnare(ac,t){
  const src=ac.createBufferSource(); src.buffer=noiseBuf(ac,'snare',0.11,1.6);
  const f=ac.createBiquadFilter(); f.type='bandpass'; f.frequency.value=1900; f.Q.value=0.9;
  const g=ac.createGain(); g.gain.setValueAtTime(0.5,t); g.gain.exponentialRampToValueAtTime(0.001,t+0.11);
  src.connect(f); f.connect(g); g.connect(musicMasterGain(ac)); src.start(t); src.stop(t+0.12); reap(src,f,g);
  const o=ac.createOscillator(),og=ac.createGain();
  o.type='triangle'; o.frequency.setValueAtTime(190,t); o.frequency.exponentialRampToValueAtTime(120,t+0.06);
  og.gain.setValueAtTime(0.28,t); og.gain.exponentialRampToValueAtTime(0.001,t+0.07);
  o.connect(og); og.connect(musicMasterGain(ac)); o.start(t); o.stop(t+0.08); reap(o,og);
}
function musTick(ac,t){
  const src=ac.createBufferSource(); src.buffer=noiseBuf(ac,'tick',0.03,1);
  const f=ac.createBiquadFilter(); f.type='highpass'; f.frequency.value=5000;
  const g=ac.createGain(); g.gain.value=0.06;
  src.connect(f); f.connect(g); g.connect(musicMasterGain(ac)); src.start(t); src.stop(t+0.04); reap(src,f,g);
}
function musCello(ac,t,freq,dur){
  const o=ac.createOscillator(),g=ac.createGain(),f=ac.createBiquadFilter();
  o.type='sawtooth'; o.frequency.value=freq;
  f.type='lowpass'; f.frequency.value=520; f.Q.value=1.2;
  g.gain.setValueAtTime(0.0001,t); g.gain.linearRampToValueAtTime(0.34,t+0.02);
  g.gain.exponentialRampToValueAtTime(0.001,t+dur*1.05);
  o.connect(f); f.connect(g); g.connect(musicMasterGain(ac)); o.start(t); o.stop(t+dur*1.1); reap(o,f,g);
}
function musHorn(ac,t,freq,dur,vol){
  for(const cents of [-7,0,7]){
    const o=ac.createOscillator(),g=ac.createGain(),f=ac.createBiquadFilter();
    o.type='sawtooth'; o.frequency.value=freq*Math.pow(2,cents/1200);
    f.type='lowpass'; f.frequency.setValueAtTime(700,t); f.frequency.linearRampToValueAtTime(1400,t+dur*0.5);
    g.gain.setValueAtTime(0.0001,t); g.gain.linearRampToValueAtTime(vol,t+0.18);
    g.gain.setValueAtTime(vol,t+dur-0.25); g.gain.exponentialRampToValueAtTime(0.001,t+dur);
    o.connect(f); f.connect(g); g.connect(musicMasterGain(ac)); o.start(t); o.stop(t+dur); reap(o,f,g);
  }
}
function musGuitar(ac,t,freq,dur,vol){
  for(const mul of [1,1.5]){
    const o=ac.createOscillator(),g=ac.createGain();
    const dist=ac.createWaveShaper(); dist.curve=GTR_CURVE;
    const f=ac.createBiquadFilter(); f.type='lowpass'; f.frequency.value=2400; f.Q.value=0.8;
    o.type='sawtooth'; o.frequency.value=freq*mul;
    g.gain.setValueAtTime(0.0001,t); g.gain.linearRampToValueAtTime(vol*(mul===1?1:0.6),t+0.008);
    g.gain.exponentialRampToValueAtTime(0.001,t+dur);
    o.connect(dist); dist.connect(f); f.connect(g); g.connect(musicMasterGain(ac));
    o.start(t); o.stop(t+dur); reap(o,dist,f,g);
  }
}
function musFrenzy(){
  let total=0; for(const r of roster) total+=r.tank.kills;
  return total>=20;
}
function scheduleMusic(){
  if(!audioCtx || audioCtx.state!=='running') return;
  if(isMuted){ musicNextT=Math.max(musicNextT,audioCtx.currentTime+0.1); return; }
  const ac=audioCtx, S=musFrenzy()?MUS_STEP_FRENZY:MUS_STEP_NORMAL;
  if(musicNextT<ac.currentTime) musicNextT=ac.currentTime+0.05;
  while(musicNextT < ac.currentTime+0.75){
    const t=musicNextT, st=musicStep, bar=Math.floor(st/16), inBar=st%16, eighth=Math.floor(inBar/2);
    if(inBar%2===0){
      musCello(ac,t,OST[eighth],S*2.1);
      if(eighth===0) musKick(ac,t,true);
      if(eighth===4) musKick(ac,t,false);
      if(eighth===3 && bar%2===1) musKick(ac,t,false);
      if(eighth===2||eighth===6) musSnare(ac,t);
      if(bar%4===3&&eighth===7) musSnare(ac,t);
      for(const [hb,freqs,barsHeld] of HORNS)
        if(bar===hb&&eighth===0) for(const fq of freqs) musHorn(ac,t,fq,S*16*barsHeld,0.10);
      for(const [lb,fq,lenE,off] of LEAD)
        if(bar===lb&&inBar===off) musHorn(ac,t,fq,S*2*lenE+0.05,0.15);
      if(bar<4) musGuitar(ac,t,N.E2,S*1.7,0.05);
      else musGuitar(ac,t,(bar%2===0?GTR_A:GTR_B)[eighth],S*3.4,0.11);
    }
    musTick(ac,t);
    musicNextT+=S; musicStep=(musicStep+1)%MUS_STEPS;
  }
}
function startMusicEngine(){
  if(musicTimer) return;
  musicTimer=setInterval(scheduleMusic,90);
}
function armAudio(){ try{ const ac=getAudio(); ac.resume(); startMusicEngine(); }catch(e){} }
window.addEventListener('pointerdown',armAudio,{once:true});
window.addEventListener('keydown',armAudio,{once:true});

function playShieldPickup() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    [330,440,550,660].forEach((freq,i) => {
      const o = ac.createOscillator(), g = ac.createGain();
      o.type = 'triangle';
      o.frequency.setValueAtTime(freq, t+i*0.07);
      g.gain.setValueAtTime(0.2, t+i*0.07);
      g.gain.exponentialRampToValueAtTime(0.001, t+i*0.07+0.18);
      o.connect(g); g.connect(masterBus(ac));
      o.start(t+i*0.07); o.stop(t+i*0.07+0.18); reap(o,g);
    });
  } catch(e){}
}
function playShieldDeploy() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const o = ac.createOscillator(), g = ac.createGain();
    o.type = 'sine';
    o.frequency.setValueAtTime(200,t); o.frequency.exponentialRampToValueAtTime(600,t+0.25);
    g.gain.setValueAtTime(0.35,t); g.gain.exponentialRampToValueAtTime(0.001,t+0.35);
    o.connect(g); g.connect(masterBus(ac)); o.start(t); o.stop(t+0.35); reap(o,g);
  } catch(e){}
}
function playShieldBlock() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const o = ac.createOscillator(), g = ac.createGain();
    o.type = 'sine';
    o.frequency.setValueAtTime(800,t); o.frequency.exponentialRampToValueAtTime(300,t+0.2);
    g.gain.setValueAtTime(0.4,t); g.gain.exponentialRampToValueAtTime(0.001,t+0.25);
    o.connect(g); g.connect(masterBus(ac)); o.start(t); o.stop(t+0.25); reap(o,g);
  } catch(e){}
}
function playShot(isPlayer) {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const osc = ac.createOscillator(), gain = ac.createGain(), dist = ac.createWaveShaper();
    const curve = new Float32Array(256);
    for (let i=0;i<256;i++){const x=(i*2/256)-1; curve[i]=(3+20)*x*20*Math.PI/180/(Math.PI+20*Math.abs(x));}
    dist.curve = curve;
    osc.type = 'sawtooth';
    osc.frequency.setValueAtTime(isPlayer?220:160,t); osc.frequency.exponentialRampToValueAtTime(40,t+0.12);
    gain.gain.setValueAtTime(isPlayer?0.4:0.25,t); gain.gain.exponentialRampToValueAtTime(0.001,t+0.15);
    osc.connect(dist); dist.connect(gain); gain.connect(masterBus(ac));
    osc.start(t); osc.stop(t+0.15); reap(osc,dist,gain);
  } catch(e){}
}
function playExplosion() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const src = ac.createBufferSource(); src.buffer = noiseBuf(ac,'boom',0.35,2);
    const filter = ac.createBiquadFilter(); filter.type='lowpass';
    filter.frequency.setValueAtTime(800,t); filter.frequency.exponentialRampToValueAtTime(60,t+0.3);
    const gain = ac.createGain();
    gain.gain.setValueAtTime(0.9,t); gain.gain.exponentialRampToValueAtTime(0.001,t+0.35);
    src.connect(filter); filter.connect(gain); gain.connect(masterBus(ac));
    src.start(t); src.stop(t+0.35); reap(src,filter,gain);
    const osc = ac.createOscillator(), og = ac.createGain();
    osc.type='sine';
    osc.frequency.setValueAtTime(90,t); osc.frequency.exponentialRampToValueAtTime(25,t+0.25);
    og.gain.setValueAtTime(0.7,t); og.gain.exponentialRampToValueAtTime(0.001,t+0.25);
    osc.connect(og); og.connect(masterBus(ac)); osc.start(t); osc.stop(t+0.25); reap(osc,og);
  } catch(e){}
}
function playRicochet() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const osc = ac.createOscillator(), gain = ac.createGain();
    osc.type='sine';
    osc.frequency.setValueAtTime(1200,t); osc.frequency.exponentialRampToValueAtTime(400,t+0.18);
    gain.gain.setValueAtTime(0.15,t); gain.gain.exponentialRampToValueAtTime(0.001,t+0.18);
    osc.connect(gain); gain.connect(masterBus(ac)); osc.start(t); osc.stop(t+0.18); reap(osc,gain);
  } catch(e){}
}
function playEngineRev() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const osc = ac.createOscillator(), gain = ac.createGain();
    osc.type='sawtooth';
    osc.frequency.setValueAtTime(55,t); osc.frequency.linearRampToValueAtTime(80,t+0.08);
    gain.gain.setValueAtTime(0.07,t); gain.gain.exponentialRampToValueAtTime(0.001,t+0.1);
    osc.connect(gain); gain.connect(masterBus(ac)); osc.start(t); osc.stop(t+0.1); reap(osc,gain);
  } catch(e){}
}
function playPickup() {
  if (isMuted) return;
  try {
    const ac = getAudio();
    [440,660,880].forEach((freq,i) => {
      const t=ac.currentTime+i*0.08;
      const osc=ac.createOscillator(),gain=ac.createGain();
      osc.type='sine';
      osc.frequency.setValueAtTime(freq,t);
      gain.gain.setValueAtTime(0.25,t); gain.gain.exponentialRampToValueAtTime(0.001,t+0.15);
      osc.connect(gain); gain.connect(masterBus(ac)); osc.start(t); osc.stop(t+0.15); reap(osc,gain);
    });
  } catch(e){}
}
function playMissileLaunch() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const osc = ac.createOscillator(), gain = ac.createGain();
    osc.type='sawtooth';
    osc.frequency.setValueAtTime(80,t); osc.frequency.exponentialRampToValueAtTime(400,t+0.3);
    gain.gain.setValueAtTime(0.5,t); gain.gain.exponentialRampToValueAtTime(0.001,t+0.4);
    const filter = ac.createBiquadFilter(); filter.type='bandpass'; filter.frequency.value=800;
    osc.connect(filter); filter.connect(gain); gain.connect(masterBus(ac));
    osc.start(t); osc.stop(t+0.4); reap(osc,filter,gain);
  } catch(e){}
}
function playMgShot() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const o = ac.createOscillator(), g = ac.createGain();
    o.type='square';
    o.frequency.setValueAtTime(190,t); o.frequency.exponentialRampToValueAtTime(55,t+0.05);
    g.gain.setValueAtTime(0.1,t); g.gain.exponentialRampToValueAtTime(0.001,t+0.06);
    o.connect(g); g.connect(masterBus(ac)); o.start(t); o.stop(t+0.06); reap(o,g);
  } catch(e){}
}
function playRapidPickup() {
  if (isMuted) return;
  try {
    const ac = getAudio(); const t = ac.currentTime;
    const o = ac.createOscillator(), g = ac.createGain();
    o.type='sawtooth';
    o.frequency.setValueAtTime(300,t); o.frequency.exponentialRampToValueAtTime(900,t+0.2);
    g.gain.setValueAtTime(0.22,t); g.gain.exponentialRampToValueAtTime(0.001,t+0.25);
    o.connect(g); g.connect(masterBus(ac)); o.start(t); o.stop(t+0.25); reap(o,g);
  } catch(e){}
}

function roundRect(x,y,w,h,r) {
  ctx.beginPath();
  ctx.moveTo(x+r,y); ctx.lineTo(x+w-r,y); ctx.quadraticCurveTo(x+w,y,x+w,y+r);
  ctx.lineTo(x+w,y+h-r); ctx.quadraticCurveTo(x+w,y+h,x+w-r,y+h);
  ctx.lineTo(x+r,y+h); ctx.quadraticCurveTo(x,y+h,x,y+h-r);
  ctx.lineTo(x,y+r); ctx.quadraticCurveTo(x,y,x+r,y);
  ctx.closePath();
}

const obstacles = [];
const OBS_BAR_MIN=50,  OBS_BAR_MAX=112;
const OBS_ARM_MIN=38,  OBS_ARM_MAX=80;
const OBS_TH_MIN=16,   OBS_TH_MAX=22;
const OBS_BLOCK_MIN=26, OBS_BLOCK_MAX=60;
const OBS_GAP=26;
const OBS_SPEED_MIN=0.2, OBS_SPEED_MAX=1.15;
const OBS_ROT_MIN=0.0008, OBS_ROT_MAX=0.006;
const OBS_PIVOT_CHANCE=0.003;

function rndRange(a,b){ return a + Math.random()*(b-a); }

function makeObstacleParts() {
  const th=Math.round(rndRange(OBS_TH_MIN,OBS_TH_MAX));
  const roll=Math.random();
  let parts;
  if (roll<0.28) {
    const len=Math.round(rndRange(OBS_BAR_MIN,OBS_BAR_MAX));
    parts=[{x:-len/2,y:-th/2,w:len,h:th}];
  } else if (roll<0.48) {
    const a=Math.round(rndRange(OBS_BLOCK_MIN,OBS_BLOCK_MAX));
    const b=Math.round(rndRange(OBS_BLOCK_MIN,OBS_BLOCK_MAX));
    parts=[{x:-a/2,y:-b/2,w:a,h:b}];
  } else if (roll<0.66) {
    const aa=Math.round(rndRange(OBS_ARM_MIN,OBS_ARM_MAX));
    const bb=Math.round(rndRange(OBS_ARM_MIN,OBS_ARM_MAX));
    parts=[{x:0,y:0,w:aa,h:th},{x:0,y:0,w:th,h:bb}];
  } else if (roll<0.84) {
    const aa=Math.round(rndRange(OBS_ARM_MIN,OBS_ARM_MAX));
    const bb=Math.round(rndRange(OBS_ARM_MIN,OBS_ARM_MAX));
    parts=[{x:-aa/2,y:0,w:aa,h:th},{x:-th/2,y:0,w:th,h:bb}];
  } else {
    const aa=Math.round(rndRange(OBS_ARM_MIN,OBS_ARM_MAX));
    const bb=Math.round(rndRange(OBS_ARM_MIN,OBS_ARM_MAX));
    parts=[{x:-aa/2,y:-th/2,w:aa,h:th},{x:-th/2,y:-bb/2,w:th,h:bb}];
  }
  let x0=1e9,y0=1e9,x1=-1e9,y1=-1e9;
  for(const q of parts){ x0=Math.min(x0,q.x); y0=Math.min(y0,q.y); x1=Math.max(x1,q.x+q.w); y1=Math.max(y1,q.y+q.h); }
  const cx=(x0+x1)/2, cy=(y0+y1)/2;
  for(const q of parts){ q.x-=cx; q.y-=cy; }
  let r=0;
  for(const q of parts){
    for(const [px,py] of [[q.x,q.y],[q.x+q.w,q.y],[q.x,q.y+q.h],[q.x+q.w,q.y+q.h]])
      r=Math.max(r,Math.hypot(px,py));
  }
  return { parts, boundR:Math.ceil(r) };
}

function generateObstacles() {
  obstacles.length = 0;
  const W = canvas.width, H = canvas.height;
  const target = 8 + Math.floor(Math.random()*6);
  let guard = 0;
  while (obstacles.length < target && guard < 500) {
    guard++;
    const {parts,boundR}=makeObstacleParts();
    const margin=boundR+16;
    if (W-2*margin<=0 || H-2*margin<=0) continue;
    const cx=Math.round(rndRange(margin,W-margin));
    const cy=Math.round(rndRange(margin,H-margin));
    let clear=true;
    for (const o of obstacles) {
      if (Math.hypot(cx-o.x,cy-o.y) < boundR+o.boundR+OBS_GAP) { clear=false; break; }
    }
    if (!clear) continue;
    const spd=OBS_SPEED_MIN + Math.random()*Math.random()*(OBS_SPEED_MAX-OBS_SPEED_MIN);
    const dir=Math.random()*Math.PI*2;
    obstacles.push({
      x:cx, y:cy, parts, boundR,
      spd,
      vx:Math.cos(dir)*spd, vy:Math.sin(dir)*spd,
      rot:Math.random()*Math.PI*2,
      rotSpd:(OBS_ROT_MIN + Math.random()*Math.random()*(OBS_ROT_MAX-OBS_ROT_MIN))
             *(Math.random()<0.5?1:-1),
      toneSpd:rndRange(0.006,0.016),
      tonePhase:Math.random()*Math.PI*2,
      glowHue:Math.random()*360,
      glowDrift:0.2+Math.random()*0.9,
      pulseSpd:0.03+Math.random()*0.05,
      pulsePhase:Math.random()*Math.PI*2,
      fx:null, fxHue:-1 });
    const ob=obstacles[obstacles.length-1];
    renderObstacleFX(ob, Math.floor(ob.glowHue/4)*4);
  }
}

function regenerateCurrentMap() {
  const W = canvas.width, H = canvas.height;
  obstacles.forEach(o => {
    o.x=Math.min(Math.max(o.x,o.boundR),Math.max(o.boundR,W-o.boundR));
    o.y=Math.min(Math.max(o.y,o.boundR),Math.max(o.boundR,H-o.boundR));
  });
}

function serializeObstacle(o){
  return {x:o.x,y:o.y,parts:o.parts,boundR:o.boundR,spd:o.spd,vx:o.vx,vy:o.vy,rot:o.rot,rotSpd:o.rotSpd,
    toneSpd:o.toneSpd,tonePhase:o.tonePhase,glowHue:o.glowHue,glowDrift:o.glowDrift,pulseSpd:o.pulseSpd,pulsePhase:o.pulsePhase};
}
function applyObstacleList(list){
  obstacles.length=0;
  for(const d of list){
    const o=Object.assign({},d,{fx:null,fxHue:-1});
    obstacles.push(o);
    renderObstacleFX(o,Math.floor(o.glowHue/4)*4);
  }
}
function applyObsAdd(d){
  const o=Object.assign({},d,{fx:null,fxHue:-1});
  obstacles.push(o);
  renderObstacleFX(o,Math.floor(o.glowHue/4)*4);
  particles.push({x:o.x,y:o.y,ring:true,r:6,life:1,decay:0.04,color:'#9adfe3'});
}

const obsRespawns=[];
function destroyObstacle(i){
  const o=obstacles[i];
  const col=`hsl(${Math.round(o.glowHue)},90%,65%)`;
  for (let k=0;k<44;k++){
    const a=Math.random()*Math.PI*2, sp=2+Math.random()*7;
    particles.push({x:o.x,y:o.y,vx:Math.cos(a)*sp,vy:Math.sin(a)*sp,life:1,
      decay:0.012+Math.random()*0.015,size:3+Math.random()*6,color:k%3?col:'#ffffff'});
  }
  particles.push({x:o.x,y:o.y,ring:true,r:o.boundR*0.6,life:1,decay:0.03,color:col});
  particles.push({x:o.x,y:o.y,ring:true,r:o.boundR*0.3,life:1,decay:0.02,color:'#ffffff'});
  obstacles.splice(i,1);
  playExplosion();
  obsRespawns.push(gameFrame+480);
}
function spawnOneObstacleHost(){
  const W=canvas.width, H=canvas.height;
  for (let tries=0; tries<60; tries++){
    const {parts,boundR}=makeObstacleParts();
    const margin=boundR+16;
    if (W-2*margin<=0||H-2*margin<=0) return;
    const cx=Math.round(rndRange(margin,W-margin));
    const cy=Math.round(rndRange(margin,H-margin));
    let clear=obstacles.every(o=>Math.hypot(cx-o.x,cy-o.y)>=boundR+o.boundR+OBS_GAP);
    if (clear) for (const r of roster){ if(Math.hypot(cx-r.tank.x,cy-r.tank.y)<boundR+90){ clear=false; break; } }
    if (!clear) continue;
    const spd=OBS_SPEED_MIN + Math.random()*Math.random()*(OBS_SPEED_MAX-OBS_SPEED_MIN);
    const dir=Math.random()*Math.PI*2;
    obstacles.push({x:cx,y:cy,parts,boundR,spd,vx:Math.cos(dir)*spd,vy:Math.sin(dir)*spd,
      rot:Math.random()*Math.PI*2,
      rotSpd:(OBS_ROT_MIN+Math.random()*Math.random()*(OBS_ROT_MAX-OBS_ROT_MIN))*(Math.random()<0.5?1:-1),
      toneSpd:rndRange(0.006,0.016),tonePhase:Math.random()*Math.PI*2,
      glowHue:Math.random()*360,glowDrift:0.2+Math.random()*0.9,
      pulseSpd:0.03+Math.random()*0.05,pulsePhase:Math.random()*Math.PI*2,fx:null,fxHue:-1});
    const ob=obstacles[obstacles.length-1];
    renderObstacleFX(ob, Math.floor(ob.glowHue/4)*4);
    particles.push({x:cx,y:cy,ring:true,r:6,life:1,decay:0.04,color:'#9adfe3'});
    if(isHost) broadcastObsAdd(ob);
    return;
  }
}
function updateObstacles() {
  gameFrame++;
  for (let i=obsRespawns.length-1;i>=0;i--)
    if (gameFrame>=obsRespawns[i]) { obsRespawns.splice(i,1); if(isHost) spawnOneObstacleHost(); }
  const W=canvas.width, H=canvas.height;
  for (const o of obstacles) {
    o.x+=o.vx; o.y+=o.vy;
    o.rot+=o.rotSpd;
    if (o.x < -o.boundR)  o.x = W+o.boundR;
    if (o.x > W+o.boundR) o.x = -o.boundR;
    if (o.y < -o.boundR)  o.y = H+o.boundR;
    if (o.y > H+o.boundR) o.y = -o.boundR;
    if (Math.random()<OBS_PIVOT_CHANCE) { const t=o.vx; o.vx=o.vy; o.vy=t; }
  }
  for (let i=0;i<obstacles.length;i++) for (let j=i+1;j<obstacles.length;j++) {
    const a=obstacles[i], b=obstacles[j];
    let dx=b.x-a.x, dy=b.y-a.y, d=Math.hypot(dx,dy);
    const minD=a.boundR+b.boundR;
    if (d>=minD) continue;
    if (d<0.01){ dx=1; dy=0; d=1; }
    const nx=dx/d, ny=dy/d, push=(minD-d)/2+0.5;
    a.x-=nx*push; a.y-=ny*push; b.x+=nx*push; b.y+=ny*push;
    const va=a.vx*nx+a.vy*ny, vb=b.vx*nx+b.vy*ny;
    a.vx+=(vb-va)*nx; a.vy+=(vb-va)*ny;
    b.vx+=(va-vb)*nx; b.vy+=(va-vb)*ny;
  }
  for (const o of obstacles) {
    const sp=Math.hypot(o.vx,o.vy);
    if (sp<0.01) {
      const dir=Math.random()*Math.PI*2;
      o.vx=Math.cos(dir)*o.spd; o.vy=Math.sin(dir)*o.spd;
    } else {
      const k=(sp + (o.spd-sp)*0.03)/sp;
      o.vx*=k; o.vy*=k;
    }
  }
}

const OBS_FX_PAD=20;
function renderObstacleFX(o,hue){
  const size=2*(o.boundR+OBS_FX_PAD);
  if(!o.fx){ o.fx=document.createElement('canvas'); o.fx.width=o.fx.height=size; }
  const fc=o.fx.getContext('2d');
  fc.clearRect(0,0,size,size);
  fc.save(); fc.translate(size/2,size/2);
  fc.shadowColor=`hsl(${hue},100%,60%)`; fc.shadowBlur=14;
  fc.fillStyle=`hsl(${hue},100%,62%)`;
  for (const q of o.parts) fc.fillRect(q.x-3,q.y-3,q.w+6,q.h+6);
  fc.restore();
  o.fxHue=hue;
}

let fxPending=null;
function drawObstacles() {
  obstacles.forEach(o => {
    ctx.save();
    ctx.translate(o.x,o.y); ctx.rotate(o.rot);
    const L=47+39*Math.sin(gameFrame*o.toneSpd+o.tonePhase);
    const gray=l=>`hsl(0,0%,${Math.max(0,Math.min(96,Math.round(l)))}%)`;
    const hue2=(o.glowHue + gameFrame*o.glowDrift) % 360;
    const bucket=Math.floor(hue2/4)*4;
    if (!o.fx) renderObstacleFX(o,bucket);
    else if (o.fxHue!==bucket && !fxPending) fxPending={o,bucket};
    const pulse2=Math.sin(gameFrame*o.pulseSpd + o.pulsePhase)*0.28 + 0.62;
    ctx.fillStyle='rgba(0,0,0,0.4)';
    for (const q of o.parts) ctx.fillRect(q.x+4,q.y+4,q.w,q.h);
    ctx.globalAlpha=pulse2;
    const half=o.boundR+OBS_FX_PAD;
    ctx.drawImage(o.fx,-half,-half);
    ctx.globalAlpha=Math.min(1,pulse2+0.25);
    ctx.fillStyle=`hsl(${bucket},100%,82%)`;
    for (const q of o.parts) ctx.fillRect(q.x-1.5,q.y-1.5,q.w+3,q.h+3);
    ctx.globalAlpha=1;
    ctx.fillStyle=gray(L);
    for (const q of o.parts) ctx.fillRect(q.x,q.y,q.w,q.h);
    ctx.restore();
  });
}

function rectCollide(x,y,r,o) {
  const dx=x-o.x, dy=y-o.y;
  if (dx*dx+dy*dy > (o.boundR+r)*(o.boundR+r)) return false;
  const c=Math.cos(-o.rot), sn=Math.sin(-o.rot);
  const lx=dx*c-dy*sn, ly=dx*sn+dy*c;
  for (const q of o.parts) {
    const nx=Math.max(q.x,Math.min(lx,q.x+q.w));
    const ny=Math.max(q.y,Math.min(ly,q.y+q.h));
    const ox=lx-nx, oy=ly-ny;
    if (ox*ox+oy*oy < r*r) return true;
  }
  return false;
}
function bulletHitsObstacle(bx,by) {
  return obstacles.some(o => rectCollide(bx,by,2,o));
}
function hasLOS(x1,y1,x2,y2) {
  const d=Math.hypot(x2-x1,y2-y1);
  const steps=Math.max(2, Math.floor(d/12));
  for(let i=1;i<steps;i++){
    const t=i/steps;
    if(bulletHitsObstacle(x1+(x2-x1)*t, y1+(y2-y1)*t)) return false;
  }
  return true;
}

const PICKUP_COLLECT_R=36, PICKUP_CLEAR_R=50, PICKUP_SPACING=120, PICKUP_FADE=180;

class Pickup {
  constructor(cfg){ this.cfg=cfg; this.visible=cfg.startVisible; this.timer=cfg.startTimer; this.x=0; this.y=0; this.pulse=0; }
  spawn(){
    let bx=canvas.width/2, by=canvas.height/2, bestScore=-1;
    for(let t=0;t<40;t++){
      const x=120+Math.random()*(canvas.width-240);
      const y=120+Math.random()*(canvas.height-240);
      if(obstacles.some(o=>rectCollide(x,y,PICKUP_CLEAR_R,o))) continue;
      let minD=1e9;
      for(const p of PICKUPS){ if(p!==this&&p.visible) minD=Math.min(minD,Math.hypot(x-p.x,y-p.y)); }
      if(minD>=PICKUP_SPACING){ bx=x; by=y; bestScore=1e9; break; }
      if(minD>bestScore){ bestScore=minD; bx=x; by=y; }
    }
    this.x=bx; this.y=by;
    this.flash=80;
    if(this.cfg.onSpawn) this.cfg.onSpawn(this);
  }
  update(){
    this.timer++;
    if(this.visible){
      if(this.timer>=this.cfg.activeTime){ this.visible=false; this.timer=0; return; }
      for(const r of roster){
        const s=r.tank;
        if(!this.cfg.canCollect(s)) continue;
        if(Math.hypot(s.x-this.x,s.y-this.y)<PICKUP_COLLECT_R){
          this.cfg.onCollect(s); this.visible=false; this.timer=0; break;
        }
      }
    } else if(this.timer>=this.cfg.hiddenTime){
      if(isHost){ this.spawn(); this.visible=true; this.timer=0; broadcastPickupSpawn(this); }
      else { this.timer=this.cfg.hiddenTime; }
    }
  }
  draw(){
    if(!this.visible) return;
    this.pulse+=0.08;
    if(this.flash>0){
      this.flash--;
      const t=(80-this.flash)/80, a=Math.abs(Math.sin(t*Math.PI*2));
      ctx.save(); ctx.translate(this.x,this.y);
      ctx.globalAlpha=a*0.85;
      ctx.beginPath(); ctx.arc(0,0,26,0,Math.PI*2); ctx.fillStyle='#fff'; ctx.fill();
      ctx.globalAlpha=a*0.6; ctx.lineWidth=3;
      ctx.beginPath(); ctx.arc(0,0,26+t*34,0,Math.PI*2); ctx.strokeStyle='#fff'; ctx.stroke();
      ctx.restore();
    }
    const alpha=this.timer>this.cfg.activeTime-PICKUP_FADE?(this.cfg.activeTime-this.timer)/PICKUP_FADE:1;
    ctx.save(); ctx.globalAlpha=alpha*(Math.sin(this.pulse)*0.25+0.75);
    ctx.translate(this.x,this.y);
    ctx.beginPath(); ctx.arc(0,0,22+Math.sin(this.pulse)*4,0,Math.PI*2);
    const ring=typeof this.cfg.ring==='function'?this.cfg.ring():this.cfg.ring;
    const label=typeof this.cfg.label==='function'?this.cfg.label():this.cfg.label;
    ctx.strokeStyle=ring; ctx.lineWidth=2; ctx.stroke();
    this.cfg.drawIcon();
    ctx.fillStyle=this.cfg.labelColor; ctx.font='bold 9px Arial'; ctx.textAlign='center';
    ctx.fillText(label,0,30);
    ctx.restore();
  }
}

const PU={
  missile:new Pickup({
    key:'missile', enabled:()=>true, activeTime:600, hiddenTime:600, startVisible:true, startTimer:0,
    ring:'#ff8800', label:'MISSILE', labelColor:'#fff',
    canCollect:s=>!s.hasMissile,
    onCollect:s=>{
      s.hasMissile=true;
      if(s.isLocal){ playPickup(); if(touchMode) fireMissileFor(s); }
    },
    drawIcon(){
      ctx.font='22px Arial'; ctx.textAlign='center'; ctx.textBaseline='middle';
      ctx.fillText('🚀',0,1);
    }
  }),
  shield:new Pickup({
    key:'shield', enabled:()=>true, activeTime:600, hiddenTime:700, startVisible:false, startTimer:300,
    ring:'#4488ff', label:'SHIELD', labelColor:'#aaddff',
    canCollect:s=>!s.hasShield&&!s.shieldOn,
    onCollect:s=>{ s.hasShield=true; if(s.isLocal){ playShieldPickup(); } },
    drawIcon(){
      ctx.font='22px Arial'; ctx.textAlign='center'; ctx.textBaseline='middle';
      ctx.fillText('🛡',0,1);
    }
  }),
  power:new Pickup({
    key:'power', enabled:()=>true, activeTime:550, hiddenTime:240, startVisible:false, startTimer:550,
    ring:()=>POWERS[PU.power.kind||'rapid'].ring,
    label:()=>POWERS[PU.power.kind||'rapid'].label,
    labelColor:'#fff',
    onSpawn:p=>{ p.kind=POWER_KEYS[Math.floor(Math.random()*POWER_KEYS.length)]; },
    canCollect:s=>true,
    onCollect:s=>{
      s.powers[PU.power.kind]=POWER_DURATION;
      if(s.isLocal){ playRapidPickup(); }
    },
    drawIcon(){
      const k=PU.power.kind||'rapid';
      const g=k==='rapid'?'⚡':k==='scatter'?'🔱':k==='invincible'?'⭐':k==='ricochet'?'🎱':'💨';
      ctx.font='22px Arial'; ctx.textAlign='center'; ctx.textBaseline='middle';
      ctx.fillText(g,0,1);
    }
  })
};
const PICKUPS=[PU.missile,PU.shield,PU.power];
function pkSnap(p){ return {visible:p.visible,x:p.x,y:p.y,timer:p.timer,kind:p.kind}; }
function broadcastPickupSpawn(p){ if(spawnAction) try{ spawnAction.send({t:'pk',key:p.cfg.key,x:p.x,y:p.y,kind:p.kind}); }catch(e){} }

const SHIELD_DURATION = 300;
function tickShields() {
  for (const r of roster) {
    const t=r.tank;
    if (!t.shieldOn) continue;
    t.shieldTimer--;
    if (t.shieldTimer<=0) t.shieldOn=false;
  }
}
function drawActiveShields() {
  for (const r of roster) {
    const t=r.tank;
    if (!t.shieldOn) continue;
    const ph=t.shieldPhase;
    const pulse=Math.sin(Date.now()*0.012+ph)*0.3+0.7;
    const fade=Math.min(1,t.shieldTimer/40);
    ctx.save(); ctx.globalAlpha=pulse*fade*0.55;
    ctx.beginPath(); ctx.arc(t.x,t.y,42+Math.sin(Date.now()*0.015+ph)*4,0,Math.PI*2);
    ctx.strokeStyle=t.pal.hud; ctx.lineWidth=3; ctx.stroke();
    ctx.globalAlpha=pulse*fade*0.18; ctx.fillStyle=t.pal.body; ctx.fill();
    ctx.restore();
  }
}

const POWER_DURATION = 360;
const RAPID_CADENCE  = 3;
const POWERS = {
  rapid:      { hud:'⚡ MACHINE GUN',  ring:'#ffd23f', label:'RAPID' },
  scatter:    { hud:'🔱 SCATTER-SHOT', ring:'#ff8844', label:'SCATTER' },
  invincible: { hud:'⭐ INVINCIBLE',   ring:'#ffffff', label:'INVINCIBLE' },
  super:      { hud:'💨 SUPER SPEED',  ring:'#66ffcc', label:'SPEED' },
  ricochet:   { hud:'🎱 RICOCHET',     ring:'#ff5fd2', label:'RICOCHET' },
};
const POWER_KEYS = Object.keys(POWERS);
function hasPow(t,k){ return !!t && !!t.powers && (t.powers[k]||0)>0; }
function isInvincible(t){ return hasPow(t,'invincible'); }

const particles=[];
function spawnExplosion(x,y,color) {
  addShake(7,14); addHitstop(4); buzz(25);
  markScorch(x,y,13+Math.random()*9);
  const count=18;
  for (let i=0;i<count;i++) {
    const angle=(Math.PI*2/count)*i+(Math.random()-.5)*0.4;
    const speed=2+Math.random()*5;
    particles.push({x,y,vx:Math.cos(angle)*speed,vy:Math.sin(angle)*speed,life:1,decay:0.03+Math.random()*0.03,size:3+Math.random()*4,color});
  }
  particles.push({x,y,ring:true,r:4,life:1,decay:0.06,color});
}
function simParticles() {
  for (let i=particles.length-1;i>=0;i--) {
    const p=particles[i]; p.life-=p.decay;
    if (p.life<=0){particles.splice(i,1);continue;}
    if (p.ring) p.r+=4;
    else { p.x+=p.vx; p.y+=p.vy; p.vx*=0.93; p.vy*=0.93; }
  }
}
function drawParticles() {
  for (const p of particles) {
    if (p.ring) {
      ctx.beginPath(); ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.strokeStyle=`rgba(255,200,80,${p.life*0.6})`; ctx.lineWidth=2; ctx.stroke();
    } else {
      ctx.save(); ctx.globalAlpha=p.life; ctx.fillStyle=p.color;
      ctx.beginPath(); ctx.arc(p.x,p.y,p.size*p.life,0,Math.PI*2); ctx.fill(); ctx.restore();
    }
  }
}
const flashes=[];
function spawnFlash(x,y,angle){flashes.push({x,y,angle,life:1});}
function simFlashes() {
  for (let i=flashes.length-1;i>=0;i--) {
    flashes[i].life-=0.25;
    if (flashes[i].life<=0) flashes.splice(i,1);
  }
}
function drawFlashes() {
  for (const f of flashes) {
    ctx.save(); ctx.globalAlpha=f.life*0.9; ctx.translate(f.x,f.y); ctx.rotate(f.angle);
    const g=ctx.createRadialGradient(0,0,0,0,0,20);
    g.addColorStop(0,'#fff'); g.addColorStop(0.3,'#ffdd44'); g.addColorStop(1,'rgba(255,100,0,0)');
    ctx.fillStyle=g; ctx.beginPath(); ctx.ellipse(10,0,24,10,0,0,Math.PI*2); ctx.fill(); ctx.restore();
  }
}

function makePal(name,h,s){
  const c=(l,sat=s)=>`hsl(${h},${sat}%,${l}%)`;
  return {
    name, hue:h,
    body:c(40), hi:c(50), sh:c(25), turret:c(35),
    track:c(22), track2:c(37), barrel:c(31), barrelHi:c(41),
    bullet:c(77,100), bulletDark:c(22,100), hud:c(60,100)
  };
}
const TANK_COLORS = {
  red:    makePal('RED',     0, 58),
  orange: makePal('ORANGE',  26, 88),
  yellow: makePal('YELLOW',  47, 85),
  lime:   makePal('LIME',    84, 70),
  green:  makePal('GREEN',  120, 50),
  teal:   makePal('TEAL',   155, 60),
  cyan:   makePal('CYAN',   186, 66),
  blue:   makePal('BLUE',   214, 62),
  indigo: makePal('INDIGO', 244, 62),
  purple: makePal('PURPLE', 276, 58),
  magenta:makePal('MAGENTA',300, 68),
  pink:   makePal('PINK',   325, 72),
  rose:   makePal('ROSE',   344, 72),
  white:  { name:'WHITE', hue:0,
    body:'hsl(0,0%,72%)', hi:'hsl(0,0%,86%)', sh:'hsl(0,0%,48%)', turret:'hsl(0,0%,64%)',
    track:'hsl(0,0%,40%)', track2:'hsl(0,0%,62%)', barrel:'hsl(0,0%,55%)', barrelHi:'hsl(0,0%,78%)',
    bullet:'hsl(0,0%,100%)', bulletDark:'hsl(0,0%,55%)', hud:'#ffffff' },
};
const COLOR_KEYS = Object.keys(TANK_COLORS);

class Bullet {
  constructor(x,y,angle,pal) {
    this.x=x; this.y=y; this.angle=angle; this.speed=11; this.pal=pal; this.alive=true; this.trail=[]; this.ric=false; this.bounces=0;
  }
  update() {
    this.trail.push({x:this.x,y:this.y});
    if (this.trail.length>7) this.trail.shift();
    this.x+=this.speed*Math.cos(this.angle);
    this.y+=this.speed*Math.sin(this.angle);
    if (bulletHitsObstacle(this.x,this.y)){
      if (this.ric) {
        const px=this.x-this.speed*Math.cos(this.angle), py=this.y-this.speed*Math.sin(this.angle);
        const hitX=bulletHitsObstacle(this.x,py), hitY=bulletHitsObstacle(px,this.y);
        if (hitX&&!hitY)      this.angle=Math.PI-this.angle;
        else if (hitY&&!hitX) this.angle=-this.angle;
        else                  this.angle+=Math.PI;
        this.x=px; this.y=py;
        this.bounces++; playRicochet();
        if (this.bounces>12) this.alive=false;
      } else { this.alive=false; playRicochet(); }
    }
    if (this.x<0||this.x>canvas.width||this.y<0||this.y>canvas.height) this.alive=false;
  }
  draw() {
    for (let i=0;i<this.trail.length;i++) {
      ctx.beginPath(); ctx.arc(this.trail[i].x,this.trail[i].y,2,0,Math.PI*2);
      ctx.fillStyle=this.ric?`rgba(255,95,220,${(i/this.trail.length)*0.5})`:`rgba(255,200,80,${(i/this.trail.length)*0.4})`; ctx.fill();
    }
    ctx.save(); ctx.translate(this.x,this.y); ctx.rotate(this.angle);
    const bg=ctx.createRadialGradient(0,0,0,0,0,5);
    bg.addColorStop(0,'#fff');
    bg.addColorStop(0.4,this.pal.bullet);
    bg.addColorStop(1, this.pal.bulletDark);
    ctx.fillStyle=bg; ctx.beginPath(); ctx.ellipse(0,0,7,3,0,0,Math.PI*2); ctx.fill(); ctx.restore();
  }
  checkHit(tank) {
    const dx=this.x-tank.x,dy=this.y-tank.y; return Math.sqrt(dx*dx+dy*dy)<TUNE.BULLET_HIT_R;
  }
}

const missiles=[];
class Missile {
  constructor(x,y,angle,target,owner) {
    this.x=x; this.y=y; this.angle=angle; this.target=target; this.owner=owner;
    this.speed=4.5; this.turnRate=0.045; this.alive=true; this.trail=[]; this.age=0;
    if (touchMode && target.isLocal) deployShield(target);
  }
  update() {
    this.age++;
    let dx=this.target.x-this.x, dy=this.target.y-this.y;
    if (Math.abs(dx)>canvas.width/2) dx-=Math.sign(dx)*canvas.width;
    if (Math.abs(dy)>canvas.height/2) dy-=Math.sign(dy)*canvas.height;
    let hxv=Math.cos(Math.atan2(dy,dx)), hyv=Math.sin(Math.atan2(dy,dx));
    for (const o of obstacles){
      const ox=this.x-o.x, oy=this.y-o.y, d=Math.hypot(ox,oy);
      const range=o.boundR+56;
      if (d<range && d>0.001){ const w=1.6*(range-d)/range; hxv+=w*ox/d; hyv+=w*oy/d; }
    }
    const desired=Math.atan2(hyv,hxv);
    const diff=normAngle(desired-this.angle);
    this.angle+=Math.sign(diff)*Math.min(Math.abs(diff),this.turnRate*1.4);
    this.trail.push({x:this.x,y:this.y});
    if (this.trail.length>20) this.trail.shift();
    this.x+=this.speed*Math.cos(this.angle);
    this.y+=this.speed*Math.sin(this.angle);
    if (this.x<0) this.x=canvas.width;
    if (this.x>canvas.width) this.x=0;
    if (this.y<0) this.y=canvas.height;
    if (this.y>canvas.height) this.y=0;
    const hx=this.target.x-this.x, hy=this.target.y-this.y;
    if (Math.sqrt(hx*hx+hy*hy)<TUNE.MISSILE_HIT_R) {
      const shielded=this.target.shieldOn||isInvincible(this.target)||this.target.spawnGrace>0;
      this.alive=false;
      if (shielded) {
        spawnExplosion(this.x,this.y,'#44aaff'); playShieldBlock();
      }
      else {
        this.target.hitFlash=14;
        spawnExplosion(this.target.x,this.target.y,'#ff8800');
        spawnExplosion(this.target.x+(Math.random()-.5)*30,this.target.y+(Math.random()-.5)*30,'#ffaa00');
        playExplosion();
        if (this.target.authoritative) {
          if(this.owner) this.owner.kills++;
          this.target.relocate();
          if(this.target.isLocal) broadcastHit(this.target);
        }
      }
    }
    if (this.alive && obstacles.some(o=>rectCollide(this.x,this.y,5,o))) {
      this.alive=false; spawnExplosion(this.x,this.y,'#ffaa00'); playRicochet();
    }
    if (this.age>720) this.alive=false;
  }
  draw() {
    for (let i=0;i<this.trail.length;i++) {
      const tr=this.trail[i], frac=i/this.trail.length;
      ctx.save(); ctx.globalAlpha=frac*0.6;
      ctx.beginPath(); ctx.arc(tr.x,tr.y,4*frac,0,Math.PI*2);
      ctx.fillStyle=frac>0.6?'#ff6600':'#ffaa00'; ctx.fill(); ctx.restore();
    }
    ctx.save(); ctx.translate(this.x,this.y); ctx.rotate(this.angle);
    ctx.shadowColor='#ff8800'; ctx.shadowBlur=12;
    ctx.beginPath(); ctx.moveTo(18,0); ctx.lineTo(6,-5); ctx.lineTo(6,5);
    ctx.closePath(); ctx.fillStyle='#ffdd44'; ctx.fill();
    ctx.fillStyle='#ff8800'; ctx.fillRect(-10,-5,18,10);
    ctx.fillStyle='#cc4400';
    ctx.beginPath(); ctx.moveTo(-8,-5); ctx.lineTo(-16,-12); ctx.lineTo(-4,-5); ctx.closePath(); ctx.fill();
    ctx.beginPath(); ctx.moveTo(-8,5);  ctx.lineTo(-16,12);  ctx.lineTo(-4,5);  ctx.closePath(); ctx.fill();
    const flicker=Math.random()*4;
    ctx.beginPath(); ctx.moveTo(-10,-4); ctx.lineTo(-18-flicker,0); ctx.lineTo(-10,4);
    ctx.closePath(); ctx.fillStyle=`rgba(255,${100+Math.random()*100|0},0,0.9)`; ctx.fill();
    ctx.restore();
  }
}

function nearestOther(tank){
  let best=null,bd=Infinity;
  for(const r of roster){
    if(r.tank===tank) continue;
    const d=Math.hypot(r.tank.x-tank.x,r.tank.y-tank.y);
    if(d<bd){bd=d;best=r.tank;}
  }
  return best;
}
function fireMissileFor(tank) {
  if (!tank.hasMissile) return;
  const target=nearestOther(tank);
  if (!target) return;
  const mx=tank.x+52*Math.cos(tank.turretAngle), my=tank.y+52*Math.sin(tank.turretAngle);
  missiles.push(new Missile(mx,my,tank.turretAngle,target,tank));
  tank.hasMissile=false; playMissileLaunch();
}
function fireMissile() { if(localEntry) fireMissileFor(localEntry.tank); }
function deployShield(tank) {
  if (!tank.hasShield || tank.shieldOn) return;
  tank.hasShield=false; tank.shieldOn=true; tank.shieldTimer=SHIELD_DURATION;
  playShieldDeploy();
}
function deployPlayerShield() { if(localEntry) deployShield(localEntry.tank); }

class Tank {
  constructor(x,y,angle,colorKey,name,isLocal,peerId) {
    this.x=x; this.y=y; this.angle=angle; this.turretAngle=angle;
    this.colorKey=colorKey; this.pal=TANK_COLORS[colorKey]||TANK_COLORS.green;
    this.name=name; this.speed=TUNE.TANK_BASE_SPEED;
    this.rotSpeed=Math.PI/180*2; this.bullets=[];
    this.spawnGrace=0;
    this.fireCooldown=0; this.FIRE_RATE=TUNE.TANK_BASE_FIRE; this.hitFlash=0;
    this.trackOffset=0;
    this.hasMissile=false; this.hasShield=false; this.shieldOn=false; this.shieldTimer=0; this.powers={};
    this.kills=0; this.isLocal=!!isLocal; this.peerId=peerId||null; this.authoritative=!!isLocal;
    this.shotSeq=0; this.shieldPhase=Math.random()*Math.PI*2;
  }
  setColor(key){ this.colorKey=key; this.pal=TANK_COLORS[key]||TANK_COLORS.green; }
  draw() {
    const p=this.pal;
    ctx.save(); ctx.translate(this.x,this.y);
    if (this.spawnGrace>0) ctx.globalAlpha=0.45+0.25*Math.sin(gameFrame*0.4);
    ctx.save();
    ctx.translate(3,5);
    ctx.fillStyle='rgba(0,0,0,0.30)';
    ctx.save(); ctx.rotate(this.angle);
    ctx.beginPath();
    ctx.moveTo(-26,-22); ctx.lineTo(26,-22); ctx.lineTo(30,-18); ctx.lineTo(30,18);
    ctx.lineTo(26,22); ctx.lineTo(-26,22); ctx.closePath(); ctx.fill();
    ctx.restore();
    ctx.save(); ctx.rotate(this.turretAngle);
    ctx.fillRect(10,-4,40,8);
    ctx.restore();
    ctx.restore();
    const invinc = hasPow(this,'invincible');
    if (invinc) {
      const hue=(gameFrame*3)%360;
      ctx.scale(1.5,1.5);
      ctx.shadowColor=`hsl(${hue},100%,62%)`;
      ctx.shadowBlur=22;
    }
    if (this.spawnGrace>0) this.spawnGrace--;
    if (this.hitFlash>0) {
      ctx.save(); ctx.globalAlpha=this.hitFlash/10*0.6; ctx.fillStyle='white';
      ctx.beginPath(); ctx.arc(0,0,36,0,Math.PI*2); ctx.fill(); ctx.restore();
      this.hitFlash--;
    }
    ctx.save(); ctx.rotate(this.angle);
    const toff = -(((this.trackOffset % 8) + 8) % 8);
    const idle = Math.abs(this.trackOffset-(this._lastTrackOff??this.trackOffset))<0.05;
    this._lastTrackOff=this.trackOffset;
    if (!idle && Math.random()<0.10) {
      const sd=Math.random()<0.5?1:-1;
      const ex=this.x-29*Math.cos(this.angle)-9*Math.sin(this.angle)*sd;
      const ey=this.y-29*Math.sin(this.angle)+9*Math.cos(this.angle)*sd;
      particles.push({x:ex,y:ey,vx:-Math.cos(this.angle)*0.5+(Math.random()-.5)*0.3,
                      vy:-Math.sin(this.angle)*0.5+(Math.random()-.5)*0.3,
                      life:0.55,decay:0.028,size:2+Math.random()*2,color:'rgba(190,190,200,0.5)'});
    }
    const trackTop=()=>{ ctx.beginPath(); ctx.moveTo(-26,-22); ctx.lineTo(26,-22); ctx.lineTo(30,-18); ctx.lineTo(30,-13); ctx.lineTo(-26,-13); ctx.closePath(); };
    const trackBot=()=>{ ctx.beginPath(); ctx.moveTo(-26,13); ctx.lineTo(30,13); ctx.lineTo(30,18); ctx.lineTo(26,22); ctx.lineTo(-26,22); ctx.closePath(); };
    ctx.fillStyle=p.track; trackTop(); ctx.fill();
    ctx.save(); trackTop(); ctx.clip();
    ctx.fillStyle=p.track2;
    for (let i=-30;i<=30;i+=8) ctx.fillRect(i+toff,-22,4,9);
    ctx.restore();
    ctx.fillStyle=p.track; trackBot(); ctx.fill();
    ctx.save(); trackBot(); ctx.clip();
    ctx.fillStyle=p.track2;
    for (let i=-30;i<=30;i+=8) ctx.fillRect(i+toff,13,4,9);
    ctx.restore();
    ctx.fillStyle=p.body; roundRect(-26,-12,48,24,4); ctx.fill();
    ctx.beginPath(); ctx.moveTo(21,-12); ctx.lineTo(26,0); ctx.lineTo(21,12); ctx.closePath(); ctx.fill();
    ctx.fillStyle=p.hi; ctx.fillRect(-22,-10,40,6);
    ctx.beginPath(); ctx.moveTo(20,-10); ctx.lineTo(24,-1); ctx.lineTo(20,-1); ctx.closePath(); ctx.fill();
    ctx.strokeStyle=p.sh; ctx.lineWidth=1;
    ctx.beginPath(); ctx.moveTo(-10,-10); ctx.lineTo(-10,10);
    ctx.moveTo(10,-10); ctx.lineTo(10,10); ctx.stroke();
    const beam=ctx.createLinearGradient(22,0,74,0);
    beam.addColorStop(0,'rgba(255,250,225,0.22)');
    beam.addColorStop(1,'rgba(255,250,225,0)');
    ctx.fillStyle=beam;
    ctx.beginPath(); ctx.moveTo(22,-11); ctx.lineTo(74,-20); ctx.lineTo(74,-1); ctx.closePath(); ctx.fill();
    ctx.beginPath(); ctx.moveTo(22,11);  ctx.lineTo(74,1);  ctx.lineTo(74,20);  ctx.closePath(); ctx.fill();
    ctx.fillStyle='rgba(255,250,225,0.95)';
    ctx.fillRect(18,-11,4,3); ctx.fillRect(18,8,4,3);
    if (idle) {
      for (const ly of [-9.5,9.5]) {
        const g=ctx.createRadialGradient(-25,ly,1,-25,ly,14);
        g.addColorStop(0,'rgba(255,60,60,0.55)');
        g.addColorStop(1,'rgba(255,60,60,0)');
        ctx.fillStyle=g;
        ctx.beginPath(); ctx.arc(-25,ly,14,Math.PI/2,Math.PI*1.5); ctx.closePath(); ctx.fill();
      }
      ctx.fillStyle='rgba(255,60,60,1)';
      ctx.fillRect(-27,-11.5,4,4); ctx.fillRect(-27,7.5,4,4);
    } else {
      ctx.fillStyle='rgba(255,45,45,0.9)';
      ctx.fillRect(-26,-11,3,3); ctx.fillRect(-26,8,3,3);
    }
    ctx.restore();
    ctx.save(); ctx.rotate(this.turretAngle);
    ctx.beginPath(); ctx.arc(0,0,14,0,Math.PI*2);
    ctx.fillStyle=p.turret; ctx.fill();
    ctx.strokeStyle=p.sh; ctx.lineWidth=1.5; ctx.stroke();
    ctx.beginPath(); ctx.arc(0,0,7,0,Math.PI*2);
    ctx.fillStyle=p.sh; ctx.fill();
    ctx.fillStyle=p.barrel; ctx.fillRect(10,-4,33,8);
    ctx.fillStyle=p.barrelHi; ctx.fillRect(10,-4,33,3);
    ctx.fillStyle='#222'; ctx.fillRect(43,-5,7,10);
    ctx.fillStyle=p.sh; ctx.fillRect(44.5,-5,1.5,10); ctx.fillRect(47.5,-5,1.5,10);
    ctx.restore(); ctx.restore();
    this.bullets.forEach(b=>b.draw());
  }
  moveForward(scale=1) {
    const sp=this.speed*scale;
    const ox=this.x, oy=this.y;
    const nx=this.x+sp*Math.cos(this.angle), ny=this.y+sp*Math.sin(this.angle);
    if (!this.collidesWithObstacles(nx,this.y)) this.x=nx;
    if (!this.collidesWithObstacles(this.x,ny)) this.y=ny;
    const moved=Math.hypot(this.x-ox,this.y-oy);
    this.trackOffset += moved;
    this._wearAcc=(this._wearAcc||0)+moved;
    if (this._wearAcc>9){ this._wearAcc=0; markTread(this.x,this.y,this.angle); }
    this.wrapAround();
  }
  moveBackward(scale=1) {
    const sp=this.speed*scale;
    const ox=this.x, oy=this.y;
    const nx=this.x-sp*Math.cos(this.angle), ny=this.y-sp*Math.sin(this.angle);
    if (!this.collidesWithObstacles(nx,this.y)) this.x=nx;
    if (!this.collidesWithObstacles(this.x,ny)) this.y=ny;
    this.trackOffset -= Math.hypot(this.x-ox,this.y-oy);
    this.wrapAround();
  }
  unstick() {
    const R=TUNE.TANK_OBS_R;
    for (const o of obstacles) {
      const dx0=this.x-o.x, dy0=this.y-o.y;
      if (dx0*dx0+dy0*dy0 > (o.boundR+R)*(o.boundR+R)) continue;
      const c=Math.cos(-o.rot), sn=Math.sin(-o.rot);
      let lx=dx0*c-dy0*sn, ly=dx0*sn+dy0*c;
      for (const q of o.parts) {
        const nx=Math.max(q.x,Math.min(lx,q.x+q.w));
        const ny=Math.max(q.y,Math.min(ly,q.y+q.h));
        const ox=lx-nx, oy=ly-ny;
        const d2=ox*ox+oy*oy;
        if (d2>=R*R) continue;
        let px,py;
        if (d2>0.0001) {
          const d=Math.sqrt(d2), need=R-d+0.5;
          px=ox/d*need; py=oy/d*need;
        } else {
          const left=lx-q.x, right=q.x+q.w-lx, top=ly-q.y, bot=q.y+q.h-ly;
          const mn=Math.min(left,right,top,bot);
          px = mn===left?-(left+R):mn===right?(right+R):0;
          py = (px===0) ? (mn===top?-(top+R):(bot+R)) : 0;
        }
        const cw=Math.cos(o.rot), sw=Math.sin(o.rot);
        this.x += px*cw - py*sw;
        this.y += px*sw + py*cw;
        const dx=this.x-o.x, dy=this.y-o.y;
        lx=dx*c-dy*sn; ly=dx*sn+dy*c;
      }
    }
  }
  fire() {
    if (this.spawnGrace>0) return;
    if (this.fireCooldown>0) return;
    const bx=this.x+52*Math.cos(this.turretAngle), by=this.y+52*Math.sin(this.turretAngle);
    const scatter = hasPow(this,'scatter');
    const SPREAD=5*Math.PI/180;
    const angles = scatter ? [this.turretAngle-SPREAD,this.turretAngle,this.turretAngle+SPREAD]
                           : [this.turretAngle];
    const ric = hasPow(this,'ricochet');
    for (const a of angles) { const nb=new Bullet(bx,by,a,this.pal); nb.ric=ric; this.bullets.push(nb); }
    this.shotSeq++;
    spawnFlash(bx,by,this.turretAngle); playShot(this.isLocal);
    this.fireCooldown=this.FIRE_RATE;
  }
  rapidShot() {
    if (this.spawnGrace>0) return;
    const bx=this.x+52*Math.cos(this.turretAngle), by=this.y+52*Math.sin(this.turretAngle);
    const SPREAD=5*Math.PI/180;
    const angles = hasPow(this,'scatter') ? [this.turretAngle-SPREAD,this.turretAngle,this.turretAngle+SPREAD]
                                               : [this.turretAngle];
    const ric = hasPow(this,'ricochet');
    for (const a of angles){ const nb=new Bullet(bx,by,a,this.pal); nb.ric=ric; this.bullets.push(nb); }
    spawnFlash(bx,by,this.turretAngle); playMgShot();
  }
  updateBulletsMulti(others) {
    if (this.fireCooldown>0) this.fireCooldown--;
    const deflect=(b,cx,cy)=>{
      const nx=b.x-cx, ny=b.y-cy, nl=Math.hypot(nx,ny)||1;
      const ux=nx/nl, uy=ny/nl, vx=Math.cos(b.angle), vy=Math.sin(b.angle);
      const d=vx*ux+vy*uy;
      b.angle=Math.atan2(vy-2*d*uy, vx-2*d*ux);
      b.x=cx+ux*(TUNE.BULLET_HIT_R+3); b.y=cy+uy*(TUNE.BULLET_HIT_R+3);
      b.bounces++;
    };
    this.bullets.forEach(b=>{
      b.update();
      if (b.alive&&b.ric&&b.checkHit(this)) {
        const tox=this.x-b.x, toy=this.y-b.y;
        if (Math.cos(b.angle)*tox+Math.sin(b.angle)*toy>0) {
          deflect(b,this.x,this.y); playRicochet();
        }
      }
      if (!b.alive) return;
      for (const enemy of others) {
        if (!b.alive) break;
        if (!b.checkHit(enemy)) continue;
        const shielded = enemy.shieldOn || isInvincible(enemy);
        if (shielded && b.ric) {
          deflect(b,enemy.x,enemy.y);
          spawnExplosion(b.x,b.y, enemy.shieldOn?'#44aaff':'#ffffff'); playShieldBlock();
          continue;
        }
        b.alive=false;
        if (shielded) {
          spawnExplosion(b.x,b.y, enemy.shieldOn?'#44aaff':'#ffffff'); playShieldBlock();
        } else {
          spawnExplosion(enemy.x,enemy.y,this.pal.bullet);
          playExplosion();
          if (enemy.authoritative) {
            enemy.hitFlash=10; this.kills++;
            enemy.relocate();
            if (enemy.isLocal) broadcastHit(enemy);
          }
        }
      }
    });
    this.bullets=this.bullets.filter(b=>b.alive);
  }
  collidesWithObstacles(nx,ny){
    if (isInvincible(this)) {
      for (let i=obstacles.length-1;i>=0;i--) {
        if (rectCollide(nx,ny,TUNE.TANK_OBS_R,obstacles[i])) destroyObstacle(i);
      }
      return false;
    }
    return obstacles.some(o=>rectCollide(nx,ny,TUNE.TANK_OBS_R,o));
  }
  relocate() {
    let tries=0;
    do {
      this.x=80+Math.random()*(canvas.width-160);
      this.y=80+Math.random()*(canvas.height-160);
      tries++;
    } while ((this.collidesWithObstacles(this.x,this.y) ||
             roster.some(r=>r.tank!==this && Math.hypot(this.x-r.tank.x,this.y-r.tank.y)<220)) && tries<100);
    this.spawnGrace=60;
    this.angle=Math.random()*Math.PI*2; this.turretAngle=this.angle;
  }
  wrapAround() {
    if (this.x<-10) this.x=canvas.width+10;
    if (this.x>canvas.width+10) this.x=-10;
    if (this.y<-10) this.y=canvas.height+10;
    if (this.y>canvas.height+10) this.y=-10;
  }
}

class AI {
  constructor(tank,target) {
    this.tank=tank; this.target=target;
    this.state='hunt'; this.stateTimer=0; this.strafDir=1;
    this.lastX=tank.x; this.lastY=tank.y; this.stuckFrames=0; this.avoidDir=1;
    this.flankTimer=0; this.losMiss=0;
    this.aimJitter=0; this.jitTimer=0; this.losSteady=0;
  }
  driveToward(desired, turnMul=1.3) {
    const d = normAngle(desired - this.tank.angle);
    const step = Math.min(Math.abs(d), this.tank.rotSpeed*turnMul);
    this.tank.angle += Math.sign(d)*step;
    const scale = Math.cos(d)*(this.moveMul||1);
    if (scale > 0.05) this.tank.moveForward(scale);
  }
  wrappedDelta(ax,ay,bx,by) {
    let dx=bx-ax, dy=by-ay;
    if (Math.abs(dx)>canvas.width/2) dx-=Math.sign(dx)*canvas.width;
    if (Math.abs(dy)>canvas.height/2) dy-=Math.sign(dy)*canvas.height;
    return {dx,dy};
  }
  pickTarget() {
    let best=null,bd=Infinity;
    for (const r of roster) {
      if (r.tank===this.tank) continue;
      const d=Math.hypot(r.tank.x-this.tank.x,r.tank.y-this.tank.y);
      if (d<bd){bd=d;best=r.tank;}
    }
    if (best) this.target=best;
  }
  update() {
    this.pickTarget();
    if (!this.target) return;
    const {dx:pdx,dy:pdy}=this.wrappedDelta(this.tank.x,this.tank.y,this.target.x,this.target.y);
    const distToTarget=Math.sqrt(pdx*pdx+pdy*pdy);
    const angleToTarget=Math.atan2(pdy,pdx);
    const los = hasLOS(this.tank.x,this.tank.y,this.target.x,this.target.y);
    if (los) this.losMiss=0; else this.losMiss++;
    const blocked = this.losMiss > 5;
    const diff = AI_DIFF[optDifficulty]||AI_DIFF.normal;
    this.moveMul = diff.move;
    if (los) this.losSteady++; else this.losSteady=0;
    if (--this.jitTimer<=0) {
      this.aimJitter=(Math.random()*2-1)*diff.jit;
      this.jitTimer=30+Math.floor(Math.random()*30);
    }
    if (this.tank.hasShield&&!this.tank.shieldOn) {
      const incomingMissile=missiles.some(m=>m.owner!==this.tank&&m.alive&&Math.hypot(m.x-this.tank.x,m.y-this.tank.y)<200);
      if (incomingMissile) { this.tank.hasShield=false; this.tank.shieldOn=true; this.tank.shieldTimer=SHIELD_DURATION; playShieldDeploy(); }
    }
    let chasePickup=false, chaseShield=false, chaseRapid=false;
    if (PU.missile.visible&&!this.tank.hasMissile) {
      const {dx:bx,dy:by}=this.wrappedDelta(this.tank.x,this.tank.y,PU.missile.x,PU.missile.y);
      if (Math.sqrt(bx*bx+by*by)<distToTarget*1.3) chasePickup=true;
    }
    if (!chasePickup&&PU.shield.visible&&!this.tank.hasShield&&!this.tank.shieldOn) {
      const {dx:sx,dy:sy}=this.wrappedDelta(this.tank.x,this.tank.y,PU.shield.x,PU.shield.y);
      if (Math.sqrt(sx*sx+sy*sy)<distToTarget*1.2) chaseShield=true;
    }
    if (!chasePickup&&!chaseShield&&PU.power.visible&&!hasPow(this.tank,PU.power.kind)) {
      const {dx:rx,dy:ry}=this.wrappedDelta(this.tank.x,this.tank.y,PU.power.x,PU.power.y);
      if (Math.sqrt(rx*rx+ry*ry)<distToTarget*1.2) chaseRapid=true;
    }
    const W=canvas.width,H=canvas.height,EDGE=120;
    let aimX=this.target.x,aimY=this.target.y;
    let ghostX=this.target.x,ghostY=this.target.y;
    if (this.target.x<EDGE) ghostX=this.target.x+W;
    else if (this.target.x>W-EDGE) ghostX=this.target.x-W;
    if (this.target.y<EDGE) ghostY=this.target.y+H;
    else if (this.target.y>H-EDGE) ghostY=this.target.y-H;
    if (ghostX!==this.target.x||ghostY!==this.target.y) {
      const d1=this.wrappedDelta(this.tank.x,this.tank.y,aimX,aimY);
      const d2=this.wrappedDelta(this.tank.x,this.tank.y,ghostX,ghostY);
      if (Math.sqrt(d2.dx*d2.dx+d2.dy*d2.dy)<Math.sqrt(d1.dx*d1.dx+d1.dy*d1.dy)){aimX=ghostX;aimY=ghostY;}
    }
    if (this.target.spawnGrace>0) {
      if (this.lastAimX!==undefined){ aimX=this.lastAimX; aimY=this.lastAimY; }
    } else { this.lastAimX=aimX; this.lastAimY=aimY; }
    const aimDx=aimX-this.tank.x,aimDy=aimY-this.tank.y;
    const aimAngle=Math.atan2(aimDy,aimDx)+this.aimJitter;
    const tDiff=normAngle(aimAngle-this.tank.turretAngle);
    const foeInvinc = (isInvincible(this.target) || this.target.spawnGrace>0) && !isInvincible(this.tank);
    if (Math.abs(tDiff)>0.05) {
      this.tank.turretAngle+=Math.sign(tDiff)*this.tank.rotSpeed*diff.aim;
    } else if (!foeInvinc) {
      if (this.tank.hasMissile) {
        const mx=this.tank.x+40*Math.cos(this.tank.turretAngle);
        const my=this.tank.y+40*Math.sin(this.tank.turretAngle);
        missiles.push(new Missile(mx,my,this.tank.turretAngle,this.target,this.tank));
        this.tank.hasMissile=false; playMissileLaunch();
      } else if (los && this.losSteady>diff.react) {
        this.tank.fire();
      } else if (!los && hasPow(this.tank,'ricochet') && this.losMiss>diff.react) {
        this.tank.fire();
      }
    }
    if (foeInvinc) {
      this.driveToward(angleToTarget+Math.PI, 1.7);
    } else if (chasePickup) {
      const {dx:bx,dy:by}=this.wrappedDelta(this.tank.x,this.tank.y,PU.missile.x,PU.missile.y);
      this.driveToward(Math.atan2(by,bx), 1.5);
    } else if (chaseShield) {
      const {dx:sx,dy:sy}=this.wrappedDelta(this.tank.x,this.tank.y,PU.shield.x,PU.shield.y);
      this.driveToward(Math.atan2(sy,sx), 1.5);
    } else if (chaseRapid) {
      const {dx:rx,dy:ry}=this.wrappedDelta(this.tank.x,this.tank.y,PU.power.x,PU.power.y);
      this.driveToward(Math.atan2(ry,rx), 1.5);
    } else if (blocked && distToTarget < TUNE.AI_FLANK_MAX) {
      this.flankTimer--;
      if (this.flankTimer<=0) { this.flankTimer=70+Math.floor(Math.random()*50); }
      const offset = (distToTarget>340 ? 0.55 : 1.0) * (Math.PI/2) * this.strafDir;
      this.driveToward(angleToTarget + offset, 1.7);
    } else {
      this.stateTimer--;
      if (this.stateTimer<=0) {
        const roll=Math.random();
        if (distToTarget>TUNE.AI_HUNT_DIST) this.state='hunt';
        else if (distToTarget<TUNE.AI_RETREAT_DIST) this.state='retreat';
        else { this.state=roll<0.4?'strafe':'hunt'; this.strafDir=Math.random()<0.5?1:-1; }
        this.stateTimer=60+Math.floor(Math.random()*80);
      }
      if (this.state==='hunt') {
        this.driveToward(angleToTarget, 1.3);
      } else if (this.state==='retreat') {
        this.driveToward(angleToTarget+Math.PI, 1.3);
      } else {
        this.driveToward(angleToTarget + this.strafDir*Math.PI*0.5, 1.4);
      }
    }
    if (this.tank.collidesWithObstacles(
      this.tank.x+40*Math.cos(this.tank.angle),
      this.tank.y+40*Math.sin(this.tank.angle))) {
      this.tank.angle += this.avoidDir * 0.08;
    }
    const moved = Math.hypot(this.tank.x-this.lastX, this.tank.y-this.lastY);
    this.lastX=this.tank.x; this.lastY=this.tank.y;
    if (moved < 0.4) this.stuckFrames++; else this.stuckFrames=0;
    if (this.stuckFrames > 25) {
      this.avoidDir = Math.random()<0.5 ? 1 : -1;
      this.strafDir = -this.strafDir;
      this.tank.angle += this.avoidDir * 0.5;
      this.tank.moveBackward();
      this.stuckFrames = 0;
    }
  }
}

let groundCache=null;
function buildGroundCache() {
  groundCache=document.createElement('canvas');
  groundCache.width=canvas.width; groundCache.height=canvas.height;
}
let wearCache=null, wearFadeAt=0;
function wearCtx(){
  if (!wearCache||wearCache.width!==canvas.width||wearCache.height!==canvas.height){
    wearCache=document.createElement('canvas');
    wearCache.width=canvas.width; wearCache.height=canvas.height;
  }
  return wearCache.getContext('2d');
}
const ink=a=>fieldIsDark()?`rgba(235,240,255,${a*0.85})`:`rgba(0,0,0,${a})`;
function markTread(x,y,angle){
  const w=wearCtx(); w.save(); w.translate(x,y); w.rotate(angle);
  w.fillStyle=ink(0.30);
  for(const ty of [-13,9]){
    w.fillRect(-5,ty,4,4); w.fillRect(1,ty,4,4);
  }
  w.restore();
}
function markScorch(x,y,r){
  const w=wearCtx(); w.save(); w.translate(x,y);
  let sd=((x*7919+y*104729)|0)||1; const rr=()=>{sd=(sd*16807)%2147483647; return sd/2147483647;};
  w.rotate(rr()*Math.PI*2);
  w.fillStyle=ink(0.42);
  w.beginPath();
  const pts=8+Math.floor(rr()*4);
  for(let i=0;i<pts;i++){ const a=(Math.PI*2/pts)*i, d=r*(0.55+rr()*0.75);
    i?w.lineTo(Math.cos(a)*d,Math.sin(a)*d):w.moveTo(Math.cos(a)*d,Math.sin(a)*d); }
  w.closePath(); w.fill();
  w.fillStyle=ink(0.5);
  w.beginPath();
  const ox=(rr()-0.5)*r*0.6, oy=(rr()-0.5)*r*0.6;
  for(let i=0;i<7;i++){ const a=(Math.PI*2/7)*i, d=r*0.35*(0.6+rr()*0.8);
    i?w.lineTo(ox+Math.cos(a)*d,oy+Math.sin(a)*d):w.moveTo(ox+Math.cos(a)*d,oy+Math.sin(a)*d); }
  w.closePath(); w.fill();
  w.strokeStyle=ink(0.34);
  const streaks=4+Math.floor(rr()*4);
  for(let i=0;i<streaks;i++){ const a=rr()*Math.PI*2, d0=r*0.6, d1=r*(1.1+rr()*0.9);
    w.lineWidth=1.5+rr()*2.5;
    w.beginPath(); w.moveTo(Math.cos(a)*d0,Math.sin(a)*d0); w.lineTo(Math.cos(a)*d1,Math.sin(a)*d1); w.stroke(); }
  w.fillStyle=ink(0.30);
  const bias=rr()*Math.PI*2;
  for(let i=0;i<10;i++){ const a=bias+(rr()-0.5)*2.2, d=r*(0.7+rr()*0.8);
    w.beginPath(); w.arc(Math.cos(a)*d,Math.sin(a)*d,1.5+rr()*2.5,0,Math.PI*2); w.fill(); }
  w.restore();
}
function fadeWear(){
  if (!wearCache) return;
  const now=Date.now(); if (now<wearFadeAt) return; wearFadeAt=now+500;
  const w=wearCache.getContext('2d');
  w.save(); w.globalCompositeOperation='destination-out';
  w.fillStyle='rgba(0,0,0,0.04)'; w.fillRect(0,0,wearCache.width,wearCache.height);
  w.restore();
}
function drawGround() {
  if (!groundCache||groundCache.width!==canvas.width||groundCache.height!==canvas.height) buildGroundCache();
  ctx.drawImage(groundCache,0,0);
  fadeWear();
  if (wearCache) ctx.drawImage(wearCache,0,0);
}

function updateKillsHUD(){
  if(localEntry) $('vtKills').textContent='KILLS '+localEntry.tank.kills;
}
function showToast(text) {
  const badge=$('mapBadge');
  badge.textContent=text;
  badge.style.display='block'; badge.style.opacity='1';
  clearTimeout(badge._fadeTimer); clearTimeout(badge._hideTimer);
  badge._fadeTimer=setTimeout(()=>{ badge.style.opacity='0'; },2200);
  badge._hideTimer=setTimeout(()=>{ badge.style.display='none'; },2800);
}

const SIM_STEP=1000/60, MAX_FRAME_MS=250, MAX_CATCHUP_STEPS=4;
let lastFrameT=0, simAcc=0, rafId=0;

function simulate() {
  pollGamepad();
  updateObstacles();
  for (const r of roster) r.tank.unstick();
  simParticles();
  simFlashes();
  tickRemoteTanks();

  const local = localEntry?localEntry.tank:null;
  if (local) {
    let moved=false;
    if (keys['arrowup']   ||keys['w']) { local.moveForward();  moved=true; }
    if (keys['arrowdown'] ||keys['s']) { local.moveBackward(); moved=true; }
    if (keys['arrowleft'] ||keys['a']) { local.angle-=local.rotSpeed; moved=true; }
    if (keys['arrowright']||keys['d']) { local.angle+=local.rotSpeed; moved=true; }
    if (moved) engineFrames++;
    applyMobileInput();
    if (!rightActive && !usingGamepad) local.turretAngle=Math.atan2(mouseY-local.y,mouseX-local.x);
  }
  if (engineFrames>0&&engineFrames%TUNE.ENGINE_SND_EVERY===0) playEngineRev();

  for (const r of roster) r.tank.updateBulletsMulti(roster.filter(o=>o!==r).map(o=>o.tank));

  if (aiEntry) aiEntry.ai.update();

  for (const r of roster) {
    const t=r.tank;
    const boosted = hasPow(t,'super');
    const crush   = hasPow(t,'invincible');
    t.speed = TUNE.TANK_BASE_SPEED * (boosted?2 : crush?1.25 : 1);
    t.FIRE_RATE = Math.round(TUNE.TANK_BASE_FIRE / (boosted?2:1));
    for (const k in t.powers) {
      t.powers[k]--;
      if (k==='rapid' && t.powers[k]%RAPID_CADENCE===0) t.rapidShot();
      if (t.powers[k]<=0) delete t.powers[k];
    }
  }

  for (const r of roster) {
    const victim=r.tank;
    if (!victim.authoritative || isInvincible(victim)) continue;
    for (const o of roster) {
      const crusher=o.tank;
      if (crusher===victim || !isInvincible(crusher)) continue;
      const cd=Math.hypot(crusher.x-victim.x, crusher.y-victim.y);
      if (cd < TUNE.CRUSH_R) {
        victim.hitFlash=14;
        spawnExplosion(victim.x,victim.y,'#ff8800');
        spawnExplosion(victim.x,victim.y,crusher.pal.bullet);
        playExplosion();
        crusher.kills++;
        victim.relocate();
        if (victim.isLocal) broadcastHit(victim);
        break;
      }
    }
  }

  PICKUPS.forEach(p=>p.update());
  tickShields();
  for (let i=missiles.length-1;i>=0;i--) {
    missiles[i].update();
    if (!missiles[i].alive) missiles.splice(i,1);
  }

  for (const r of roster) {
    const t=r.tank;
    if (!t.authoritative || isInvincible(t)) continue;
    for (const o of roster) {
      const u=o.tank;
      if (u===t || isInvincible(u)) continue;
      const d=Math.hypot(t.x-u.x,t.y-u.y);
      if (d < TUNE.TANK_SEP) {
        const mx=(t.x+u.x)/2, my=(t.y+u.y)/2;
        spawnExplosion(mx,my,'#ffffff');
        spawnExplosion(mx,my,'#ffaa00');
        playExplosion();
        t.relocate();
        if (t.isLocal) broadcastHit(t);
        break;
      }
    }
  }
}

function render() {
  ctx.clearRect(0,0,canvas.width,canvas.height);
  let shaken=false;
  if (shakeT>0) {
    shakeT--;
    const k=shakeMag*(shakeT/shakeDur);
    ctx.save(); shaken=true;
    ctx.translate(canvas.width/2,canvas.height/2);
    ctx.rotate((Math.random()-.5)*0.003*k);
    ctx.translate(-canvas.width/2+(Math.random()-.5)*k*2,-canvas.height/2+(Math.random()-.5)*k*2);
  }
  drawGround();
  drawObstacles();
  drawParticles();
  drawFlashes();
  PICKUPS.forEach(p=>p.draw());
  drawActiveShields();
  for (const m of missiles) m.draw();
  for (const r of roster) r.tank.draw();
  if (!touchMode && !usingGamepad && localEntry) {
    const local=localEntry.tank;
    ctx.save();
    ctx.translate(mouseX,mouseY);
    const nearest=nearestOther(local);
    const onTarget = nearest && Math.hypot(mouseX-nearest.x,mouseY-nearest.y)<36;
    const cCol = onTarget ? (gameFrame%24<12?'rgba(255,60,40,0.95)':'rgba(255,220,40,0.95)')
                          : 'rgba(102,255,102,0.9)';
    ctx.strokeStyle=cCol; ctx.lineWidth=2;
    ctx.shadowColor=cCol; ctx.shadowBlur=6;
    ctx.beginPath(); ctx.arc(0,0,22,0,Math.PI*2); ctx.stroke();
    ctx.beginPath();
    for(const [x1,y1,x2,y2] of [[0,-34,0,-10],[0,10,0,34],[-34,0,-10,0],[10,0,34,0]]){
      ctx.moveTo(x1,y1); ctx.lineTo(x2,y2);
    }
    ctx.stroke();
    ctx.fillStyle=cCol;
    ctx.fillRect(-1.5,-1.5,3,3);
    ctx.restore();
  }
  if (shaken) ctx.restore();
  updateKillsHUD();
}

function frame(now) {
  rafId=requestAnimationFrame(frame);
  if (!lastFrameT) lastFrameT=now;
  simAcc += Math.min(now-lastFrameT, MAX_FRAME_MS);
  lastFrameT = now;
  let stepped=false, catchup=0;
  while (simAcc >= SIM_STEP) {
    if (hitstopSteps>0) { hitstopSteps--; simAcc -= SIM_STEP; stepped=true; continue; }
    simulate(); simAcc -= SIM_STEP; stepped=true;
    if (++catchup >= MAX_CATCHUP_STEPS) { simAcc = 0; break; }
  }
  if (stepped) render();
  if (fxPending) { renderObstacleFX(fxPending.o,fxPending.bucket); fxPending=null; }
}

function onMouseMove(e){mouseX=e.clientX;mouseY=e.clientY;usingGamepad=false;}
function onMouseDown(e){
  if (!localEntry) return;
  if (e.button===0) { localEntry.tank.fire(); }
  if (e.button===2) fireMissile();
}
function onContextMenu(e){e.preventDefault();}

function applyTankControls(gp, tank) {
  const prev=padPrev[0]||[];
  const now=gp.buttons.map(b=>b.pressed);
  const edge=i=>now[i]&&!prev[i];
  const held=i=>!!now[i];
  const ax=i=>gp.axes[i]||0;
  const DZ=0.28;
  const lx=ax(0), ly=ax(1); let moved=false;
  if (ly < -DZ) { tank.moveForward();  moved=true; }
  else if (ly > DZ) { tank.moveBackward(); moved=true; }
  if (Math.abs(lx) > DZ) { tank.angle += lx*tank.rotSpeed*1.5; moved=true; }
  if (held(12)) { tank.moveForward();  moved=true; }
  if (held(13)) { tank.moveBackward(); moved=true; }
  if (held(14)) { tank.angle -= tank.rotSpeed; moved=true; }
  if (held(15)) { tank.angle += tank.rotSpeed; moved=true; }
  if (moved) engineFrames++;
  const rx=ax(2), ry=ax(3);
  if (Math.hypot(rx,ry) > DZ) tank.turretAngle = Math.atan2(ry,rx);
  if (held(7) || held(0)) tank.fire();
  if (edge(5) || edge(1)) fireMissileFor(tank);
  if (edge(4) || edge(6) || edge(2)) deployShield(tank);
  padPrev[0]=now;
}
function pollGamepad() {
  const pads = navigator.getGamepads ? navigator.getGamepads() : [];
  const list=[]; for(const p of pads){ if(p) list.push(p); }
  if (list.length===0){ padPrev=[[]]; return; }
  const gp0=list[0];
  const now0=gp0.buttons.map(b=>b.pressed);
  const anyBtn=now0.some(p=>p)||[0,1,2,3].some(i=>Math.abs(gp0.axes[i]||0)>0.28);
  if (anyBtn) { usingGamepad=true; hideTouchControls(); }
  if (!localEntry){ padPrev[0]=now0; return; }
  applyTankControls(gp0, localEntry.tank);
}
function onGpConnect(){ usingGamepad=true; showToast('CONTROL CONECTADO'); }
function onGpDisconnect(){}

function sizeCanvas(){
  canvas.width=window.innerWidth; canvas.height=window.innerHeight;
  canvas.style.width=window.innerWidth+'px'; canvas.style.height=window.innerHeight+'px';
}
function onResize(){ sizeCanvas(); regenerateCurrentMap(); }

function setupStick(zoneId,nubId,onMove,onEnd) {
  const zone=$(zoneId), nub=$(nubId);
  let touchId=null;
  function getOffset(t) {
    const r=zone.getBoundingClientRect();
    const cx=r.left+r.width/2, cy=r.top+r.height/2;
    const ox=t.clientX-cx, oy=t.clientY-cy;
    const dist=Math.sqrt(ox*ox+oy*oy), max=r.width/2-nub.offsetWidth/2-2;
    const ratio=Math.min(dist,max)/(max||1), ang=Math.atan2(oy,ox);
    const clamp=Math.min(dist,max);
    nub.style.transform='none';
    nub.style.left=`${clamp*Math.cos(ang)+r.width/2-nub.offsetWidth/2}px`;
    nub.style.top=`${clamp*Math.sin(ang)+r.height/2-nub.offsetHeight/2}px`;
    return {ang,ratio,ox:ox/Math.max(dist,1),oy:oy/Math.max(dist,1),dist};
  }
  zone.addEventListener('touchstart',e=>{
    e.preventDefault(); if (touchId!==null) return;
    touchId=e.changedTouches[0].identifier;
    onMove(getOffset(e.changedTouches[0]));
  },{passive:false});
  zone.addEventListener('touchmove',e=>{
    e.preventDefault();
    for (const t of e.changedTouches) if (t.identifier===touchId){onMove(getOffset(t));break;}
  },{passive:false});
  zone.addEventListener('touchend',e=>{
    for (const t of e.changedTouches) if (t.identifier===touchId){
      touchId=null; nub.style.left='50%'; nub.style.top='50%';
      nub.style.transform='translate(-50%,-50%)'; if (onEnd) onEnd(); break;
    }
  },{passive:false});
}
let leftInput=null, rightInput=null, rightNub=null;
function applyMobileInput() {
  const DEAD=TUNE.TOUCH_DEAD;
  const local=localEntry?localEntry.tank:null;
  if (!local) return;
  if (leftInput && leftInput.ratio>DEAD) {
    const d=normAngle(leftInput.ang - local.angle);
    const step=Math.min(Math.abs(d), local.rotSpeed*2.4);
    local.angle += Math.sign(d)*step;
    const scale=Math.max(0,Math.cos(d))*leftInput.ratio;
    if (scale>0.05) { local.moveForward(scale); engineFrames++; }
  }
  if (rightInput && rightInput.ratio>0.15) {
    rightActive=true;
    let want=rightInput.ang;
    const nearest=nearestOther(local);
    if (nearest) {
      const bearing=Math.atan2(nearest.y-local.y, nearest.x-local.x);
      if (Math.abs(normAngle(want-bearing))<0.20) want=bearing;
    }
    const td=normAngle(want - local.turretAngle);
    local.turretAngle += Math.sign(td)*Math.min(Math.abs(td), TUNE.TOUCH_AIM_SPD);
    if (rightInput.ratio>TUNE.TOUCH_FIRE) { local.fire(); }
  } else rightActive=false;
}

function hideTouchControls(){
  if (!touchMode) return;
  touchMode=false;
  $('mobile-controls').style.display='none';
}
const MOVEMENT_KEYS=['w','a','s','d','arrowup','arrowdown','arrowleft','arrowright',' ','q'];
function onKeyDown(e){
  if (e.target && (e.target.tagName==='TEXTAREA'||e.target.tagName==='INPUT')) return;
  const k=e.key.toLowerCase();
  keys[k]=true;
  const POS={KeyW:'w',KeyA:'a',KeyS:'s',KeyD:'d'};
  if (POS[e.code]) keys[POS[e.code]]=true;
  if (MOVEMENT_KEYS.includes(k)||POS[e.code]) hideTouchControls();
  if (e.code==='Space'){ e.preventDefault(); if(localEntry) localEntry.tank.fire(); }
  if (e.code==='KeyQ'){ deployPlayerShield(); }
}
function onKeyUp(e){
  keys[e.key.toLowerCase()]=false;
  const POS={KeyW:'w',KeyA:'a',KeyS:'s',KeyD:'d'};
  if (POS[e.code]) keys[POS[e.code]]=false;
}
function clearKeys(){ for(const k in keys) keys[k]=false; }
function onVisChange(){
  try{ if(!document.hidden && audioCtx && audioCtx.state!=='running') audioCtx.resume(); }catch(e){}
  if (document.hidden) clearKeys();
}

let trysteroP=null;
function loadTrystero(){ if(!trysteroP) trysteroP=import('https://cdn.jsdelivr.net/npm/trystero@0.26.0/+esm'); return trysteroP; }
const NET_APP='cheagana-vivetanks', NET_ROOM='arena';
let room=null, selfId=null, tsAction=null, hitAction=null, spawnAction=null, isHost=true, netInterval=null;

function computeHost(){
  if (!room) return true;
  const ids=[selfId,...Object.keys(room.getPeers())].sort();
  return ids[0]===selfId;
}
function spawnPointFor(){
  let x=canvas.width/2,y=canvas.height/2,tries=0;
  do{ x=80+Math.random()*(canvas.width-160); y=80+Math.random()*(canvas.height-160); tries++; }
  while (obstacles.some(o=>rectCollide(x,y,TUNE.TANK_OBS_R,o)) && tries<60);
  return {x,y};
}
function pickColor(exclude){
  let k; do{ k=COLOR_KEYS[Math.floor(Math.random()*COLOR_KEYS.length)]; }while(k===exclude);
  return k;
}
function makeTank(colorKey,name,isLocal,peerId){
  const sp=spawnPointFor();
  const t=new Tank(sp.x,sp.y,Math.random()*Math.PI*2,colorKey,name,isLocal,peerId);
  t.spawnGrace=60;
  return t;
}
function addRemoteTank(peerId){
  const used=roster.map(r=>r.tank.colorKey);
  const colorKey=COLOR_KEYS.find(k=>!used.includes(k))||pickColor();
  const t=makeTank(colorKey,peerId.slice(0,4).toUpperCase(),false,peerId);
  t.authoritative=false;
  roster.push({tank:t,ai:null,peerId,isLocal:false});
}
function removeRemoteTank(peerId){
  const idx=roster.findIndex(r=>r.peerId===peerId);
  if (idx>=0){ const t=roster[idx].tank; spawnExplosion(t.x,t.y,t.pal.bullet); roster.splice(idx,1); }
}
function updateNetHUD(){
  const el=$('vtNet'); if(!el) return;
  if (!room) { el.textContent='NET: sin conexion (jugando solo)'; return; }
  const n=Object.keys(room.getPeers()).length;
  el.textContent='NET: '+(n>0?(n+' jugador'+(n>1?'es':'')+' conectado'+(n>1?'s':'')):'esperando jugadores...');
}
function broadcastHit(tank){ if(hitAction){ try{ hitAction.send({x:tank.x,y:tank.y,angle:tank.angle}); }catch(e){} } }
function applyRemoteHit(peerId,d){
  const r=roster.find(x=>x.peerId===peerId);
  if (!r) return;
  r.tank.x=d.x; r.tank.y=d.y; r.tank.angle=d.angle; r.tank.turretAngle=d.angle;
  r.tank.spawnGrace=60;
  spawnExplosion(d.x,d.y,r.tank.pal.bullet);
}
function lerpAngle(a,b,f){ return a+normAngle(b-a)*f; }
function applyRemoteState(peerId,d){
  window.__vtNetStats.recv++;
  const r=roster.find(x=>x.peerId===peerId);
  if (!r) return;
  const t=r.tank;
  t._netTX=d.x; t._netTY=d.y; t._netTA=d.angle; t._netTT=d.turret;
  t.hasShield=!!d.hasShield; t.shieldOn=!!d.shieldOn;
  const seq=d.seq||0;
  const lastSeq=t._lastSeq||0;
  if (seq>lastSeq) {
    const delta=Math.min(seq-lastSeq,3);
    t._lastSeq=seq;
    for (let i=0;i<delta;i++){ t.fireCooldown=0; t.fire(); }
  }
}
function tickRemoteTanks(){
  for (const r of roster) {
    if (r.isLocal || r===aiEntry) continue;
    const t=r.tank;
    if (t._netTX==null) continue;
    t.x+=(t._netTX-t.x)*0.3; t.y+=(t._netTY-t.y)*0.3;
    t.angle=lerpAngle(t.angle,t._netTA,0.3);
    t.turretAngle=lerpAngle(t.turretAngle,t._netTT,0.3);
  }
}
function netTick(){
  if (!localEntry) return;
  const t=localEntry.tank;
  if (tsAction) { try{ tsAction.send({x:t.x,y:t.y,angle:t.angle,turret:t.turretAngle,seq:t.shotSeq,hasShield:t.hasShield,shieldOn:t.shieldOn}); window.__vtNetStats.sent++; }catch(e){ window.__vtNetStats.err=String(e); } }
}
function broadcastObsAdd(o){ if(spawnAction){ try{ spawnAction.send({t:'oa',o:serializeObstacle(o)}); }catch(e){} } }
function broadcastObstaclesFull(){ if(spawnAction){ try{ spawnAction.send({t:'obs',list:obstacles.map(serializeObstacle)}); }catch(e){} } }

async function initNet(){
  try{
    const mod=await loadTrystero();
    selfId=mod.selfId;
    room=mod.joinRoom({appId:NET_APP,relayConfig:{redundancy:12}},NET_ROOM);
    tsAction=room.makeAction('ts');
    hitAction=room.makeAction('hit');
    spawnAction=room.makeAction('spawn');
    tsAction.onMessage=(d,{peerId})=>applyRemoteState(peerId,d);
    hitAction.onMessage=(d,{peerId})=>applyRemoteHit(peerId,d);
    spawnAction.onMessage=(d,{peerId})=>{
      if (isHost) return;
      if (d.t==='obs') applyObstacleList(d.list);
      else if (d.t==='oa') applyObsAdd(d.o);
      else if (d.t==='pk'){ const p=PU[d.key]; if(p){ if(d.key==='power') p.kind=d.kind; p.x=d.x;p.y=d.y;p.visible=true;p.timer=0;p.flash=80; } }
      else if (d.t==='pkall'){
        for (const key of ['missile','shield','power']){
          const s=d[key], p=PU[key];
          if (!s||!p) continue;
          p.visible=s.visible; p.x=s.x; p.y=s.y; p.timer=s.timer; if(key==='power') p.kind=s.kind;
        }
      }
    };
    room.onPeerJoin=peerId=>{
      addRemoteTank(peerId);
      isHost=computeHost();
      if (isHost) {
        try{
          spawnAction.send({t:'obs',list:obstacles.map(serializeObstacle)},{target:peerId});
          spawnAction.send({t:'pkall',missile:pkSnap(PU.missile),shield:pkSnap(PU.shield),power:pkSnap(PU.power)},{target:peerId});
        }catch(e){}
      }
      updateNetHUD();
    };
    room.onPeerLeave=peerId=>{ removeRemoteTank(peerId); isHost=computeHost(); updateNetHUD(); };
    isHost=computeHost();
    updateNetHUD();
  }catch(e){ isHost=true; room=null; console.error('[vivetanks] error de red',e); updateNetHUD(); }
  netInterval=setInterval(netTick,60);
}

function boot(){
  sizeCanvas();
  const aiColor=pickColor();
  const localColor=pickColor(aiColor);

  const aiTank=new Tank(canvas.width*0.25,canvas.height*0.25,0,aiColor,'CPU',false,null);
  aiTank.authoritative=true;
  roster.push({tank:aiTank,ai:null,peerId:null,isLocal:false});
  aiEntry=roster[0];

  const localTank=new Tank(canvas.width*0.75,canvas.height*0.75,Math.PI,localColor,'YOU',true,null);
  localTank.authoritative=true;
  roster.push({tank:localTank,ai:null,peerId:null,isLocal:true});
  localEntry=roster[1];

  aiEntry.ai=new AI(aiTank,localTank);

  generateObstacles();
  for (const r of roster) r.tank.relocate();
  PICKUPS.forEach(p=>{
    p.spawn();
    p.visible=!!p.cfg.startVisible;
    p.timer=p.cfg.startTimer;
  });

  rightNub=$('right-nub');
  setupStick('left-zone','left-nub',data=>{leftInput=data;},()=>{leftInput=null;});
  setupStick('right-zone','right-nub',data=>{
    rightInput=data;
    rightNub.classList.toggle('firing', data.ratio>TUNE.TOUCH_FIRE);
  },()=>{
    rightInput=null;
    rightNub.classList.remove('firing');
  });

  window.addEventListener('resize',onResize);
  window.addEventListener('keydown',onKeyDown);
  window.addEventListener('keyup',onKeyUp);
  window.addEventListener('blur',clearKeys);
  window.addEventListener('mousemove',onMouseMove);
  window.addEventListener('mousedown',onMouseDown);
  window.addEventListener('contextmenu',onContextMenu);
  window.addEventListener('gamepadconnected',onGpConnect);
  window.addEventListener('gamepaddisconnected',onGpDisconnect);
  document.addEventListener('visibilitychange',onVisChange);

  rafId=requestAnimationFrame(frame);

  initNet().then(()=>{
    if (isHost) {
      broadcastObstaclesFull();
      PICKUPS.forEach(p=>{ if(p.visible) broadcastPickupSpawn(p); });
    }
  });
}

function teardown(){
  cancelAnimationFrame(rafId);
  if (musicTimer) clearInterval(musicTimer);
  if (netInterval) clearInterval(netInterval);
  window.removeEventListener('resize',onResize);
  window.removeEventListener('keydown',onKeyDown);
  window.removeEventListener('keyup',onKeyUp);
  window.removeEventListener('blur',clearKeys);
  window.removeEventListener('mousemove',onMouseMove);
  window.removeEventListener('mousedown',onMouseDown);
  window.removeEventListener('contextmenu',onContextMenu);
  window.removeEventListener('gamepadconnected',onGpConnect);
  window.removeEventListener('gamepaddisconnected',onGpDisconnect);
  window.removeEventListener('pointerdown',armAudio);
  window.removeEventListener('keydown',armAudio);
  document.removeEventListener('visibilitychange',onVisChange);
  if (room) { try{ room.leave(); }catch(e){} }
  if (audioCtx) { try{ audioCtx.close(); }catch(e){} }
  if (contentEl) contentEl.setAttribute('style',ctPrev||'');
  document.body.style.overflow=bodyOverflowPrev||'';
  if (adSlotEl) adSlotEl.style.display=adSlotPrev||'';
  if (disqusEl) disqusEl.style.display=disqusPrev||'';
}
if (contentEl) contentEl.addEventListener('contentUnload',teardown,{once:true});

window.__vtNetStats={sent:0,recv:0,err:null};
window.__vtDebug=()=>({
  net:window.__vtNetStats,
  selfId,isHost,
  peers:room?Object.keys(room.getPeers()):null,
  roster:roster.map(r=>({peerId:r.peerId,isLocal:r.isLocal,isAi:r===aiEntry,x:r.tank.x,y:r.tank.y,netTX:r.tank._netTX,netTY:r.tank._netTY,lastSeq:r.tank._lastSeq}))
});

boot();
}();
</script>
