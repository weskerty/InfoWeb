<!DOCTYPE html>
<html lang="es">
<head><meta charset="UTF-8"></head>
<body>

<style data-content>
:root{
  --fb-accent:#39ff14;
  --fb-danger:#ff2d6b;
  --fb-gold:#ffd700;
  --fb-hud:48px;
}
#FB_W{
  position:relative;
  width:100%;
  height:calc(50vh - var(--fb-hud));
  min-height:220px;
  overflow:hidden;
  font-family:'Courier New',monospace;
  background:transparent;
  user-select:none;
  -webkit-user-select:none;
  touch-action:none;
}
#FB_CV{position:absolute;inset:0;width:100%;height:100%;}
#FB_HUD{
  position:absolute;
  top:0;left:0;right:0;
  height:var(--fb-hud);
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 16px;
  pointer-events:none;
  z-index:10;
}
#FB_SC{
  font-size:2rem;
  font-weight:900;
  color:var(--fb-accent);
  text-shadow:0 0 12px var(--fb-accent),0 0 24px var(--fb-accent);
  letter-spacing:2px;
}
#FB_SH{
  font-size:1rem;
  font-weight:900;
  color:var(--fb-gold);
  text-shadow:0 0 10px var(--fb-gold);
  letter-spacing:2px;
  min-width:40px;
  text-align:center;
}
#FB_NET{font-size:.7rem;color:#ffffff55;text-align:right;line-height:1.4;}
#FB_NET.FB_con{color:var(--fb-accent);}
#FB_OV{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  gap:10px;
  z-index:20;
  background:#00000066;
}
#FB_OV.FB_h{display:none;}
#FB_OV h2{
  color:var(--fb-accent);
  font-size:1.6rem;
  font-weight:900;
  text-shadow:0 0 20px var(--fb-accent);
  margin:0;
  letter-spacing:4px;
  text-transform:uppercase;
}
#FB_OV p{color:#fff;font-size:.85rem;margin:0;opacity:.8;}
#FB_BTN{
  margin-top:6px;
  padding:8px 28px;
  background:transparent;
  border:2px solid var(--fb-accent);
  color:var(--fb-accent);
  font-family:'Courier New',monospace;
  font-size:.9rem;
  font-weight:900;
  letter-spacing:3px;
  cursor:pointer;
  text-transform:uppercase;
  text-shadow:0 0 8px var(--fb-accent);
  box-shadow:0 0 16px #39ff1444;
  transition:background .15s,color .15s;
}
#FB_BTN:hover,#FB_BTN:active{background:var(--fb-accent);color:#070710;}
#FB_MUTE{
  position:absolute;
  bottom:8px;right:8px;
  background:transparent;
  border:1px solid #ffffff33;
  color:#fff;
  font-size:1rem;
  width:30px;height:30px;
  border-radius:50%;
  cursor:pointer;
  z-index:15;
  display:none;
  align-items:center;
  justify-content:center;
  transition:border-color .2s;
}
#FB_MUTE.FB_vis{display:flex;}
#FB_MUTE.FB_muted{border-color:var(--fb-danger);color:var(--fb-danger);}
</style>

<div id="FB_W">
  <canvas id="FB_CV"></canvas>
  <div id="FB_HUD">
    <div id="FB_SC">0</div>
    <div id="FB_SH"></div>
    <div id="FB_NET">sin red</div>
  </div>
  <div id="FB_OV">
    <h2 id="FB_OT">FLAPPY</h2>
    <p id="FB_OM">Toca o pulsa espacio para jugar</p>
    <button id="FB_BTN">JUGAR</button>
  </div>
  <button id="FB_MUTE">🎤</button>
</div>

<script>
(function(){

const FB={
  W:document.getElementById('FB_W'),
  cv:document.getElementById('FB_CV'),
  sc:document.getElementById('FB_SC'),
  sh:document.getElementById('FB_SH'),
  net:document.getElementById('FB_NET'),
  ov:document.getElementById('FB_OV'),
  ot:document.getElementById('FB_OT'),
  om:document.getElementById('FB_OM'),
  btn:document.getElementById('FB_BTN'),
  mute:document.getElementById('FB_MUTE'),
  content:document.getElementById('content'),
};
const ctx=FB.cv.getContext('2d');

const CFG={
  gravity:0.38,
  flap:-6.5,
  pipeW:52,
  pipeGap:110,
  pipeSpd:2.2,
  pipeDist:260,
  birdX:80,
  birdR:14,
  birdDrawR:22,
  killMargin:20,
  lobbyId:'flappy-p2p-v1',
  appId:{appId:'flappy-p2p-v1'},
  imgSrc:'https://picsum.photos/seed/',
  posSendMs:50,
  pipeImgCount:10,
  pwChance:0.05,
  blinkDurMs:900,
  blinkHz:80,
  base:'web/adjuntos/Flappy_Esquivar_Obstaculos/',
};

const SFX={
  bgm:new Audio(),
  jump:new Audio(),
  hit:new Audio(),
  pw:new Audio(),
};
SFX.bgm.src=CFG.base+'bgm.ogg';
SFX.jump.src=CFG.base+'jump.ogg';
SFX.hit.src=CFG.base+'hit.ogg';
SFX.pw.src=CFG.base+'pipeW.ogg';
SFX.bgm.loop=true;
SFX.bgm.volume=0.4;
SFX.jump.volume=0.6;
SFX.hit.volume=0.7;
SFX.pw.volume=0.8;

function sfxPlay(a){if(!a.src)return;a.currentTime=0;a.play().catch(function(){});}
function bgmPlay(){if(!SFX.bgm.src)return;SFX.bgm.play().catch(function(){});}
function bgmPause(){SFX.bgm.pause();}

let W=0,H=0;
function FB_resize(){
  W=FB.W.offsetWidth;
  H=FB.W.offsetHeight;
  FB.cv.width=W;
  FB.cv.height=H;
}
FB_resize();
const RO=new ResizeObserver(FB_resize);
RO.observe(FB.W);

function rng32(s){
  return function(){
    s=s+0x6d2b79f5|0;
    let t=Math.imul(s^s>>>15,1|s);
    t^=t+Math.imul(t^t>>>7,61|t);
    return((t^t>>>14)>>>0)/4294967296;
  };
}

const PI_fallback=(function(){
  const img=new Image();
  img.src=CFG.base+'pipe.avif';
  return img;
})();

const PI_pw=(function(){
  const img=new Image();
  img.src=CFG.base+'pipeW.avif';
  return img;
})();

const pipeImgs=[];
(function(){
  for(let i=0;i<CFG.pipeImgCount;i++){
    const img=new Image();
    img.src=CFG.base+'pipe'+i+'.avif';
    pipeImgs.push(img);
  }
})();

const MY_IMG=(function(){
  const img=new Image();
  img.src=CFG.base+'im.avif';
  return img;
})();

function PI_get(idx){
  const img=pipeImgs[idx];
  if(img&&img.complete&&img.naturalWidth)return img;
  if(PI_fallback.complete&&PI_fallback.naturalWidth)return PI_fallback;
  return null;
}

let rng=null;
let pipes=[],score=0,best=0,shields=0;
let by=0,bvy=0,alive=false,started=false;
let blinkEnd=0,hitCoolEnd=0;
let rafId=null,posIv=null;

function SH_update(){
  FB.sh.textContent=shields>0?'❤️':'';
}

function newPipe(x){
  const margin=H*0.12;
  const isPW=rng()<CFG.pwChance;
  const imgIdx=isPW?-1:Math.floor(rng()*CFG.pipeImgCount);
  return{x,topH:margin+rng()*(H-margin*2-CFG.pipeGap),passed:false,imgIdx,isPW,pwTaken:false};
}

function initGame(){
  rng=rng32(Date.now()&0xFFFFFFFF);
  pipes=[];
  score=0;
  shields=0;
  by=H/2;
  bvy=0;
  alive=true;
  started=false;
  blinkEnd=0;hitCoolEnd=0;
  FB.sc.textContent='0';
  SH_update();
  pipes.push(newPipe(W+CFG.pipeDist));
  pipes.push(newPipe(W+CFG.pipeDist*2));
}

function flap(){
  if(!alive)return;
  if(!started){started=true;bgmPlay();}
  bvy=CFG.flap;
  sfxPlay(SFX.jump);
}

function tick(){
  if(!alive||!started)return;
  bvy+=CFG.gravity;
  by+=bvy;
  for(const p of pipes)p.x-=CFG.pipeSpd;
  if(pipes[pipes.length-1].x<W-CFG.pipeDist)pipes.push(newPipe(W+10));
  while(pipes.length&&pipes[0].x<-CFG.pipeW-CFG.killMargin)pipes.shift();
  const bx=CFG.birdX,br=CFG.birdR-3;
  const now=performance.now();
  for(const p of pipes){
    if(!p.passed&&p.x+CFG.pipeW<bx){
      p.passed=true;
      if(p.isPW&&!p.pwTaken){
        p.pwTaken=true;
        if(shields<1)shields++;
        SH_update();
        sfxPlay(SFX.pw);
      }else if(!p.isPW){
        score++;
        FB.sc.textContent=score;
      }
    }
    if(p.isPW)continue;
    const inX=bx+br>p.x&&bx-br<p.x+CFG.pipeW;
    const inY=by-br<p.topH||by+br>p.topH+CFG.pipeGap;
    if(inX&&inY&&now>hitCoolEnd){
      if(shields>0){
        shields--;
        SH_update();
        blinkEnd=now+CFG.blinkDurMs;
        hitCoolEnd=now+CFG.blinkDurMs;
        sfxPlay(SFX.hit);
      }else{
        die();return;
      }
    }
  }
  const km=CFG.killMargin;
  if(by+CFG.birdR<-km||by-CFG.birdR>H+km){
    if(shields>0&&now>hitCoolEnd){
      shields--;
      SH_update();
      blinkEnd=now+CFG.blinkDurMs;
      hitCoolEnd=now+CFG.blinkDurMs;
      by=Math.max(CFG.birdR,Math.min(H-CFG.birdR,by));
      bvy=0;
      sfxPlay(SFX.hit);
    }else if(shields===0){
      die();return;
    }
  }
}

function die(){
  alive=false;
  bgmPause();
  sfxPlay(SFX.hit);
  if(score>best)best=score;
  FB.ot.textContent='Caiste 😿';
  FB.om.textContent='Esquivados: '+score+' | Mejor: '+best;
  FB.ov.classList.remove('FB_h');
}

function drawPipe(p){
  const botY=p.topH+CFG.pipeGap;
  const botH=H-botY;
  let img;
  if(p.isPW){
    img=(PI_pw.complete&&PI_pw.naturalWidth)?PI_pw:PI_get(0);
  }else{
    img=PI_get(p.imgIdx);
  }
  if(img){
    ctx.drawImage(img,p.x,0,CFG.pipeW,p.topH);
    ctx.drawImage(img,p.x,botY,CFG.pipeW,botH);
  }else{
    const g=ctx.createLinearGradient(p.x,0,p.x+CFG.pipeW,0);
    if(p.isPW){
      g.addColorStop(0,'#7a5500');g.addColorStop(.4,'#ffd700');g.addColorStop(1,'#7a5500');
    }else{
      g.addColorStop(0,'#1a3a1a');g.addColorStop(.4,'#2d7a2d');g.addColorStop(1,'#1a3a1a');
    }
    ctx.fillStyle=g;
    ctx.fillRect(p.x,0,CFG.pipeW,p.topH);
    ctx.fillRect(p.x,botY,CFG.pipeW,botH);
  }
  if(p.isPW&&!p.pwTaken){
    ctx.save();
    const cx=p.x+CFG.pipeW/2,cy=p.topH+CFG.pipeGap/2;
    ctx.font='bold 18px "Courier New"';
    ctx.textAlign='center';
    ctx.textBaseline='middle';
    ctx.fillStyle='#ffd700';
    ctx.shadowColor='#ffd700';
    ctx.shadowBlur=12;
    ctx.fillText('❤️',cx,cy);
    ctx.restore();
  }
}

const peerImgs={};
function getPeerImg(id){
  if(peerImgs[id])return peerImgs[id];
  const img=new Image();
  img.crossOrigin='anonymous';
  img.src=CFG.imgSrc+id+'/'+(CFG.birdDrawR*4)+'/'+(CFG.birdDrawR*4);
  return(peerImgs[id]=img);
}

const MY_ID=Math.random().toString(36).slice(2,8);
const peers={};

function drawBird(x,y,id,alpha,angle){
  ctx.save();
  ctx.globalAlpha=alpha;
  ctx.translate(x,y);
  ctx.rotate(angle);
  const r=CFG.birdDrawR;
  const img=id===MY_ID?MY_IMG:getPeerImg(id);
  ctx.beginPath();
  ctx.arc(0,0,r,0,Math.PI*2);
  if(img.complete&&img.naturalWidth){
    ctx.clip();
    ctx.drawImage(img,-r,-r,r*2,r*2);
  }else{
    ctx.fillStyle=id===MY_ID?'#39ff14':'#f7c948';
    ctx.fill();
  }
  ctx.restore();
}

function render(){
  ctx.clearRect(0,0,W,H);
  for(const p of pipes)drawPipe(p);

  for(const [pid,ps] of Object.entries(peers)){
    if(ps.y!=null&&ps.alive)drawBird(CFG.birdX+4,ps.y,pid,0.72,0);
  }
  const now=performance.now();
  const blinking=now<blinkEnd;
  let birdAlpha=1;
  if(blinking){
    birdAlpha=Math.floor((blinkEnd-now)/CFG.blinkHz)%2===0?0.15:1;
  }
  drawBird(CFG.birdX,by,MY_ID,birdAlpha,Math.max(-0.5,Math.min(1.2,bvy*0.06)));

  if(!started&&alive){
    ctx.fillStyle='#ffffff55';
    ctx.font='bold 13px "Courier New"';
    ctx.textAlign='center';
    ctx.fillText('TAP / ESPACIO',W/2,H/2+40);
    ctx.textAlign='left';
  }
}

function loop(){
  tick();
  render();
  rafId=requestAnimationFrame(loop);
}

function startGame(){
  if(rafId){cancelAnimationFrame(rafId);rafId=null;}
  FB.ov.classList.add('FB_h');
  initGame();
  rafId=requestAnimationFrame(loop);
}

const FB_key=function(e){
  if(e.code==='Space'||e.code==='ArrowUp'){
    e.preventDefault();
    if(!alive){startGame();return;}
    flap();
  }
};
document.addEventListener('keydown',FB_key);

FB.btn.addEventListener('click',startGame);
FB.W.addEventListener('click',function(e){
  if(e.target===FB.btn)return;
  if(!alive){startGame();return;}
  flap();
});
FB.W.addEventListener('touchstart',function(e){
  e.preventDefault();
  if(!alive){startGame();return;}
  flap();
},{passive:false});

let room=null,sendPos=null;
let ls=null,ra=null,mm=false,voiceInit=false;

async function initVoice(){
  if(voiceInit||!room)return;
  voiceInit=true;
  try{
    ls=await navigator.mediaDevices.getUserMedia({audio:{echoCancellation:1,noiseSuppression:1},video:false});
  }catch(e){ls=null;voiceInit=false;return;}
  FB.mute.classList.add('FB_vis');
  room.addStream(ls);
  room.onPeerStream=function(s){
    if(ra){ra.pause();ra.srcObject=null;ra.remove();}
    ra=document.createElement('audio');
    ra.srcObject=s;ra.autoplay=1;ra.playsInline=1;ra.volume=.7;
    document.body.appendChild(ra);
  };
}

async function initNet(){
  try{
    const mod=await import('https://cdn.jsdelivr.net/npm/trystero@0.26.0/+esm');
    const {joinRoom}=mod;
    room=joinRoom(CFG.appId,CFG.lobbyId);
    FB.net.textContent='...';
    const FP_A1=room.makeAction('pos');
    sendPos=FP_A1.send;
    FP_A1.onMessage=function(d,{peerId:from}){
      if(!d||typeof d.y!=='number')return;
      if(!peers[from])peers[from]={};
      peers[from].y=d.y;
      peers[from].alive=!!d.alive;
    };
    room.onPeerJoin=function(id){
      peers[id]={};
      FB.net.textContent=Object.keys(peers).length+' online';
      FB.net.classList.add('FB_con');
      if(ls)room.addStream(ls,{target:id});
      initVoice();
    };
    room.onPeerLeave=function(id){
      delete peers[id];
      const n=Object.keys(peers).length;
      FB.net.textContent=n?n+' online':'0';
      if(!n)FB.net.classList.remove('FB_con');
    };
  }catch(e){
    FB.net.textContent='sin red';
  }
}

posIv=setInterval(function(){
  if(sendPos&&alive)sendPos({y:by,alive}).catch(function(){});
},CFG.posSendMs);

FB.mute.addEventListener('click',function(){
  mm=!mm;
  if(ls)ls.getAudioTracks().forEach(function(t){t.enabled=!mm;});
  FB.mute.classList.toggle('FB_muted',mm);
  FB.mute.textContent=mm?'🔇':'🎤';
});

initNet();
startGame();

FB.content.addEventListener('contentUnload',function(){
  if(rafId){cancelAnimationFrame(rafId);rafId=null;}
  if(posIv){clearInterval(posIv);posIv=null;}
  document.removeEventListener('keydown',FB_key);
  RO.disconnect();
  bgmPause();
  if(ls){ls.getTracks().forEach(function(t){t.stop();});ls=null;}
  if(ra){ra.pause();ra.srcObject=null;ra.remove();ra=null;}
  try{if(room)room.leave();}catch(e){}
},{once:true});

})();
</script>

</body>
</html>
