<style>
*{box-sizing:border-box}
.mc-wrap{display:flex;flex-direction:column;gap:10px;margin:14px 0}
.mc-card{
  background:rgba(255,255,255,.04);
  border:1px solid rgba(255,255,255,.09);
  border-radius:16px;overflow:hidden;
  transition:border-color .2s;
}
.mc-card:hover{border-color:rgba(255,255,255,.18)}
.mc-head{padding:15px 18px 10px;display:flex;gap:12px;align-items:flex-start}
.mc-hinfo{flex:1;min-width:0}
.mc-thumb{width:48px;height:48px;border-radius:10px;object-fit:cover;flex-shrink:0}
.mc-name{font-size:1.05em;font-weight:700;color:#fff;margin:0 0 4px}
.mc-desc{font-size:.85em;color:rgba(255,255,255,.5);margin:0 0 10px;line-height:1.45}
.MC_R1{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:12px}
.MC_B1{
  display:flex;align-items:center;gap:8px;
  padding:10px 14px;border-radius:12px;
  font-family:monospace,monospace;color:rgba(255,255,255,.75);
  background:rgba(255,255,255,.05);
  border:1px solid rgba(255,255,255,.09);
  cursor:pointer;user-select:none;
  transition:background .18s,border-color .18s,transform .15s;
}
.MC_B1:hover{background:rgba(255,255,255,.1);border-color:rgba(255,255,255,.18)}
.MC_B1:active{transform:scale(.97)}
.MC_T1{word-break:break-all}
.mc-acts{display:flex;gap:6px;flex-wrap:wrap}
.mc-bbtn{
  display:inline-flex;align-items:center;gap:6px;
  padding:7px 13px;border-radius:12px;font-size:.8em;font-weight:600;
  text-decoration:none;cursor:pointer;
  border:1px solid rgba(98,210,88,.3);
  background:rgba(98,210,88,.08);color:#7ee87a;
  transition:background .18s,transform .15s;
}
.mc-bbtn:hover{background:rgba(98,210,88,.16);transform:translateY(-1px)}
.mc-bbtn img{width:16px;height:16px;object-fit:contain;flex-shrink:0}

.mc-java{
  padding:10px 18px 14px;
  border-top:1px solid rgba(255,255,255,.06);
  font-size:.8em;color:rgba(255,255,255,.45);
  line-height:1.6;
}
.mc-java code{
  background:rgba(255,255,255,.07);padding:2px 6px;
  border-radius:6px;color:rgba(255,255,255,.75);font-size:.95em;
}

.lk{
  display:inline-flex;align-items:center;gap:6px;
  padding:5px 11px;border-radius:20px;
  font-size:.78em;font-weight:600;
  text-decoration:none;
  border:1px solid rgba(255,255,255,.12);
  background:rgba(255,255,255,.06);color:#fff;
  transition:background .18s,transform .15s;
}
.lk:hover{background:rgba(255,255,255,.13);transform:translateY(-1px)}
.lk::before{
  content:'';display:inline-block;
  width:14px;height:14px;flex-shrink:0;
  background-color:currentColor;
  -webkit-mask-size:contain;mask-size:contain;
  -webkit-mask-repeat:no-repeat;mask-repeat:no-repeat;
  -webkit-mask-position:center;mask-position:center;
}
.lk-wa{border-color:rgba(37,211,102,.3);color:#4edc7e}
.lk-wa:hover{background:rgba(37,211,102,.12)}
.lk-wa::before{-webkit-mask-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.149-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347zM12 0C5.373 0 0 5.373 0 12c0 2.126.555 4.122 1.528 5.855L0 24l6.335-1.505A11.94 11.94 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-1.89 0-3.66-.498-5.194-1.37l-.372-.22-3.862.918.975-3.768-.242-.387A9.96 9.96 0 0 1 2 12C2 6.477 6.477 2 12 2s10 4.477 10 10-4.477 10-10 10z'/%3E%3C/svg%3E");mask-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.149-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347zM12 0C5.373 0 0 5.373 0 12c0 2.126.555 4.122 1.528 5.855L0 24l6.335-1.505A11.94 11.94 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-1.89 0-3.66-.498-5.194-1.37l-.372-.22-3.862.918.975-3.768-.242-.387A9.96 9.96 0 0 1 2 12C2 6.477 6.477 2 12 2s10 4.477 10 10-4.477 10-10 10z'/%3E%3C/svg%3E")}
.lk-tg{border-color:rgba(44,165,224,.3);color:#5ec8f0}
.lk-tg:hover{background:rgba(44,165,224,.12)}
.lk-tg::before{-webkit-mask-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z'/%3E%3C/svg%3E");mask-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z'/%3E%3C/svg%3E")}
.lk-dc{border-color:rgba(88,101,242,.3);color:#9da8ff}
.lk-dc:hover{background:rgba(88,101,242,.12)}
.lk-dc::before{-webkit-mask-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028c.462-.63.874-1.295 1.226-1.994a.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z'/%3E%3C/svg%3E");mask-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028c.462-.63.874-1.295 1.226-1.994a.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z'/%3E%3C/svg%3E")}

.mc-skin{
  margin-top:16px;padding:14px 16px;
  border-radius:14px;
  background:rgba(255,255,255,.03);
  border:1px solid rgba(255,255,255,.07);
  font-size:.83em;color:rgba(255,255,255,.5);line-height:1.6;
}
.mc-skin a{color:#9fd3ff;text-decoration:none}
.mc-skin a:hover{text-decoration:underline}
</style>

<h1 style="margin:0 0 6px;font-size:1.4em;font-weight:700;color:#fff">⛏️ Servidores Minecraft Paraguay</h1>
<p style="margin:0 0 14px;font-size:.88em;color:rgba(255,255,255,.45)">Copia la IP y Unete a los Mundos.</p>

<div id="mc-wrap" class="mc-wrap">
  <div style="height:80px;border-radius:16px;background:linear-gradient(90deg,rgba(255,255,255,.04) 25%,rgba(255,255,255,.08) 50%,rgba(255,255,255,.04) 75%);background-size:200%;animation:mc-sk 1.4s infinite"></div>
</div>

<div class="mc-skin">
  Para ver Skins desactiva <strong style="color:rgba(255,255,255,.7)">"Permitir solo Aspectos seguros"</strong> en Config General.
  Descargar skins: <a href="https://es.namemc.com/minecraft-skins/random" target="_blank" rel="noopener noreferrer">namemc.com ↗️</a>
</div>


<style>
@keyframes mc-sk{0%{background-position:200%}100%{background-position:-200%}}
</style>

<script>
(function(){
const WRAP=document.getElementById('mc-wrap');
const JSON_URL='web/Publico/minecraft/data.json';
const ICON_B='web/adjuntos/Server_Minecraft/iconbedrock.avif';

function esc(s){const d=document.createElement('div');d.textContent=s==null?'':String(s);return d.innerHTML;}
function parseEntry(relPath){
  const fn=relPath.split('/').pop();
  const mNB=fn.match(/NB=(.+)\.\w+$/);
  if(!mNB)return null;
  const parts=mNB[1].split(';');
  const name=parts[0],desc=parts[1]||'',url=parts[2],port=parseInt(parts[3])||0,type=parts[4]||'B';
  if(!name||!url)return null;
  return{name,desc,url,port,type,img:relPath};
}

function sanitizeURI(s){
  return s.normalize('NFD').replace(/[\u0300-\u036f]/g,'').replace(/\s+/g,'%20');
}

function MC_FB1(t,ok){
  const a=document.createElement('textarea');
  a.value=t;a.style.position='fixed';a.style.opacity=0;
  document.body.appendChild(a);a.select();
  try{document.execCommand('copy');ok();}catch(e){}
  a.remove();
}
function MC_CP1(b){
  const t=b.querySelector('.MC_T1').textContent;
  const i=b.querySelector('.MC_I1');
  const ok=()=>{i.textContent='✅';setTimeout(()=>{i.textContent='📄';},1200);};
  if(navigator.clipboard&&navigator.clipboard.writeText)navigator.clipboard.writeText(t).then(ok,()=>MC_FB1(t,ok));
  else MC_FB1(t,ok);
}
WRAP.addEventListener('click',e=>{
  const b=e.target.closest('.MC_B1');
  if(b)MC_CP1(b);
});

function mkCard(s){
  const isB=s.type==='B'||s.type==='B+J';
  const div=document.createElement('div');
  div.className='mc-card';

  let acts='';
  if(isB){
    const uri=`minecraft:?addExternalServer=${sanitizeURI(s.name)}|${s.url}:${s.port}`;
    acts+=`<a class="mc-bbtn" href="${uri}"><img src="${ICON_B}" alt="">Añadir en Bedrock</a>`;
  }  div.innerHTML=`<div class="mc-head">
    ${s.img?`<img class="mc-thumb" src="${encodeURI(s.img)}" alt="" onerror="this.style.display='none'">`:''}
    <div class="mc-hinfo">
      <div class="mc-name">${esc(s.name)}</div>
      ${s.desc?`<div class="mc-desc">${esc(s.desc)}</div>`:''}
      <div class="MC_R1">
        <div class="MC_B1" title="Copiar IP"><span class="MC_T1">${esc(s.url)}</span><span class="MC_I1">📄</span></div>
        ${s.port?`<div class="MC_B1" title="Copiar puerto"><span class="MC_T1">${esc(s.port)}</span><span class="MC_I1">📄</span></div>`:''}
      </div>
      ${acts?`<div class="mc-acts">${acts}</div>`:''}
    </div>
  </div>`;
  return div;
}

fetch(JSON_URL)
  .then(r=>r.json())
  .then(data=>{
    const files=(data.galleries||{}).minecraft||[];
    const list=files.map(parseEntry).filter(Boolean);
    WRAP.innerHTML='';
    if(!list.length){WRAP.innerHTML='<p style="color:rgba(255,255,255,.4);font-size:.9em">Sin servidores disponibles.</p>';return;}
    const frag=document.createDocumentFragment();
    list.forEach(s=>frag.appendChild(mkCard(s)));
    WRAP.appendChild(frag);
  })
  .catch(()=>{WRAP.innerHTML='<p style="color:rgba(255,100,100,.6);font-size:.9em">Error al cargar servidores.</p>';});
})();
</script>

<a href="web/paginas/AgregarPublico.html" class="back-button"> Subir Peticion ➡️</a>
<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>

