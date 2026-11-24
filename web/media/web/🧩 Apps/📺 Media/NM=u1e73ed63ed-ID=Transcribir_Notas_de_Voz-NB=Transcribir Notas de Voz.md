<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.tn-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 6px}
.tn-nt{color:rgba(255,255,255,.45);font-size:.8em;max-width:440px;margin:0 auto 16px;line-height:1.5}
.tn-dz{display:block;max-width:420px;margin:0 auto 10px;padding:22px 16px;border:2px dashed rgba(255,255,255,.2);border-radius:16px;cursor:pointer;color:rgba(255,255,255,.7);transition:border-color .2s,background .2s}
.tn-dz.on{border-color:rgba(56,189,248,.6);background:rgba(56,189,248,.06)}
.tn-op{display:flex;gap:10px;justify-content:center;align-items:center;flex-wrap:wrap;margin:0 auto 14px;color:rgba(255,255,255,.7);font-size:.85em}
.tn-cd{border-radius:14px;padding:14px 16px;margin:10px auto;max-width:560px;text-align:left;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06)}
.tn-nm{font-weight:700;color:#fff;word-break:break-all}
.tn-ms{color:rgba(255,255,255,.55);font-size:.82em;margin:4px 0}
.tn-tx{color:#fff;white-space:pre-wrap;line-height:1.6;margin-top:8px;user-select:text}
.tn-ac{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}
.tn-cd .wait-anim{width:40px;height:40px}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🎙️</div>
<div class="tn-st">Transcribir Notas de Voz</div>
<div class="tn-nt">Pasa audios a texto en tu dispositivo, sin subirlos. Compartilos desde WhatsApp o elegilos aca. La primera vez se descarga el modelo (unos 250 MB), despues queda guardado.</div>
<label class="tn-dz" id="tn-dz">🎧 Toca o arrastra audios aca<input type="file" id="tn-in" accept="audio/*,video/*" multiple hidden></label>
<div class="tn-op"><button id="tn-rc">⏺️ Grabar</button><label><input type="checkbox" id="tn-ts"> Con tiempos</label></div>
<div id="tn-ls"></div>

<script>
(function(){
const $=i=>document.getElementById(i);
const WA=window.__CFG?.waitAnim||'';
const TN_SRC=`import{pipeline}from'https://cdn.jsdelivr.net/npm/@huggingface/transformers@4.3.2/+esm';
let P=null;
self.onmessage=async e=>{const{id,a,ts}=e.data;
try{P??=pipeline('automatic-speech-recognition','onnx-community/whisper-small',{dtype:'q8',device:'wasm',progress_callback:p=>{if(p.status==='progress'&&p.total)self.postMessage({id,t:'p',f:p.file,l:p.loaded,n:p.total})}});
const asr=await P;self.postMessage({id,t:'r'});
self.postMessage({id,t:'ok',o:await asr(a,{language:'spanish',task:'transcribe',chunk_length_s:30,stride_length_s:5,return_timestamps:ts})});
}catch(x){P=null;self.postMessage({id,t:'er',m:String(x&&x.message||x)})}};`;
let TN_W=null,TN_Q=Promise.resolve(),TN_N=0,TN_R=null,TN_S=null;
const TN_H={};
function TN_W1(){
  if(!TN_W){
    TN_W=new Worker(URL.createObjectURL(new Blob([TN_SRC],{type:'text/javascript'})),{type:'module'});
    TN_W.onmessage=e=>TN_H[e.data.id]?.(e.data);
  }
  return TN_W;
}
const TN_T=s=>{s=Math.max(0,Math.round(s||0));return Math.floor(s/60)+':'+String(s%60).padStart(2,'0')};
function TN_B(c,t,f){const b=document.createElement('button');b.textContent=t;b.onclick=f;c.append(b);return b}
async function TN_D(f){
  const ac=new AudioContext({sampleRate:16000});
  try{
    const b=await ac.decodeAudioData(await f.arrayBuffer());
    const a=new Float32Array(b.length);
    for(let c=0;c<b.numberOfChannels;c++){const d=b.getChannelData(c);for(let i=0;i<d.length;i++)a[i]+=d[i]/b.numberOfChannels}
    return a;
  }finally{ac.close()}
}
function TN_A1(f){
  const c=document.createElement('div');c.className='tn-cd';
  const n=document.createElement('div');n.className='tn-nm';n.textContent=f.name;
  const m=document.createElement('div');m.className='tn-ms';m.textContent='En espera...';
  const w=document.createElement('div');
  if(WA){const i=document.createElement('img');i.className='wait-anim';i.src=WA;i.alt='';w.append(i)}
  const tx=document.createElement('div');tx.className='tn-tx';
  c.append(n,m,w,tx);$('tn-ls').prepend(c);
  const ts=$('tn-ts').checked;
  TN_Q=TN_Q.then(async()=>{
    try{
      m.textContent='Leyendo audio...';
      const a=await TN_D(f);
      m.textContent=`Duracion ${TN_T(a.length/16000)} · Preparando modelo...`;
      const id=++TN_N,pr={};
      const o=await new Promise((ok,er)=>{
        TN_H[id]=d=>{
          if(d.t==='p'){pr[d.f]=[d.l,d.n];let l=0,t=0;for(const k in pr){l+=pr[k][0];t+=pr[k][1]}m.textContent=`Descargando modelo ${Math.round(l/t*100)}% (${Math.round(t/1048576)} MB, una sola vez)`}
          else if(d.t==='r')m.textContent=`Duracion ${TN_T(a.length/16000)} · Transcribiendo...`;
          else{delete TN_H[id];d.t==='ok'?ok(d.o):er(new Error(d.m))}
        };
        TN_W1().postMessage({id,a,ts},[a.buffer]);
      });
      w.remove();
      const t=ts&&o.chunks?o.chunks.map(k=>`[${TN_T(k.timestamp[0])}] ${k.text.trim()}`).join('\n'):(o.text||'').trim();
      tx.textContent=t||'(sin voz detectada)';
      m.textContent='Listo';
      const ac=document.createElement('div');ac.className='tn-ac';c.append(ac);
      TN_B(ac,'📋 Copiar',async e=>{try{await navigator.clipboard.writeText(t);e.target.textContent='✅ Copiado'}catch{}});
      if(navigator.share)TN_B(ac,'📤 Compartir',()=>navigator.share({text:t}).catch(()=>{}));
    }catch(e){w.remove();m.textContent='Error Audio '+(e&&e.message||'').slice(0,80)}
  });
}
const TN_F=fl=>{for(const f of fl)TN_A1(f)};
const dz=$('tn-dz');
$('tn-in').onchange=e=>{TN_F(e.target.files);e.target.value=''};
dz.ondragover=e=>{e.preventDefault();dz.classList.add('on')};
dz.ondragleave=()=>dz.classList.remove('on');
dz.ondrop=e=>{e.preventDefault();dz.classList.remove('on');TN_F(e.dataTransfer.files)};
const TN_X=()=>{TN_S?.getTracks().forEach(t=>t.stop());TN_S=null};
$('tn-rc').onclick=async e=>{
  const b=e.target;
  if(TN_R){TN_R.stop();return}
  try{
    TN_S=await navigator.mediaDevices.getUserMedia({audio:true});
    const ch=[];TN_R=new MediaRecorder(TN_S);
    TN_R.ondataavailable=d=>ch.push(d.data);
    TN_R.onstop=()=>{TN_X();TN_R=null;b.textContent='⏺️ Grabar';TN_A1(new File(ch,'Grabacion '+new Date().toLocaleTimeString('es-PY')+'.webm',{type:ch[0]?.type||'audio/webm'}))};
    TN_R.start();b.textContent='⏹️ Detener';
  }catch{TN_X();b.textContent='⏺️ Grabar'}
};
document.addEventListener('contentUnload',()=>{if(TN_R){TN_R.onstop=null;TN_R.stop();TN_R=null}TN_X();TN_W?.terminate();TN_W=null},{once:true});
(async()=>{
  try{
    const C={cacheName:'share-pending'},r=await caches.match('/__share_data',C);
    if(!r||Date.now()>+r.headers.get('X-Expires'))return;
    const b=(await r.json()).files.filter(x=>/^(audio|video)\//.test(x.type)||/\.(ogg|opus|oga|m4a|mp3|wav|aac|amr|webm|mp4)$/i.test(x.name||''));
    if(!b.length)return;
    const f=await Promise.all(b.map(async x=>new File([await(await caches.match(x.key,C)).blob()],x.name||'audio',{type:x.type||''})));
    await caches.delete('share-pending');
    TN_F(f);
  }catch{}
})();
})();
</script>

</div>
