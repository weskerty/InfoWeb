<style>
.gsi-warn{color:#ffb300}
#gsiLog{background:rgba(0,0,0,.35);border:1px solid rgba(255,255,255,.14);border-radius:10px;padding:10px 12px;height:220px;overflow-y:auto;font-size:.8em;white-space:pre-wrap;margin:10px 0;font-family:monospace}
.gsi-optrow{display:flex;align-items:center;gap:8px;margin:6px 0;flex-wrap:wrap}
.gsi-chips{display:flex;flex-wrap:wrap;gap:6px 16px;font-size:.9em;opacity:.9}
#gsiProgWrap{display:none;margin:10px 0}
#gsiProgBar{width:100%}
#gsiPlanBody p{margin:4px 0}
.gsi-optst{opacity:.7;font-size:.85em}
#gsiSlotBox{display:flex;flex-wrap:wrap;align-items:center;gap:4px 14px}
#gsiSlotBox label{cursor:pointer}
.gsi-inp{flex:1;min-width:220px;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);border-radius:10px;padding:8px 12px;color:#fff;font-family:inherit}
.gsi-wrap h3{margin-top:22px}
.gsi-wrap{position:relative}
#gsiStOv{position:absolute;inset:0;z-index:50;display:none;flex-direction:column;align-items:center;justify-content:center;gap:14px;backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);background:rgba(0,0,0,.25);border-radius:12px}
body.low-perf #gsiStOv{backdrop-filter:none;background:var(--rdm-bg)}
#gsiStOv img{width:56px;height:56px}
#gsiStOv span{color:#fff;font-size:.95em}
</style>
<div class="gsi-wrap">
<h2>Instalador GSI - NO PROBADO PELIGROSO USA FASTBOOT</h2>
<p id="gsiSt">Comprobando espacio...</p>

<div id="gsiChips" class="gsi-chips">
<span id="gsiChQuota"></span>
<span id="gsiChProd"></span>
<span id="gsiChOs"></span>
<span id="gsiChApi"></span>
<span id="gsiChAbi"></span>
<span id="gsiChLock"></span>
<span id="gsiChBatt"></span>
<span id="gsiSlotBox"></span>
</div>
<div id="gsiWarnBox"></div>

<div id="gsiConnBox" style="display:none">
<p>Inicia el telefono en modo Fastboot (Power + Volumen abajo) y conecta el cable.</p>
<button id="gsiBtnCnn">Conectar</button>
</div>

<div id="gsiUnlockBox" style="display:none">
<p id="gsiUnlockMsg"></p>
<button id="gsiBtnUnlock">Desbloquear bootloader</button>
</div>

<div id="gsiMainBox" style="display:none">
<h3>ROM (GSI)</h3>
<div class="gsi-optrow">
<button id="gsiRomFileBtn">Elegir archivo .img/.zip</button>
<input type="file" id="gsiRomFile" accept=".img,.zip" style="display:none">
</div>
<div class="gsi-optrow">
<input type="text" id="gsiRomUrl" class="gsi-inp" placeholder="o pega un enlace directo a la GSI (.img/.zip)">
<button id="gsiRomUrlBtn">Usar enlace</button>
</div>
<p id="gsiRomSt"></p>

<h3>Particiones opcionales</h3>
<p style="opacity:.7;font-size:.85em">Dejalas vacias si no las necesitas. vbmeta faltante puede causar bootloop en algunos dispositivos.</p>
<div id="gsiOptBox"></div>

<h3>Opciones</h3>
<label><input type="checkbox" id="gsiWipeChk"> Borrar userdata + metadata (IRREVERSIBLE)</label>

<p></p>
<button id="gsiBtnPlan" style="opacity:.5;pointer-events:none">Ver plan y flashear</button>
</div>

<div id="gsiProgWrap">
<progress id="gsiProgBar" value="0" max="1"></progress>
<p id="gsiProgLbl"></p>
</div>

<div id="gsiLog"></div>
<div class="gsi-optrow">
<input type="text" id="gsiCmdInp" class="gsi-inp" placeholder="comando fastboot manual...">
<button id="gsiCmdRun">Ejecutar</button>
</div>

<div id="gsiStOv"><img id="gsiStOvImg"><span id="gsiStOvTxt">Iniciando...</span></div>
</div>

<dialog id="gsiPlanDlg">
<h3>Confirmar flasheo</h3>
<div id="gsiPlanBody"></div>
<div style="display:flex;gap:8px;margin-top:12px">
<button id="gsiPlanCancel">Cancelar</button>
<button id="gsiPlanOk">Flashear</button>
</div>
</dialog>

<script>
(async()=>{
const ovEl=document.getElementById("gsiStOv"),ovImg=document.getElementById("gsiStOvImg"),ovTxt=document.getElementById("gsiStOvTxt");
function ovShow1(t){const wa=window.__CFG?.waitAnim;if(wa)ovImg.src=wa;ovTxt.textContent=t||"Cargando...";ovEl.style.display="flex"}
function ovHide1(){ovEl.style.display="none"}
ovShow1("Iniciando...");
const { FastbootDevice } = await import("/web/js/lib/Fastboot/fastboot.mjs");
const { ZipReader, BlobReader } = await import("https://cdn.jsdelivr.net/npm/@zip.js/zip.js@2.24.0/+esm");

const VPARTS1=["vbmeta","vbmeta_system","vbmeta_vendor","vbmeta_boot"];
const OPARTS1=["boot","vendor_boot","recovery"];
const MINB1=1.5*1024*1024*1024;
const GSIM1=64*1024*1024;
const SMM1=64*1024*1024;

let D1=null,GVA1={},SLOT1="a",ISVAB1=false,WIPE1=false,BUSY1=false,WAKE1=null;
let FILES1={},GSI1=null,GSINAME1="",GSISIZE1=0;

const E1=id=>document.getElementById(id);

function setSt1(s){E1("gsiSt").textContent=s}
function log1(t){const p=document.createElement("p");p.textContent=t;E1("gsiLog").appendChild(p);E1("gsiLog").scrollTop=E1("gsiLog").scrollHeight}
function wrapDev1(){
  const orig=D1.runCommand.bind(D1);
  D1.runCommand=async(cmd)=>{
    log1("> "+cmd);
    try{
      const r=await orig(cmd);
      log1((r.text||"(sin salida)").trim());
      return r;
    }catch(e){
      log1("! "+e.message);
      throw e;
    }
  };
}
function gv1(k){return GVA1[k]||""}
function h2d1(h){return h?parseInt(h,16)||0:0}
function mb1(n){return Math.round(n/1024/1024)}
function hasPart1(n){return h2d1(gv1("partition-size:"+n))>0}
function opp1(){return SLOT1==="a"?"b":"a"}
function setEn1(el,on){el.style.opacity=on?"":".5";el.style.pointerEvents=on?"":"none"}

async function chkQuota1(){
  try{
    const es=await navigator.storage.estimate();
    const free=(es.quota||0)-(es.usage||0);
    E1("gsiChQuota").textContent="💻 "+(free/1024/1024/1024).toFixed(1)+"GB";
    if(!es.quota||free<MINB1){setSt1("Espacio insuficiente, se necesita al menos 1.5 GB libres");return false}
    return true;
  }catch(e){setSt1("No se pudo comprobar el espacio: "+e.message);return false}
}

function fixEp1(){
  const dev=D1.device;
  if(!dev||dev.__epFixed)return;
  dev.__epFixed=true;
  let realIn=null;
  try{
    for(const iface of dev.configuration.interfaces)for(const ep of iface.alternate.endpoints){
      if(ep.endpointNumber===D1.epIn&&ep.direction==="in")realIn=ep.packetSize;
    }
  }catch(e){}
  if(realIn&&realIn!==64){
    const orig=dev.transferIn.bind(dev);
    dev.transferIn=(ep,len)=>orig(ep,ep===D1.epIn?realIn:len);
  }
}

async function readAll1(){
  fixEp1();
  const r=await D1.runCommand("getvar:all");
  GVA1={};
  (r.text||"").split("\n").forEach(ln=>{
    const i=ln.lastIndexOf(":");
    if(i<0)return;
    GVA1[ln.slice(0,i).trim()]=ln.slice(i+1).trim();
  });
  SLOT1=gv1("current-slot")||"a";
}

async function readAllRetry1(tries,delay){
  for(let i=0;i<tries;i++){
    try{
      await Promise.race([readAll1(),new Promise((_,rj)=>setTimeout(()=>rj(new Error("timeout")),20000))]);
      if(Object.keys(GVA1).length)return;
    }catch(e){}
    await new Promise(r=>setTimeout(r,delay));
  }
  throw new Error("El dispositivo no respondio tras varios intentos");
}

async function ensureFbd1(){
  if(gv1("is-userspace")==="yes")return;
  setSt1("Cambiando a fastbootd...");
  try{await D1.reboot("fastboot",false)}catch(e){}
  await Promise.race([D1.waitForConnect(),new Promise(r=>setTimeout(r,8000))]);
  await readAllRetry1(8,1500);
}

async function toBootloader1(){
  if(gv1("is-userspace")!=="yes")return;
  setSt1("Volviendo al bootloader...");
  try{await D1.reboot("bootloader",false)}catch(e){}
  await Promise.race([D1.waitForConnect(),new Promise(r=>setTimeout(r,8000))]);
  await readAllRetry1(8,1500);
}

function superFree1(){
  const sup=h2d1(gv1("partition-size:super"));
  let used=0;
  for(const k in GVA1){
    const m=k.match(/^partition-size:(.+)$/);
    if(!m)continue;
    if(gv1("is-logical:"+m[1])==="yes")used+=h2d1(GVA1[k]);
  }
  return sup-used;
}

function renderInfo1(){
  const treble=gv1("treble-enabled"),batt=gv1("battery-soc");
  E1("gsiChProd").textContent="📱 "+gv1("product");
  E1("gsiChOs").textContent="🤖 "+gv1("version-os");
  E1("gsiChApi").textContent="🔢 API "+gv1("first-api-level");
  E1("gsiChAbi").textContent="⚙️ "+gv1("cpu-abi");
  E1("gsiChLock").textContent=gv1("unlocked")==="yes"?"🔓 Desbloqueado":"🔒 BLOQUEADO";
  E1("gsiChBatt").textContent="🔋 "+(batt||"?")+"%";
  let w="";
  if(treble!=="true")w+='<p class="gsi-warn">⚠️ No reporta Treble activado, la GSI puede no funcionar</p>';
  if(batt&&+batt<30)w+='<p class="gsi-warn">⚠️ Bateria baja, riesgo de corte durante el flasheo</p>';
  E1("gsiWarnBox").innerHTML=w;
}

function detectSlot1(){
  const sa=h2d1(gv1("partition-size:system_a")),sb=h2d1(gv1("partition-size:system_b"));
  const box=E1("gsiSlotBox");box.innerHTML="";
  const ico=document.createElement("span");ico.textContent="🔀";box.appendChild(ico);
  if(sa>0&&sb>0){
    ["a","b"].forEach(s=>{
      const lbl=document.createElement("label");
      const rad=document.createElement("input");rad.type="radio";rad.name="gsiSlot";rad.value=s;rad.checked=s===SLOT1;
      rad.addEventListener("change",()=>{SLOT1=s;renderOptParts1()});
      lbl.appendChild(rad);lbl.append(" Slot "+s.toUpperCase());
      box.appendChild(lbl);
    });
  }else if(sa>0){
    ISVAB1=true;SLOT1="a";
    const sp=document.createElement("span");sp.textContent="Slot A (VAB)";box.appendChild(sp);
  }else if(sb>0){
    ISVAB1=true;SLOT1="b";
    const sp=document.createElement("span");sp.textContent="Slot B (VAB)";box.appendChild(sp);
  }else{
    box.innerHTML='<p class="gsi-warn">No se encontro particion system, no se puede continuar</p>';
  }
}

const OPLABEL1={vbmeta:"Vbmeta",vbmeta_system:"Vbmeta System",vbmeta_vendor:"Vbmeta Vendor",vbmeta_boot:"Vbmeta Boot",boot:"Boot",vendor_boot:"Vendor Boot",recovery:"Recovery"};

function renderOptParts1(){
  const box=E1("gsiOptBox");box.innerHTML="";
  [...VPARTS1,...OPARTS1].forEach(p=>{
    if(!hasPart1(p+"_"+SLOT1))return;
    const row=document.createElement("div");row.className="gsi-optrow";
    const lbl=document.createElement("span");lbl.textContent=(OPLABEL1[p]||p)+":";
    const btn=document.createElement("button");btn.textContent="Seleccionar";
    const st=document.createElement("span");st.className="gsi-optst";
    if(FILES1[p])st.textContent=FILES1[p].name;
    const inp=document.createElement("input");inp.type="file";inp.accept=".img";inp.style.display="none";
    inp.addEventListener("change",()=>{
      if(!inp.files[0])return;
      FILES1[p]=inp.files[0];
      st.textContent=inp.files[0].name;
    });
    btn.addEventListener("click",()=>inp.click());
    row.appendChild(lbl);row.appendChild(btn);row.appendChild(st);row.appendChild(inp);
    box.appendChild(row);
  });
}

const OPN1=["gsi_dl","gsi_img"];
async function opfsW1(n){
  const h=await (await navigator.storage.getDirectory()).getFileHandle(n,{create:true});
  return{h,w:await h.createWritable()};
}
async function opfsClr1(){
  try{const d=await navigator.storage.getDirectory();for(const n of OPN1)await d.removeEntry(n).catch(()=>{})}catch(e){}
}

async function extractImgFromZip1(blob,onProg){
  const zr=new ZipReader(new BlobReader(blob));
  const entries=await zr.getEntries();
  const entry=entries.find(e=>!e.directory&&/\.img$/i.test(e.filename));
  if(!entry){await zr.close();throw new Error("No se encontro un .img dentro del zip")}
  const{h,w}=await opfsW1("gsi_img");
  await entry.getData(w,{
    onprogress:(p,t)=>onProg&&t&&onProg(p/t)
  });
  await zr.close();
  return{blob:await h.getFile(),name:entry.filename.split("/").pop()};
}

async function fetchWithProgress1(url,onProg){
  const res=await fetch(url);
  if(!res.ok)throw new Error("HTTP "+res.status);
  const len=+res.headers.get("content-length")||0;
  const{h,w}=await opfsW1("gsi_dl");
  const reader=res.body.getReader();
  let got=0;
  for(;;){
    const{done,value}=await reader.read();
    if(done)break;
    await w.write(value);got+=value.length;
    len&&onProg&&onProg(got/len);
  }
  await w.close();
  return await h.getFile();
}

async function vbOff1(f){
  const b=new Uint8Array(await f.slice(0,128).arrayBuffer());
  if(b.length<128||String.fromCharCode(...b.subarray(0,4))!=="AVB0")return f;
  b[123]|=3;
  log1("vbmeta: verity y verificacion desactivadas");
  return new Blob([b,f.slice(128)]);
}

function updFlashReady1(){setEn1(E1("gsiBtnPlan"),!!GSI1)}

async function useGsiBlob1(blob,name){
  if(/\.xz$/i.test(name))throw new Error("Los archivos .xz no son soportados, descomprimilos antes de subirlos");
  if(/\.zip$/i.test(name)){
    E1("gsiRomSt").textContent="Extrayendo "+name+"...";
    const r=await extractImgFromZip1(blob,p=>E1("gsiRomSt").textContent="Extrayendo... "+Math.round(p*100)+"%");
    GSI1=r.blob;GSINAME1=r.name;
  }else{
    GSI1=blob;GSINAME1=name;
  }
  GSISIZE1=GSI1.size;
  E1("gsiRomSt").textContent=GSINAME1+" ("+(GSISIZE1/1024/1024/1024).toFixed(2)+" GB)";
  updFlashReady1();
}

E1("gsiRomFileBtn").addEventListener("click",()=>E1("gsiRomFile").click());
E1("gsiRomFile").addEventListener("change",async()=>{
  const f=E1("gsiRomFile").files[0];
  if(!f)return;
  try{await useGsiBlob1(f,f.name)}catch(e){E1("gsiRomSt").textContent="Error: "+e.message}
});

E1("gsiRomUrlBtn").addEventListener("click",async()=>{
  const u=E1("gsiRomUrl").value.trim();
  if(!u)return;
  setEn1(E1("gsiRomUrlBtn"),false);
  try{
    const name=decodeURIComponent(u.split("/").pop().split("?")[0])||"rom.img";
    E1("gsiRomSt").textContent="Descargando...";
    const blob=await fetchWithProgress1(u,p=>E1("gsiRomSt").textContent="Descargando... "+Math.round(p*100)+"%");
    await useGsiBlob1(blob,name);
  }catch(e){
    E1("gsiRomSt").textContent="Error: "+e.message+" (revisa que el enlace permita descarga directa/CORS)";
  }
  setEn1(E1("gsiRomUrlBtn"),true);
});

E1("gsiWipeChk").addEventListener("change",()=>{WIPE1=E1("gsiWipeChk").checked});

async function runManualCmd1(){
  const cmd=E1("gsiCmdInp").value.trim();
  if(!cmd||!D1)return;
  E1("gsiCmdInp").value="";
  try{await D1.runCommand(cmd)}catch(e){}
}
E1("gsiCmdRun").addEventListener("click",runManualCmd1);
E1("gsiCmdInp").addEventListener("keydown",ev=>{if(ev.key==="Enter")runManualCmd1()});

function buildPlan1(){
  const b=E1("gsiPlanBody");b.textContent="";
  const add=(t,w)=>{const p=document.createElement("p");p.textContent=t;if(w)p.className="gsi-warn";b.appendChild(p)};
  add("GSI -> system_"+SLOT1+": "+GSINAME1+" ("+(GSISIZE1/1024/1024/1024).toFixed(2)+" GB)");
  VPARTS1.forEach(p=>{
    if(!hasPart1(p+"_"+SLOT1))return;
    if(FILES1[p])add(p+"_"+SLOT1+": "+FILES1[p].name+(p==="vbmeta"?" (sin verity ni verificacion)":""));
    else add(p+".img no seleccionado, riesgo de bootloop",1);
  });
  OPARTS1.forEach(p=>{
    if(hasPart1(p+"_"+SLOT1)&&FILES1[p])add(p+"_"+SLOT1+": "+FILES1[p].name);
  });
  if(WIPE1)add("Se borrara userdata y metadata (IRREVERSIBLE)",1);
}

E1("gsiBtnPlan").addEventListener("click",()=>{
  if(!GSI1)return;
  buildPlan1();
  E1("gsiPlanDlg").showModal();
});
E1("gsiPlanCancel").addEventListener("click",()=>E1("gsiPlanDlg").close());
E1("gsiPlanOk").addEventListener("click",()=>{E1("gsiPlanDlg").close();doFlash1()});

async function tryFreeSpace1(needed,avail){
  const o=opp1();
  const sysOpp=h2d1(gv1("partition-size:system_"+o));
  if(sysOpp>0&&confirm("Falta espacio. Borrar system_"+o+" ("+mb1(sysOpp)+"MB, slot inactivo)?")){
    await D1.runCommand("delete-logical-partition:system_"+o);
    avail+=sysOpp;
    if(avail>=needed)return avail;
  }
  const prodOpp=h2d1(gv1("partition-size:product_"+o));
  if(prodOpp>0&&confirm("Sigue faltando espacio. Borrar product_"+o+" ("+mb1(prodOpp)+"MB, slot inactivo)?")){
    await D1.runCommand("delete-logical-partition:product_"+o);
    avail+=prodOpp;
    if(avail>=needed)return avail;
  }
  const prodCur=h2d1(gv1("partition-size:product_"+SLOT1));
  if(prodCur>0&&confirm("Sigue faltando espacio. Borrar product_"+SLOT1+" ("+mb1(prodCur)+"MB, slot activo)?")){
    await D1.runCommand("delete-logical-partition:product_"+SLOT1);
    avail+=prodCur;
    if(avail>=needed)return avail;
  }
  throw new Error("Espacio insuficiente para la GSI incluso liberando particiones");
}

async function doResize1(){
  const needed=GSISIZE1+GSIM1;
  const cur=h2d1(gv1("partition-size:system_"+SLOT1));
  if(cur>=needed)return;
  const free=superFree1();
  let avail=cur+free;
  if(avail<needed)avail=await tryFreeSpace1(needed,avail);
}

async function tryMirrorOpp1(){
  if(ISVAB1)return;
  const o=opp1();
  const sysCur=h2d1(gv1("partition-size:system_"+SLOT1));
  const sysOpp=h2d1(gv1("partition-size:system_"+o));
  if(sysOpp===0)return;
  const needExtra=sysCur-sysOpp;
  if(needExtra<=0)return;
  if(superFree1()-needExtra<SMM1)return;
  if(!confirm("Copiar tamano a system_"+o+" para futuras actualizaciones OTA?"))return;
  try{
    await D1.runCommand("resize-logical-partition:system_"+o+":"+sysCur);
    log1("system_"+o+" preparado para OTA");
  }catch(e){log1("No se pudo preparar system_"+o+" para OTA")}
}

function prog1(label){
  return p=>{E1("gsiProgBar").value=p;E1("gsiProgLbl").textContent=label+" "+Math.round(p*100)+"%"};
}

function beforeUnload1(e){e.preventDefault();e.returnValue=""}

async function doFlash1(){
  if(BUSY1)return;
  BUSY1=true;
  window.addEventListener("beforeunload",beforeUnload1);
  try{WAKE1=await navigator.wakeLock.request("screen")}catch(e){}
  E1("gsiLog").innerHTML="";
  E1("gsiProgWrap").style.display="";
  try{
    await ensureFbd1();
    log1("Verificando espacio...");
    await doResize1();

    for(const p of VPARTS1){
      if(!FILES1[p]||!hasPart1(p+"_"+SLOT1))continue;
      log1("Flasheando "+p+"_"+SLOT1+"...");
      await D1.flashBlob(p+"_"+SLOT1,p==="vbmeta"?await vbOff1(FILES1[p]):FILES1[p],prog1(p));
      log1(p+"_"+SLOT1+" OK");
    }

    log1("Flasheando GSI a system_"+SLOT1+"...");
    await D1.flashBlob("system_"+SLOT1,GSI1,prog1("system"));
    log1("system_"+SLOT1+" OK");

    await toBootloader1();

    for(const p of OPARTS1){
      if(!FILES1[p]||!hasPart1(p+"_"+SLOT1))continue;
      log1("Flasheando "+p+"_"+SLOT1+"...");
      await D1.flashBlob(p+"_"+SLOT1,FILES1[p],prog1(p));
      log1(p+"_"+SLOT1+" OK");
    }

    if(WIPE1){
      log1("Borrando userdata...");
      await D1.runCommand("erase:userdata");
      log1("Borrando metadata...");
      await D1.runCommand("erase:metadata");
    }

    await tryMirrorOpp1();

    await D1.runCommand("set_active:"+SLOT1);
    log1("Reiniciando...");
    await D1.reboot();
    log1("Listo. El dispositivo esta reiniciando al slot "+SLOT1);
    GSI1=null;updFlashReady1();opfsClr1();
  }catch(e){
    log1("Error: "+e.message);
  }finally{
    BUSY1=false;
    window.removeEventListener("beforeunload",beforeUnload1);
    if(WAKE1){WAKE1.release().catch(()=>{});WAKE1=null}
  }
}

function afterConnect1(){
  E1("gsiConnBox").style.display="none";
  renderInfo1();
  if(gv1("unlocked")!=="yes"){
    E1("gsiUnlockBox").style.display="";
    E1("gsiUnlockMsg").textContent="Bootloader bloqueado. Activa OEM Unlock en Opciones de desarrollador y desbloquea.";
    return;
  }
  detectSlot1();
  renderOptParts1();
  E1("gsiMainBox").style.display="";
  setSt1("Listo");
}

E1("gsiBtnUnlock").addEventListener("click",async()=>{
  setEn1(E1("gsiBtnUnlock"),false);
  try{await toBootloader1()}catch(e){}
  E1("gsiUnlockMsg").textContent="Intentando desbloquear, revisa la pantalla del telefono (volumen para navegar, power para confirmar)...";
  for(const c of ["flashing unlock","oem unlock"]){
    try{await D1.runCommand(c)}catch(e){}
  }
  const raced=await Promise.race([D1.waitForDisconnect().then(()=>"disc"),new Promise(r=>setTimeout(()=>r("to"),6000))]);
  if(raced==="disc"){
    E1("gsiUnlockMsg").textContent="El dispositivo se reinicio, esperando reconexion...";
    try{await D1.waitForConnect()}catch(e){}
    await new Promise(r=>setTimeout(r,1000));
  }
  await readAllRetry1(5,1500);
  if(gv1("unlocked")==="yes"){
    E1("gsiUnlockBox").style.display="none";
    try{await ensureFbd1()}catch(e){setSt1("Error: "+e.message)}
    afterConnect1();
  }else{
    E1("gsiUnlockMsg").innerHTML="No se pudo desbloquear. Depende de la marca: algunos como Xiaomi usan un proceso distinto con autorizacion previa desde su pagina oficial.";
    setEn1(E1("gsiBtnUnlock"),true);
  }
});

E1("gsiBtnCnn").addEventListener("click",async()=>{
  setEn1(E1("gsiBtnCnn"),false);
  ovShow1("Conectando...");
  setSt1("Selecciona el dispositivo en el dialogo de Chrome...");
  try{
    D1=new FastbootDevice();
    wrapDev1();
    await D1.connect();
    D1.waitForDisconnect().then(()=>{setSt1("Dispositivo desconectado");setEn1(E1("gsiBtnCnn"),true)});
    setSt1("Conectado, leyendo informacion...");
    ovShow1("Leyendo informacion...");
    await readAllRetry1(5,1000);
    if(gv1("unlocked")==="yes"){ovShow1("Entrando a fastbootd...");await ensureFbd1()}
    afterConnect1();
  }catch(e){
    setSt1("Error: "+e.message);
    setEn1(E1("gsiBtnCnn"),true);
  }finally{
    ovHide1();
  }
});

const cont=document.getElementById("content");
if(cont)cont.addEventListener("contentUnload",()=>{
  window.removeEventListener("beforeunload",beforeUnload1);
  if(WAKE1){WAKE1.release().catch(()=>{});WAKE1=null}
  opfsClr1();
},{once:true});

await opfsClr1();
const ok=await chkQuota1();
if(ok){E1("gsiConnBox").style.display="";setSt1("Listo para conectar")}
ovHide1();
})();
</script>
