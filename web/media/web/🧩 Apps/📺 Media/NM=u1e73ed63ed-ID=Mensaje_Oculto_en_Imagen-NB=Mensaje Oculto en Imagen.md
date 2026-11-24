<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.mo-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 6px}
.mo-nt{color:rgba(255,255,255,.45);font-size:.8em;max-width:460px;margin:0 auto 14px;line-height:1.5}
.mo-tb{display:flex;gap:10px;justify-content:center;margin:0 auto 12px}
.mo-bx{border-radius:14px;padding:12px 14px;margin:10px auto;max-width:560px;text-align:left;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06)}
.mo-h{font-size:.72em;letter-spacing:.08em;color:rgba(255,255,255,.45);margin:10px 0 6px;text-transform:uppercase}
.mo-h:first-child{margin-top:0}
.mo-bx textarea,.mo-bx input[type=password]{width:100%;box-sizing:border-box;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);border-radius:10px;color:#fff;padding:8px 10px;font-family:inherit;font-size:.9em}
.mo-bx textarea{min-height:70px;resize:vertical}
.mo-md{display:grid;gap:6px}
.mo-md label{display:flex;gap:8px;align-items:flex-start;padding:8px 10px;border-radius:10px;background:rgba(255,255,255,.05);cursor:pointer;color:#fff;font-size:.88em}
.mo-md small{display:block;color:rgba(255,255,255,.5)}
.mo-dz{display:block;padding:14px;border:2px dashed rgba(255,255,255,.2);border-radius:12px;cursor:pointer;color:rgba(255,255,255,.7);text-align:center;font-size:.88em;word-break:break-all}
.mo-dz.on{border-color:rgba(56,189,248,.6)}
.mo-go{text-align:center;margin-top:12px}
.mo-out{margin-top:10px;color:#fff;font-size:.9em}
.mo-out:empty{display:none}
.mo-res{white-space:pre-wrap;word-break:break-word;background:rgba(0,0,0,.25);border-radius:10px;padding:10px;margin:6px 0;user-select:text}
.mo-er{color:var(--warn)}
.mo-ok{color:var(--ok)}
.mo-ac{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
.mo-out .wait-anim{width:36px;height:36px}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🕵️</div>
<div class="mo-st">Mensaje Oculto</div>
<div class="mo-nt">Esconde un mensaje o un archivo dentro de un texto, una foto o un video que se ven normales. Con contrasena queda cifrado (AES-256). Todo pasa en tu dispositivo.</div>
<div class="mo-tb"><button id="mo-t1" aria-pressed="true">🙈 Ocultar</button><button id="mo-t2" aria-pressed="false">👀 Revelar</button></div>

<div class="mo-bx" id="mo-oc">
  <div class="mo-h">Donde esconderlo</div>
  <div class="mo-md">
    <label><input type="radio" name="mo-md" value="t" checked><span>💬 Texto invisible<small>Dentro de una frase normal. Sobrevive a WhatsApp. Para mensajes cortos.</small></span></label>
    <label><input type="radio" name="mo-md" value="i"><span>🖼️ Foto (PNG)<small>Entra mucho, incluso un archivo. Mandala como documento, no como foto.</small></span></label>
    <label><input type="radio" name="mo-md" value="r"><span>🛡️ Foto resistente (experimental)<small>Aguanta que WhatsApp la comprima. Solo texto corto.</small></span></label>
    <label><input type="radio" name="mo-md" value="f"><span>🎬 Video o cualquier archivo<small>Se sigue viendo normal. Mandalo como documento.</small></span></label>
  </div>
  <div id="mo-cvw"><div class="mo-h">Texto visible</div><textarea id="mo-cv" placeholder="Ej: Nos vemos manana, saludos!"></textarea></div>
  <div id="mo-pfw" hidden><div class="mo-h">Foto o archivo portador</div><label class="mo-dz" id="mo-pd">📂 Toca o arrastra aca<input type="file" id="mo-pf" hidden></label></div>
  <div class="mo-h">Mensaje secreto</div>
  <textarea id="mo-ms" placeholder="Lo que nadie tiene que ver"></textarea>
  <div id="mo-sfw" hidden><label class="mo-dz" id="mo-sd" style="margin-top:6px">📎 o un archivo secreto<input type="file" id="mo-sf" hidden></label></div>
  <div class="mo-h">Contrasena (opcional)</div>
  <input type="password" id="mo-pw" autocomplete="new-password" placeholder="Sin contrasena cualquiera con esta app lo lee">
  <div class="mo-go"><button id="mo-go">🙈 Ocultar</button></div>
  <div class="mo-out" id="mo-or"></div>
</div>

<div class="mo-bx" id="mo-rv" hidden>
  <div class="mo-h">Texto recibido</div>
  <textarea id="mo-rt" placeholder="Pega aca el texto"></textarea>
  <label class="mo-dz" id="mo-rd" style="margin-top:8px">📂 o toca o arrastra la foto, video o archivo<input type="file" id="mo-rf" hidden></label>
  <div class="mo-h">Contrasena (si tiene)</div>
  <input type="password" id="mo-rp" autocomplete="off" placeholder="Contrasena">
  <div class="mo-go"><button id="mo-rg">👀 Revelar</button></div>
  <div class="mo-out" id="mo-rr"></div>
</div>

<script>
(function(){
const $=i=>document.getElementById(i);
const WA=window.__CFG?.waitAnim||'',TE=new TextEncoder(),TD=new TextDecoder();
const MO_MG=TE.encode('CHAGANA1'),MO_SL=96,MO_DL=24,MO_MX=1280;
let MO_PF=null,MO_SF=null,MO_RF=null,MO_U=[];
const MO_CAT=(...a)=>{const r=new Uint8Array(a.reduce((n,x)=>n+x.length,0));let o=0;for(const x of a){r.set(x,o);o+=x.length}return r};
const MO_EL=(t,c,x)=>{const e=document.createElement(t);if(c)e.className=c;if(x!=null)e.textContent=x;return e};
const MO_LIB=()=>import('/web/js/lib/Steganography/src/text.js');
async function MO_Z(b,d){return new Uint8Array(await new Response(new Blob([b]).stream().pipeThrough(new(d?DecompressionStream:CompressionStream)('deflate-raw'))).arrayBuffer())}
async function MO_K(p,s){const k=await crypto.subtle.importKey('raw',TE.encode(p),'PBKDF2',false,['deriveKey']);return crypto.subtle.deriveKey({name:'PBKDF2',salt:s,iterations:200000,hash:'SHA-256'},k,{name:'AES-GCM',length:256},false,['encrypt','decrypt'])}
async function MO_PK(t,f,pw){
  let p;
  if(f){const n=TE.encode(f.name).slice(0,200);p=MO_CAT([1,n.length],n,new Uint8Array(await f.arrayBuffer()))}else p=MO_CAT([0],TE.encode(t));
  let fl=0;const z=await MO_Z(p);if(z.length<p.length){p=z;fl|=2}
  if(pw){const s=crypto.getRandomValues(new Uint8Array(16)),iv=crypto.getRandomValues(new Uint8Array(12));p=MO_CAT(s,iv,new Uint8Array(await crypto.subtle.encrypt({name:'AES-GCM',iv},await MO_K(pw,s),p)));fl|=1}
  return MO_CAT([fl],p);
}
async function MO_UP(e,pw){
  const fl=e[0];let p=e.slice(1);
  if(fl&1){if(!pw)throw new Error('PW');try{p=new Uint8Array(await crypto.subtle.decrypt({name:'AES-GCM',iv:p.slice(16,28)},await MO_K(pw,p.slice(0,16)),p.slice(28)))}catch{throw new Error('MAL')}}
  if(fl&2)p=await MO_Z(p,1);
  if(p[0]===1){const n=p[1];return{f:new File([p.slice(2+n)],TD.decode(p.slice(2,2+n))||'archivo')}}
  return{t:TD.decode(p.slice(1))};
}
async function MO_IMG(f,mx){
  const b=await createImageBitmap(f,{premultiplyAlpha:'none',colorSpaceConversion:'none'});
  const k=mx?Math.min(1,mx/Math.max(b.width,b.height)):1,c=document.createElement('canvas');
  c.width=Math.round(b.width*k);c.height=Math.round(b.height*k);
  const x=c.getContext('2d',{willReadFrequently:true});if(mx){x.fillStyle='#fff';x.fillRect(0,0,c.width,c.height)}
  x.drawImage(b,0,0,c.width,c.height);b.close();
  return{c,x,d:x.getImageData(0,0,c.width,c.height)};
}
const MO_BL=(c,t,q)=>new Promise(r=>c.toBlob(r,t,q));
function MO_LI(d){const a=d.data,ix=[];for(let i=0;i<a.length;i+=4)if(a[i+3]===255)ix.push(i,i+1,i+2);return ix}
async function MO_HI(f,e){
  const{c,x,d}=await MO_IMG(f),ix=MO_LI(d),h=new Uint8Array(6);h.set(TE.encode('CA'));new DataView(h.buffer).setUint32(2,e.length);
  const b=MO_CAT(h,e);if(b.length*8>ix.length)throw new Error('CAP:'+Math.floor(ix.length/8-6));
  for(let i=0;i<b.length*8;i++){const k=ix[i];d.data[k]=d.data[k]&254|(b[i>>3]>>(7-(i&7))&1)}
  x.putImageData(d,0,0);return MO_BL(c,'image/png');
}
async function MO_HR(f){
  const{d}=await MO_IMG(f),ix=MO_LI(d),rd=(o,n)=>{const r=new Uint8Array(n);for(let i=0;i<n*8;i++)r[i>>3]|=(d.data[ix[o*8+i]]&1)<<(7-(i&7));return r};
  if(ix.length<48)return null;const h=rd(0,6);if(h[0]!==67||h[1]!==65)return null;
  const n=new DataView(h.buffer).getUint32(2);if(!n||(n+6)*8>ix.length)return null;return rd(6,n);
}
const MO_B=(()=>{const B=new Float32Array(64);for(let y=0;y<8;y++)for(let x=0;x<8;x++)B[y*8+x]=.25*Math.cos((2*x+1)*Math.PI/16)*Math.cos((2*y+1)*2*Math.PI/16);return B})();
function MO_PM(n){let s=0xC4A6A1;const r=()=>{s=s+0x6D2B79F5|0;let t=Math.imul(s^s>>>15,1|s);t=t+Math.imul(t^t>>>7,61|t)^t;return((t^t>>>14)>>>0)/4294967296},p=Array.from({length:n},(_,i)=>i);for(let i=n-1;i>0;i--){const j=Math.floor(r()*(i+1));[p[i],p[j]]=[p[j],p[i]]}return p}
function MO_RB(d){const w=d.width,bw=w>>3,bh=d.height>>3,N=bw*bh,F=(MO_SL+3)*8,R=Math.floor(N/F);return{w,bw,N,F,R,P:MO_PM(N)}}
function MO_CF(d,w,bx,by){let c=0;for(let y=0;y<8;y++)for(let x=0;x<8;x++){const i=((by*8+y)*w+bx*8+x)*4,a=d.data;c+=(.299*a[i]+.587*a[i+1]+.114*a[i+2])*MO_B[y*8+x]}return c}
async function MO_RH(f,e){
  if(e.length>MO_SL)throw new Error('LARGO');
  const{c,x,d}=await MO_IMG(f,MO_MX),G=MO_RB(d);if(G.R<5)throw new Error('CHICA');
  const fr=new Uint8Array(MO_SL+3);fr[0]=e.length;fr.set(e,1);let ck=0;for(let i=0;i<=MO_SL;i++)ck=(ck*31+fr[i])&65535;fr[MO_SL+1]=ck>>8;fr[MO_SL+2]=ck&255;
  for(let r=0;r<G.R;r++)for(let k=0;k<G.F;k++){
    const bl=G.P[r*G.F+k],bx=bl%G.bw,by=Math.floor(bl/G.bw),bit=fr[k>>3]>>(7-(k&7))&1,q=bit?MO_DL/2:0;
    const cf=MO_CF(d,G.w,bx,by),dl=MO_DL*Math.round((cf-q)/MO_DL)+q-cf;
    for(let y=0;y<8;y++)for(let xx=0;xx<8;xx++){const i=((by*8+y)*G.w+bx*8+xx)*4,v=dl*MO_B[y*8+xx];for(let ch=0;ch<3;ch++)d.data[i+ch]=Math.max(0,Math.min(255,Math.round(d.data[i+ch]+v)))}
  }
  x.putImageData(d,0,0);return MO_BL(c,'image/jpeg',.92);
}
async function MO_RR(f){
  const{d}=await MO_IMG(f),G=MO_RB(d);if(G.R<5)return null;
  const s=new Float32Array(G.F);
  for(let r=0;r<G.R;r++)for(let k=0;k<G.F;k++){const bl=G.P[r*G.F+k],cf=MO_CF(d,G.w,bl%G.bw,Math.floor(bl/G.bw)),d0=Math.abs(cf-MO_DL*Math.round(cf/MO_DL)),c1=cf-MO_DL/2,d1=Math.abs(c1-MO_DL*Math.round(c1/MO_DL));s[k]+=d0-d1}
  const fr=new Uint8Array(MO_SL+3);for(let k=0;k<G.F;k++)if(s[k]>0)fr[k>>3]|=1<<(7-(k&7));
  let ck=0;for(let i=0;i<=MO_SL;i++)ck=(ck*31+fr[i])&65535;
  if(fr[MO_SL+1]!==ck>>8||fr[MO_SL+2]!==(ck&255)||!fr[0])return null;return fr.slice(1,1+fr[0]);
}
async function MO_FR(f){
  if(f.size<12)return null;const t=new Uint8Array(await f.slice(-12).arrayBuffer());
  if(!MO_MG.every((v,i)=>t[4+i]===v))return null;const n=new DataView(t.buffer).getUint32(0);
  if(n+12>f.size)return null;return new Uint8Array(await f.slice(-12-n,-12).arrayBuffer());
}
function MO_W(o,t){o.textContent='';if(WA){const i=MO_EL('img','wait-anim');i.src=WA;i.alt='';o.append(i,' ')}o.append(t)}
function MO_DLK(o,b,n,lbl){
  const u=URL.createObjectURL(b);MO_U.push(u);const ac=MO_EL('div','mo-ac'),a=MO_EL('a','view-all-button',lbl);a.href=u;a.download=n;ac.append(a);
  const fi=new File([b],n,{type:b.type});if(navigator.canShare?.({files:[fi]})){const s=MO_EL('button',0,'📤 Compartir');s.onclick=()=>navigator.share({files:[fi]}).catch(()=>{});ac.append(s)}
  o.append(ac);
}
const MO_MD=()=>document.querySelector('input[name=mo-md]:checked').value;
function MO_SM(){const m=MO_MD();$('mo-cvw').hidden=m!=='t';$('mo-pfw').hidden=m==='t';$('mo-sfw').hidden=m==='t'||m==='r';$('mo-pf').accept=m==='f'?'':'image/*'}
document.querySelectorAll('input[name=mo-md]').forEach(r=>r.onchange=MO_SM);
const MO_TAB=v=>{$('mo-oc').hidden=v;$('mo-rv').hidden=!v;$('mo-t1').setAttribute('aria-pressed',!v);$('mo-t2').setAttribute('aria-pressed',!!v)};
$('mo-t1').onclick=()=>MO_TAB(0);$('mo-t2').onclick=()=>MO_TAB(1);
function MO_DZ(z,i,set){const p=$(z),lb=p.firstChild.textContent;const s=f=>{set(f);p.firstChild.textContent=f?'✅ '+f.name:lb};$(i).onchange=e=>{s(e.target.files[0]||null)};p.ondragover=e=>{e.preventDefault();p.classList.add('on')};p.ondragleave=()=>p.classList.remove('on');p.ondrop=e=>{e.preventDefault();p.classList.remove('on');s(e.dataTransfer.files[0]||null)};return s}
const MO_SP=MO_DZ('mo-pd','mo-pf',f=>MO_PF=f),MO_SS=MO_DZ('mo-sd','mo-sf',f=>MO_SF=f),MO_SR=MO_DZ('mo-rd','mo-rf',f=>{MO_RF=f;if(f)$('mo-rt').value=''});
const MO_ERR={CHICA:'La foto es muy chica para este modo',LARGO:'Mensaje muy largo para la foto resistente (maximo unas 90 letras, o 50 con contrasena)'};
$('mo-go').onclick=async()=>{
  const o=$('mo-or'),m=MO_MD(),t=$('mo-ms').value,pw=$('mo-pw').value,sf=m==='i'||m==='f'?MO_SF:null;
  if(!t&&!sf){o.textContent='Escribi el mensaje secreto';return}
  if(m==='t'&&!$('mo-cv').value.trim()){o.textContent='Escribi el texto visible';return}
  if(m!=='t'&&!MO_PF){o.textContent='Elegi la foto o archivo portador';return}
  MO_W(o,'Ocultando...');
  try{
    const e=await MO_PK(t,sf,pw),bn=m!=='t'&&MO_PF.name.replace(/\.[^.]+$/,'');
    o.textContent='';
    if(m==='t'){
      const r=await(await MO_LIB()).encodeBinary($('mo-cv').value,e,undefined,true,{maxPayloadBytes:60000,maxSecretLength:60000});
      o.append(MO_EL('div','mo-ok','✅ Listo. Se ve igual, pero lleva el mensaje adentro:'),MO_EL('div','mo-res',r));
      const ac=MO_EL('div','mo-ac'),cp=MO_EL('button',0,'📋 Copiar');cp.onclick=async()=>{try{await navigator.clipboard.writeText(r);cp.textContent='✅ Copiado'}catch{}};ac.append(cp);
      if(navigator.share){const s=MO_EL('button',0,'📤 Compartir');s.onclick=()=>navigator.share({text:r}).catch(()=>{});ac.append(s)}o.append(ac);
    }else if(m==='i'){MO_DLK(o,await MO_HI(MO_PF,e),bn+'.png','⬇️ Descargar PNG');o.append(MO_EL('div',0,'Mandala como documento: si va como foto, WhatsApp la comprime y el mensaje se pierde.'))}
    else if(m==='r'){MO_DLK(o,await MO_RH(MO_PF,e),bn+'.jpg','⬇️ Descargar JPG');o.append(MO_EL('div',0,'Se puede mandar como foto normal. Experimental: proba primero si llega bien.'))}
    else{const n=new Uint8Array(4);new DataView(n.buffer).setUint32(0,e.length);MO_DLK(o,new Blob([MO_PF,e,n,MO_MG],{type:MO_PF.type||'application/octet-stream'}),MO_PF.name,'⬇️ Descargar archivo');o.append(MO_EL('div',0,'Mandalo como documento para que no lo recompriman.'))}
  }catch(x){const k=(x?.message||'').split(':');o.textContent='';o.append(MO_EL('div','mo-er',k[0]==='CAP'?`No entra: esta foto aguanta unos ${Math.round(k[1]/1024)} KB. Usa una foto mas grande o el modo video/archivo.`:MO_ERR[k[0]]||'Error Ocultar'))}
};
async function MO_RV(){
  const o=$('mo-rr'),t=$('mo-rt').value,f=MO_RF,pw=$('mo-rp').value;
  if(!t&&!f){o.textContent='Pega un texto o elegi un archivo';return null}
  MO_W(o,'Buscando...');
  let e=null,how='';
  try{
    if(t){if(/[​‌‍﻿⁠⁡]/.test(t)){const r=await(await MO_LIB()).decodeBinary(t);e=r.binaryData;how='texto invisible'}}
    else{
      e=await MO_FR(f);how='archivo';
      if(!e&&/^image\//.test(f.type)||!e&&/\.(png|jpe?g|webp|bmp|gif)$/i.test(f.name)){e=await MO_HR(f).catch(()=>null);how='foto'}
      if(!e&&(/^image\//.test(f.type)||/\.(jpe?g|png|webp)$/i.test(f.name))){e=await MO_RR(f).catch(()=>null);how='foto resistente'}
    }
    o.textContent='';
    if(!e||!e.length){o.append(MO_EL('div','mo-er','No se encontro ningun mensaje oculto'));return false}
    const r=await MO_UP(e,pw);
    o.append(MO_EL('div','mo-ok','✅ Mensaje encontrado ('+how+')'));
    if(r.f)MO_DLK(o,r.f,r.f.name,'⬇️ Descargar '+r.f.name);else o.append(MO_EL('div','mo-res',r.t));
    return true;
  }catch(x){o.textContent='';o.append(MO_EL('div','mo-er',x?.message==='PW'?'🔒 Tiene contrasena: escribila y toca Revelar':x?.message==='MAL'?'🔒 Contrasena incorrecta':'Error Revelar'));return true}
}
$('mo-rg').onclick=MO_RV;
$('mo-rt').oninput=()=>{if(MO_RF)MO_SR(null)};
$('mo-ms').oninput=()=>{if(MO_SF)MO_SS(null)};
MO_SM();
document.addEventListener('contentUnload',()=>{MO_U.forEach(u=>URL.revokeObjectURL(u));MO_U=[]},{once:true});
(async()=>{
  try{
    const C={cacheName:'share-pending'},r=await caches.match('/__share_data',C);
    if(!r||Date.now()>+r.headers.get('X-Expires'))return;
    const d=await r.json(),b=d.files[0],tx=[d.text,d.url].filter(Boolean).join(' ');
    if(b){
      const f=new File([await(await caches.match(b.key,C)).blob()],b.name||'archivo',{type:b.type||''});
      await caches.delete('share-pending');
      MO_TAB(1);MO_SR(f);
      if(await MO_RV()===false){
        const o=$('mo-rr'),u=MO_EL('button',0,'🙈 Usarlo para ocultar un mensaje');
        u.onclick=()=>{document.querySelector(`input[name=mo-md][value=${/^image\//.test(f.type)?'i':'f'}]`).checked=true;MO_SM();MO_SP(f);MO_TAB(0)};o.append(u);
      }
    }else if(/[​‌‍﻿⁠⁡]/.test(tx)){await caches.delete('share-pending');MO_TAB(1);$('mo-rt').value=tx;MO_RV()}
  }catch{}
})();
})();
</script>

</div>
