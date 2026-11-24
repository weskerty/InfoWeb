<div id="GP_root">
<h2>Grabador de Pantalla</h2>

<div id="GP_cfg">
<div class="GP_row">
<label><input type="checkbox" id="GP_auSis">Audio del sistema</label>
<label><input type="checkbox" id="GP_auMic">Microfono</label>
<label><input type="checkbox" id="GP_cam">Camara (PiP)</label>
</div>
<div class="GP_row">
<select id="GP_micSel" class="GP_sel" disabled></select>
<select id="GP_camSel" class="GP_sel" disabled></select>
</div>
<div class="GP_row">
<button id="GP_btnStart">Iniciar grabacion</button>
<button id="GP_btnShot" disabled>Capturar frame</button>
<button id="GP_btnStop" disabled>Detener</button>
</div>
</div>

<div id="GP_stageWrap" class="hide">
<canvas id="GP_stage"></canvas>
<div id="GP_camBox" class="hide">
<video id="GP_camVid" autoplay muted playsinline></video>
<div id="GP_camRs"></div>
</div>
<div id="GP_badge" class="hide"><span id="GP_dot"></span><span id="GP_time">00:00</span></div>
</div>

<hr>
<h3>Captura de pantalla (foto)</h3>
<p>Elegis ventana/pantalla y un retardo antes de tomar la foto. Descarga automatica.</p>
<div class="GP_row">
<select id="GP_shotDelay" class="GP_sel">
<option value="0">Sin retardo</option>
<option value="3">3 segundos</option>
<option value="5">5 segundos</option>
<option value="10">10 segundos</option>
</select>
<button id="GP_btnShotOnly">Tomar captura</button>
</div>
<div id="GP_shotCd" class="hide"></div>

<style>
#GP_stageWrap{position:relative;width:100%;border-radius:var(--r-md);overflow:hidden;background:rgba(0,0,0,.4);margin:14px 0}
#GP_stage{width:100%;display:block}
#GP_camBox{position:absolute;width:180px;height:135px;top:12px;left:12px;border-radius:50%;overflow:hidden;border:2px solid rgba(255,255,255,.4);box-shadow:0 6px 18px rgba(0,0,0,.4);cursor:move}
#GP_camBox.GP_rect{border-radius:var(--r-sm)}
#GP_camVid{width:100%;height:100%;object-fit:cover;pointer-events:none}
#GP_camRs{position:absolute;right:2px;bottom:2px;width:14px;height:14px;cursor:nwse-resize;background:rgba(255,255,255,.5);border-radius:3px}
#GP_badge{position:absolute;top:12px;right:12px;display:flex;align-items:center;gap:6px;background:rgba(0,0,0,.55);padding:6px 12px;border-radius:20px;font-size:.85em}
#GP_dot{width:9px;height:9px;border-radius:50%;background:var(--err);animation:GP_pulse 1.2s infinite}
@keyframes GP_pulse{0%,100%{opacity:1}50%{opacity:.3}}
.GP_row{display:flex;flex-wrap:wrap;gap:10px;align-items:center;margin:10px 0}
.GP_sel{flex:1;min-width:140px}
#GP_shotCd{font-size:2.4em;text-align:center;margin:16px 0}
#GP_pipBody{font-family:var(--font);background:#111;color:#fff;height:100%;margin:0;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;padding:10px}
#GP_pipBody button{width:90%}
@media(prefers-reduced-motion:reduce){#GP_dot{animation:none}}
</style>

<script>
(function(){
if(!navigator.mediaDevices?.getDisplayMedia){document.getElementById("GP_root").innerHTML="<h2>Grabador de Pantalla</h2><blockquote>No compatible</blockquote>";return}
let vS=null,vC=null,aMic=null,aSys=null,rec=null,chunks=[],t0=0,tInt=null,wakeLock=null,pipWin=null,GP_AX=null,GP_SD=null;
const GP_AC=new AbortController();
const stg=document.getElementById("GP_stage"),ctx=stg.getContext("2d");
const camBox=document.getElementById("GP_camBox");
let camX=12,camY=12,camW=180,camH=135;
let raf=null;
if(!window.MediaRecorder||!stg.captureStream){const b=document.getElementById("GP_btnStart");b.disabled=true;b.textContent="Grabacion no compatible"}

function fmtT(s){const m=String(Math.floor(s/60)).padStart(2,"0"),r=String(s%60).padStart(2,"0");return m+":"+r}

function dl(blob,name){
const url=URL.createObjectURL(blob);
const a=document.createElement("a");a.href=url;a.download=name;
document.body.appendChild(a);a.click();a.remove();
setTimeout(()=>URL.revokeObjectURL(url),4000)
}

async function listDevices(){
const ds=await navigator.mediaDevices.enumerateDevices();
const micSel=document.getElementById("GP_micSel"),camSel=document.getElementById("GP_camSel");
micSel.innerHTML="";camSel.innerHTML="";
ds.forEach(d=>{
if(d.kind==="audioinput"){const o=document.createElement("option");o.value=d.deviceId;o.textContent=d.label||"Microfono";micSel.appendChild(o)}
if(d.kind==="videoinput"){const o=document.createElement("option");o.value=d.deviceId;o.textContent=d.label||"Camara";camSel.appendChild(o)}
})
}
navigator.mediaDevices.addEventListener("devicechange",listDevices,{signal:GP_AC.signal});

document.getElementById("GP_auMic").addEventListener("change",e=>{document.getElementById("GP_micSel").disabled=!e.target.checked});
document.getElementById("GP_cam").addEventListener("change",e=>{document.getElementById("GP_camSel").disabled=!e.target.checked});

function mixAudio(sysStream,micStream){
const tracks=[];
if(sysStream)tracks.push(...sysStream.getAudioTracks());
if(micStream)tracks.push(...micStream.getAudioTracks());
if(!tracks.length)return null;
if(tracks.length===1)return new MediaStream([tracks[0]]);
const ac=GP_AX=new AudioContext(),dst=ac.createMediaStreamDestination();
tracks.forEach(tr=>{const src=ac.createMediaStreamSource(new MediaStream([tr]));src.connect(dst)});
return dst.stream
}

function resizeStage(){
const w=vS.videoWidth||1280,h=vS.videoHeight||720;
stg.width=w;stg.height=h
}

function loop(){
ctx.drawImage(vS,0,0,stg.width,stg.height);
if(!camBox.classList.contains("hide")&&vC&&vC.readyState>=2){
const sx=stg.width/camBox.parentElement.clientWidth,sy=stg.height/camBox.parentElement.clientHeight;
const cx=camX*sx,cy=camY*sy,cw=camW*sx,ch=camH*sy;
ctx.save();
ctx.beginPath();
if(camBox.classList.contains("GP_rect"))ctx.rect(cx,cy,cw,ch);
else ctx.ellipse(cx+cw/2,cy+ch/2,cw/2,ch/2,0,0,Math.PI*2);
ctx.closePath();ctx.clip();
ctx.drawImage(vC,cx,cy,cw,ch);
ctx.restore()
}
raf=requestAnimationFrame(loop)
}

function pickMime(){
const opts=["video/webm;codecs=vp9,opus","video/webm;codecs=vp8,opus","video/webm"];
return opts.find(t=>MediaRecorder.isTypeSupported(t))||""
}

function shotFrame(){
stg.toBlob(b=>dl(b,"captura_"+Date.now()+".png"),"image/png")
}

async function openPip(){
if(!window.documentPictureInPicture){return}
try{
pipWin=await window.documentPictureInPicture.requestWindow({width:220,height:140});
const body=pipWin.document.createElement("div");
body.id="GP_pipBody";
const bShot=pipWin.document.createElement("button");bShot.textContent="Capturar frame";
const bStop=pipWin.document.createElement("button");bStop.textContent="Detener";
bShot.addEventListener("click",shotFrame);
bStop.addEventListener("click",()=>document.getElementById("GP_btnStop").click());
body.appendChild(bShot);body.appendChild(bStop);
pipWin.document.body.appendChild(body);
Array.from(document.styleSheets).forEach(ss=>{
try{const l=pipWin.document.createElement("style");l.textContent=Array.from(ss.cssRules).map(r=>r.cssText).join("");pipWin.document.head.appendChild(l)}catch(e){}
});
pipWin.addEventListener("pagehide",()=>{pipWin=null})
}catch(err){pipWin=null}
}

document.getElementById("GP_btnStart").addEventListener("click",async()=>{
try{
const wantSys=document.getElementById("GP_auSis").checked;
const disp=await navigator.mediaDevices.getDisplayMedia({video:{frameRate:30},audio:wantSys});
vS=document.createElement("video");vS.srcObject=disp;vS.muted=true;await vS.play();
resizeStage();
if(wantSys)aSys=new MediaStream(disp.getAudioTracks());
if(document.getElementById("GP_auMic").checked){
const mid=document.getElementById("GP_micSel").value;
aMic=await navigator.mediaDevices.getUserMedia({audio:mid?{deviceId:mid}:true})
}
if(document.getElementById("GP_cam").checked){
const cid=document.getElementById("GP_camSel").value;
const cs=await navigator.mediaDevices.getUserMedia({video:cid?{deviceId:cid}:true});
vC=document.createElement("video");vC.srcObject=cs;vC.muted=true;await vC.play();
camBox.classList.remove("hide")
}
await listDevices();
document.getElementById("GP_stageWrap").classList.remove("hide");
document.getElementById("GP_btnShot").disabled=false;
document.getElementById("GP_btnStart").disabled=true;
disp.getVideoTracks()[0].addEventListener("ended",()=>{document.getElementById("GP_btnStop").click()});
loop();
try{wakeLock=await navigator.wakeLock.request("screen")}catch(e){}
const vStream=stg.captureStream(30);
const mixedS=mixAudio(aSys,aMic);
const finalStream=new MediaStream([...vStream.getVideoTracks(),...(mixedS?mixedS.getAudioTracks():[])]);
const mt=pickMime();
rec=new MediaRecorder(finalStream,mt?{mimeType:mt}:{});
chunks=[];
rec.ondataavailable=e=>{if(e.data.size)chunks.push(e.data)};
rec.onstop=()=>{dl(new Blob(chunks,{type:mt||"video/webm"}),"grabacion_"+Date.now()+".webm")};
rec.start();
t0=Date.now();
document.getElementById("GP_badge").classList.remove("hide");
tInt=setInterval(()=>{document.getElementById("GP_time").textContent=fmtT(Math.floor((Date.now()-t0)/1000))},500);
document.getElementById("GP_btnStop").disabled=false;
openPip()
}catch(err){console.error(err)}
});

document.getElementById("GP_btnShot").addEventListener("click",shotFrame);

document.getElementById("GP_btnStop").addEventListener("click",()=>{
if(rec&&rec.state!=="inactive")rec.stop();
if(raf)cancelAnimationFrame(raf);
clearInterval(tInt);
if(wakeLock){wakeLock.release();wakeLock=null}
if(pipWin){pipWin.close();pipWin=null}
document.getElementById("GP_badge").classList.add("hide");
if(vS&&vS.srcObject)vS.srcObject.getTracks().forEach(t=>t.stop());
if(vC&&vC.srcObject)vC.srcObject.getTracks().forEach(t=>t.stop());
if(aMic)aMic.getTracks().forEach(t=>t.stop());
if(GP_AX){GP_AX.close();GP_AX=null}
document.getElementById("GP_stageWrap").classList.add("hide");
camBox.classList.add("hide");
document.getElementById("GP_btnStart").disabled=false;
document.getElementById("GP_btnShot").disabled=true;
document.getElementById("GP_btnStop").disabled=true
});

let dragging=false,resizing=false,dragOX=0,dragOY=0;
camBox.addEventListener("mousedown",e=>{
if(e.target.id==="GP_camRs"){resizing=true;return}
dragging=true;dragOX=e.clientX-camX;dragOY=e.clientY-camY
});
window.addEventListener("mousemove",e=>{
if(dragging){camX=e.clientX-dragOX;camY=e.clientY-dragOY;camBox.style.left=camX+"px";camBox.style.top=camY+"px"}
if(resizing){camW=Math.max(80,e.clientX-camX);camH=Math.max(60,e.clientY-camY);camBox.style.width=camW+"px";camBox.style.height=camH+"px"}
},{signal:GP_AC.signal});
window.addEventListener("mouseup",()=>{dragging=false;resizing=false},{signal:GP_AC.signal});
camBox.addEventListener("dblclick",()=>camBox.classList.toggle("GP_rect"));

document.getElementById("GP_btnShotOnly").addEventListener("click",async()=>{
try{
const delay=+document.getElementById("GP_shotDelay").value;
const disp=GP_SD=await navigator.mediaDevices.getDisplayMedia({video:{frameRate:5}});
const v=document.createElement("video");v.srcObject=disp;v.muted=true;await v.play();
const cd=document.getElementById("GP_shotCd");
if(delay>0){
cd.classList.remove("hide");
for(let n=delay;n>0;n--){cd.textContent=n;await new Promise(r=>setTimeout(r,1000))}
cd.classList.add("hide")
}
const c=document.createElement("canvas");c.width=v.videoWidth;c.height=v.videoHeight;
c.getContext("2d").drawImage(v,0,0,c.width,c.height);
disp.getTracks().forEach(t=>t.stop());
c.toBlob(b=>dl(b,"captura_"+Date.now()+".png"),"image/png")
}catch(err){console.error(err)}
});

document.addEventListener("contentUnload",()=>{GP_AC.abort();document.getElementById("GP_btnStop").click();GP_SD?.getTracks().forEach(t=>t.stop())},{once:true});
listDevices();
})();
</script>
</div>