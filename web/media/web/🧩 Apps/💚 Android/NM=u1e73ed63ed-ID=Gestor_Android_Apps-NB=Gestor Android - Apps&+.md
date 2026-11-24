<style>
.adb-wrap{position:relative}
#adbStOv{position:absolute;inset:0;z-index:50;display:none;flex-direction:column;align-items:center;justify-content:center;gap:14px;backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);background:rgba(0,0,0,.25);border-radius:12px}
body.low-perf #adbStOv{backdrop-filter:none;background:var(--rdm-bg)}
#adbStOv img{width:56px;height:56px}
#adbStOv span{color:#fff;font-size:.95em}
.adbAp::before{content:none}
.adbAp.off{opacity:.55}
.adbAp-i{width:58px;height:58px;display:flex;align-items:center;justify-content:center;font-size:1.7rem;background:rgba(0,0,0,.25);flex-shrink:0}
.adbAp .BMD1-CN{padding-right:8px}
.adbAp-s{font-size:.78rem!important;opacity:.85}
.adbAp-b{display:flex;gap:6px;padding-right:10px;flex-shrink:0}
.adbAp-b button{min-width:38px;height:38px;padding:0 6px}
.adbOp{display:flex;align-items:center;justify-content:space-between;gap:10px;padding:6px 0;border-bottom:1px solid rgba(255,255,255,.08);font-size:.85em;word-break:break-all}
.adbAp{cursor:pointer}
.adbAp-b button:disabled{opacity:.35}
.adbRow{display:flex;gap:8px;flex-wrap:wrap;margin:14px 0;align-items:center}
#adbDev{display:none;gap:16px;align-items:flex-start;margin:14px 0;flex-wrap:wrap}
.adbPh{width:130px;flex-shrink:0;border:3px solid rgba(255,255,255,.35);border-radius:20px;padding:8px 4px 12px;background:#000;cursor:pointer}
.adbPh::before{content:'';display:block;width:34px;height:4px;border-radius:2px;background:rgba(255,255,255,.3);margin:0 auto 6px}
.adbPh img{width:100%;min-height:200px;display:block;border-radius:6px;background:#111}
#adbDevI{flex:1;min-width:190px;display:grid;grid-template-columns:auto 1fr;gap:4px 10px;font-size:.85em;margin:0}
#adbDevI dt{opacity:.65}
#adbDevI dd{margin:0}
#adbCf h3{word-break:break-all;margin-right:44px}
</style>
<div class="adb-wrap">
<h2>Gestor Android</h2>
<p id="adbSt">Iniciando...</p>

<details id="adbHowTo">
  <summary style="">Como Activar ADB</summary>

VideoFuturo

</details>

<div class="BS1">
<a class="BS2" id="adbBtnCnn">
<span class="BS4">🔌</span><p class="BS5">Conectar</p>
</a>
<a class="BS2" id="adbBtnRep">
<span class="BS4">🩹</span><p class="BS5">Rep. pantalla</p>
</a>
<a class="BS2" id="adbBtnApps" style="opacity:.5;pointer-events:none">
<span class="BS4">📱</span><p class="BS5">Apps</p>
</a>
<a class="BS2" id="adbBtnFl" style="opacity:.5;pointer-events:none">
<span class="BS4">📁</span><p class="BS5">Archivos</p>
</a>
<a class="BS2" id="adbBtnSec" style="opacity:.5;pointer-events:none">
<span class="BS4">🕵️</span><p class="BS5">Anti espia</p>
</a>
<a class="BS2" id="adbBtnCmd" style="opacity:.5;pointer-events:none">
<span class="BS4">📟</span><p class="BS5">Comandos</p>
</a>
<a class="BS2" id="adbBtnScr" style="opacity:.5;pointer-events:none">
<span class="BS4">📱</span><p class="BS5">Pantalla</p>
</a>
</div>

<div id="adbDev"><div class="adbPh" title="Actualizar captura"><img id="adbPhImg" alt="Pantalla del telefono"></div><dl id="adbDevI"></dl></div>

<input type="file" id="adbFileApk" accept=".apk,.apks,.xapk,.apkm,.zip" multiple style="display:none">

<div id="adbStore">
<div id="adbSearchBar" style="display:flex;align-items:center;gap:10px;margin:14px 0;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);border-radius:24px;padding:10px 16px">
<span style="opacity:.5">🔍</span>
<input id="adbSearchInp" type="search" placeholder="Buscar Nuevas Apps..." autocomplete="off" style="flex:1;background:none;border:none;outline:none;color:#fff;font-size:1rem;font-family:inherit">
</div>
<div id="adbStoreGrid"></div>
<div id="adbStorePg" class="PG1" style="display:none"></div>
</div>

<div id="adbLst" style="display:none">
<div class="adbRow"><button id="adbApIns">📥 Instalar APK</button><button id="adbApScan">🔄 Escanear</button></div>
<div id="adbApList"></div>
</div>

<div id="adbFl" style="display:none">
<div class="adbRow"><button id="adbFlUp">⬅️ Atras</button><button id="adbFlPut">📤 Subir archivo</button><span id="adbFlPath" style="opacity:.7;font-size:.85em;word-break:break-all"></span></div>
<input type="file" id="adbFlIn" multiple style="display:none">
<div id="adbFlList"></div>
</div>

<div id="adbSec" style="display:none">
<div class="adbRow"><button id="adbSecRe">🔄 Revisar de nuevo</button></div>
<div id="adbSecList"></div>
</div>

<div id="adbCmdPnl" style="display:none">
<div id="adbCmdGrid" style="display:flex;flex-wrap:wrap;gap:8px;margin:14px 0"></div>
<pre id="adbCmdLog" style="background:rgba(0,0,0,.35);border:1px solid rgba(255,255,255,.14);border-radius:10px;padding:10px 12px;height:220px;overflow-y:auto;font-size:.8em;white-space:pre-wrap;margin:0 0 10px"></pre>
<div style="display:flex;gap:8px">
<input id="adbCmdInp" type="text" placeholder="comando adb shell..." autocomplete="off" style="flex:1;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);border-radius:10px;padding:8px 12px;color:#fff;font-family:monospace;font-size:.85em;outline:none">
<button id="adbCmdRun" style="background:rgba(255,255,255,.09);border:1px solid rgba(255,255,255,.14);border-radius:10px;color:#fff;padding:6px 16px;cursor:pointer;font-family:inherit">Ejecutar</button>
</div>
</div>

<div id="adbScrPnl" style="display:none;text-align:center">
<p id="adbScrSt" style="opacity:.7;font-size:.85em">Presiona Pantalla para iniciar</p>
<div id="adbScrHold" style="max-width:100%;display:inline-block;touch-action:none"></div>
</div>
<div id="adbStOv"><img id="adbStOvImg"><span>Iniciando...</span></div>
</div>

<dialog id="adbCfDlg" class="DX1">
<button data-x="1" id="adbCfX">✕</button>
<div id="adbCf"></div>
</dialog>

<dialog id="adbRepDlg" class="DX1">
<button data-x="1" id="adbBtnRepClose">✕</button>
<h3>Reparar acceso ADB (pantalla rota + TWRP)</h3>
<div id="adbRepStep1">
<p>Esto sirve si tu pantalla esta rota y <strong>Ya tenias TWRP u OrangeFox</strong> instalado (requiere bootloader desbloqueado). No funciona con el recovery de fabrica de Android.</p>
<ol>
<li>Apaga el telefono.</li>
<li>Mantene presionado Volumen abajo + Power hasta entrar al recovery.</li>
<li>Conecta el cable USB a la computadora.</li>
<li>Presiona "Probar conexion" abajo.</li>
<li>Opcional en el paso siguiente: formatear data y desactivar el cifrado con <a href="https://github.com/leegarchat/dfe-neo-v2/releases/download/2.6.0b1/arm64-v8a-en-DFE-NEO-2.6.0-beta-1-lite.zip" target="_blank">DFE.zip</a>.</li>
</ol>


<p style="font-family: monospace; white-space: pre; margin: 0;">             Boton Encendido</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ ⬇️</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢠⣾⣿⣿⠿⠿⠿⠿⠿⢿⣿⠿⢿⣿⣷⡄</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⣿⡇</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣿ ⬅️ Volumen +</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠀⠀TWRP⠀⠀⠀⠀⣿⡇</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀Recovery ⠀⣿⣿ </p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⡇</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⡇</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⡇</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⢸⣿⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣿⡇</p>
<p style="font-family: monospace; white-space: pre; margin: 0;">⠀⠀⠀⠀⠀⠀⠀⠘⢿⣿⣿⣿⣦⣤⣤⣤⣤⣴⣿⣿⣿⡿⠃</p>


<a class="back-button" id="adbBtnRepTest">Probar conexion</a>
<p id="adbRepMsg"></p>
</div>
<div id="adbRepStep2" style="display:none">
<p id="adbRepPlan" style="white-space:pre-line"></p>
<p><label><input type="checkbox" id="adbRepFmt"> Formatear data (borra TODO, IRREVERSIBLE)</label></p>
<p><a class="back-button" id="adbBtnRepDfe">Elegir DFE.zip (opcional)</a> <span id="adbRepDfeN"></span></p>
<input type="file" id="adbRepDfe" accept=".zip" style="display:none">
<a class="view-all-button" id="adbBtnRepRun">Ejecutar reparacion</a>
</div>
<div id="adbRepStep3" style="display:none">
<p id="adbRepDone"></p>
</div>
</dialog>

<script>
const CMDS1=[
{n:"Info bateria",c:"dumpsys battery"},
{n:"Espacio libre",c:"df -h /data"},
{n:"Reiniciar",c:"reboot"},
{n:"Anti-Kill Termux",c:"device_config set_sync_disabled_for_tests persistent;device_config put activity_manager max_phantom_processes 2147483647;device_config put runtime_native_boot use_freezer false;settings put global settings_enable_monitor_phantom_procs false;am set-inactive com.termux false;cmd deviceidle whitelist +com.termux;cmd power set-mode 0;dumpsys deviceidle disable;cmd appops set --uid com.termux RUN_IN_BACKGROUND allow;cmd appops set --uid com.termux RUN_ANY_IN_BACKGROUND allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_ACTIVITY_BG_START_RESTRICTION allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_HIBERNATION allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_POWER_RESTRICTIONS allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_SUSPENSION allow;cmd appops set --uid com.termux WAKE_LOCK allow;cmd appops set --uid com.termux REQUEST_IGNORE_BATTERY_OPTIMIZATIONS allow;cmd appops set --uid com.termux ACTIVATE_PLATFORM_VPN allow;cmd appops set --uid com.termux INTERACT_ACROSS_PROFILES allow;cmd appops set --uid com.termux SCHEDULE_EXACT_ALARM allow;cmd appops set --uid com.termux START_FOREGROUND allow;echo listo anti-kill"}
];

(async()=>{
const stOv=document.getElementById("adbStOv"),stOvImg=document.getElementById("adbStOvImg");
const wa=window.__CFG?.waitAnim;
if(wa){stOvImg.src=wa;stOv.style.display="flex"}
try{
const[
{AdbDaemonTransport,Adb,adbGeneratePublicKey},
{AdbDaemonWebUsbDeviceManager},
{default:AdbWebCredentialStore},
{DefaultServerPath,AndroidMotionEventAction,AndroidMotionEventButton,ScrcpyPointerId,clamp},
{AdbScrcpyClient,AdbScrcpyOptions3_3_3},
{WebCodecsVideoDecoder,WebGLVideoFrameRenderer,BitmapVideoFrameRenderer}
]=await Promise.all([
import("https://cdn.jsdelivr.net/npm/@yume-chan/adb@2.6.4/+esm"),
import("https://cdn.jsdelivr.net/npm/@yume-chan/adb-daemon-webusb@2.3.2/+esm"),
import("https://cdn.jsdelivr.net/npm/@yume-chan/adb-credential-web@2.1.0/+esm"),
import("https://cdn.jsdelivr.net/npm/@yume-chan/scrcpy@2.3.0/+esm"),
import("https://cdn.jsdelivr.net/npm/@yume-chan/adb-scrcpy@2.3.2/+esm"),
import("https://cdn.jsdelivr.net/npm/@yume-chan/scrcpy-decoder-webcodecs@2.5.3/+esm")
]);

const U1="https://raw.githubusercontent.com/Universal-Debloater-Alliance/universal-android-debloater-next-generation/main/resources/assets/uad_lists.json";
const R1=["Recommended","Advanced","Expert","Unsafe"];
const PR1=["com.android.systemui","com.android.settings","com.android.phone","com.android.shell","android"];
const FN1="/api/fdroid";
const SRVJ1="web/js/lib/Binarios/scrcpy-server-v3.3.4";

let D1=null,A1=null,AR1=null,abi1=null;
let stCur=[],stPg=0,stDbt=null,stAC=null;
const CS1=new AdbWebCredentialStore("WebADBDebloater");

const el=id=>document.getElementById(id);
const stEl=el("adbSt"),btnCnn=el("adbBtnCnn"),btnApps=el("adbBtnApps"),lstEl=el("adbLst"),apList=el("adbApList");
const cfDlg=el("adbCfDlg"),cf=el("adbCf");
const btnFl=el("adbBtnFl"),flEl=el("adbFl"),flList=el("adbFlList"),flPath=el("adbFlPath"),flIn=el("adbFlIn");
const btnSec=el("adbBtnSec"),secEl=el("adbSec"),secList=el("adbSecList");
const devEl=el("adbDev"),devI=el("adbDevI"),phImg=el("adbPhImg");
el("adbApScan").addEventListener("click",()=>{if(A1)scanAll()});
el("adbApIns").addEventListener("click",()=>{if(A1)fileInp.click()});
el("adbCfX").addEventListener("click",()=>cfDlg.close());
for(const d of [cfDlg,el("adbRepDlg")])d.addEventListener("close",()=>{document.body.style.overflow=""});
function dOpen(d){if(!d.open)d.showModal();document.body.style.overflow="hidden"}
const btnRep=el("adbBtnRep"),repDlg=el("adbRepDlg"),repMsg=el("adbRepMsg");
const repStep1=el("adbRepStep1"),repStep2=el("adbRepStep2"),repStep3=el("adbRepStep3");
const repPlan=el("adbRepPlan"),repDone=el("adbRepDone");
const btnRepTest=el("adbBtnRepTest"),btnRepRun=el("adbBtnRepRun"),btnRepClose=el("adbBtnRepClose");
const storeEl=el("adbStore"),gridEl=el("adbStoreGrid"),pgEl=el("adbStorePg");
const searchInp=el("adbSearchInp"),fileInp=el("adbFileApk");
const btnCmd=el("adbBtnCmd"),cmdPnl=el("adbCmdPnl"),cmdGrid=el("adbCmdGrid"),cmdLog=el("adbCmdLog"),cmdInp=el("adbCmdInp"),cmdRun=el("adbCmdRun");
const howTo=el("adbHowTo");
const btnScr=el("adbBtnScr"),scrPnl=el("adbScrPnl"),scrSt=el("adbScrSt"),scrHold=el("adbScrHold");

function setSt(s){stEl.textContent=s}
function enable(btn){btn.style.opacity="";btn.style.pointerEvents=""}

async function runSh(cmd){return await A1.subprocess.noneProtocol.spawnWaitText(cmd)}
async function uninst(id){return await runSh("pm uninstall --user 0 "+id)}
async function restr(id){return await runSh("cmd package install-existing "+id)}

function parsePkgs(txt){
const arr=[];
for(const ln of txt.split("\n")){
const m=ln.match(/^package:(\S+)/);
if(m)arr.push(m[1]);
}
return arr;
}

const PKR1=/^[A-Za-z0-9._]+$/,OPR1=/^[A-Z][A-Z0-9_]*$/;
const CN1={Recommended:"Recomendado",Advanced:"Avanzado",Expert:"Experto",Unsafe:"Inseguro",Unlisted:"Sin listar"};
let SC1=null,CF1=null,ZJ1=null;
function ov(t){if(!wa)return;stOv.querySelector("span").textContent=t||"";stOv.style.display=t?"flex":"none"}
function mb(k){return k>=1048576?(k/1048576).toFixed(1)+" GB":k>=1024?Math.round(k/1024)+" MB":k+" KB"}
function oomL(o){return o<0?"Sistema":o===0?"Al frente":o<900?"Segundo plano":"En cache"}
function q1(x){return"'"+String(x).replace(/'/g,"'\\''")+"'"}
function dl(b,n){const u=URL.createObjectURL(b),a=document.createElement("a");a.href=u;a.download=n;a.click();setTimeout(()=>URL.revokeObjectURL(u),15000)}
async function rdB(st){const r=st.getReader(),c=[];for(;;){const{done,value}=await r.read();if(done)break;c.push(value)}return new Blob(c)}
async function syncDo(f){const sy=await A1.sync();try{return await f(sy)}finally{await sy.dispose()}}
function zjs(){return ZJ1||(ZJ1=import("https://cdn.jsdelivr.net/npm/@zip.js/zip.js@2.24.0/+esm"))}
function secs(o,ks){const sec={};let cur=null;const re=new RegExp("^@("+ks+")\\s*$");for(const ln of o.split("\n")){const m=ln.match(re);if(m){cur=m[1];sec[cur]=[];continue}if(cur)sec[cur].push(ln)}return sec}

function mkRow(o){
const d=document.createElement("div");d.className="BMD1 adbAp"+(o.off?" off":"");d.tabIndex=0;d.setAttribute("role","button");
const ic=document.createElement("span");ic.className="adbAp-i";ic.textContent=o.ic;
const cn=document.createElement("div");cn.className="BMD1-CN";
const h=document.createElement("h3");h.textContent=o.t;cn.appendChild(h);
if(o.de){const x=document.createElement("p");x.textContent=o.de;cn.appendChild(x)}
if(o.st){const x=document.createElement("p");x.className="adbAp-s";x.textContent=o.st;cn.appendChild(x)}
d.append(ic,cn);
if(o.b&&o.b.length){
const bx=document.createElement("div");bx.className="adbAp-b";
for(const[l,t,ok,f]of o.b){const b=document.createElement("button");b.textContent=t;b.title=l;b.setAttribute("aria-label",l);b.disabled=!ok;
b.addEventListener("click",async ev=>{ev.stopPropagation();b.disabled=true;try{await f()}catch(er){setSt("Error: "+er.message)}b.disabled=false});bx.appendChild(b)}
d.appendChild(bx);
}
if(o.go){d.addEventListener("click",o.go);d.addEventListener("keydown",ev=>{if(ev.key==="Enter"&&ev.target===d)o.go()})}
return d;
}

async function scanProc(){
const sec=secs(await runSh("echo @PS;ps -A -o PID,RSS,NAME;echo @SW;grep VmSwap /proc/[0-9]*/status 2>/dev/null;echo @OOM;grep . /proc/[0-9]*/oom_score_adj 2>/dev/null;echo @TOP;top -b -n 2 -d 1 -o PID,%CPU 2>/dev/null;echo @DK;dumpsys diskstats 2>/dev/null"),"PS|SW|OOM|TOP|DK");
const sw={},oo={},cp={},P={},Z={};
for(const l of sec.SW||[]){const m=l.match(/\/proc\/(\d+)\/status:VmSwap:\s*(\d+)/);if(m)sw[m[1]]=+m[2]}
for(const l of sec.OOM||[]){const m=l.match(/\/proc\/(\d+)\/oom_score_adj:(-?\d+)/);if(m)oo[m[1]]=+m[2]}
for(const l of sec.TOP||[]){const m=l.trim().match(/^(\d+)\s+([\d.]+)$/);if(m)cp[m[1]]=+m[2]}
for(const l of sec.PS||[]){
const m=l.trim().match(/^(\d+)\s+(\d+)\s+(\S+)$/);if(!m)continue;
const k=m[3].split(":")[0];if(!PKR1.test(k)||!k.includes("."))continue;
const e=P[k]||(P[k]={r:0,s:0,c:0,o:1e9});
e.r+=+m[2];e.s+=sw[m[1]]||0;e.c+=cp[m[1]]||0;if(m[1] in oo)e.o=Math.min(e.o,oo[m[1]]);
}
const dk=(sec.DK||[]).join("\n"),ar=n=>{const m=dk.match(new RegExp("^"+n+": (\\[.*\\])$","m"));try{return m?JSON.parse(m[1]):[]}catch(e){return[]}};
const nm=ar("Package Names"),s1=ar("App Sizes"),s2=ar("App Data Sizes"),s3=ar("Cache Sizes");
nm.forEach((n,i)=>{Z[n]=Math.round(((+s1[i]||0)+(+s2[i]||0)+(+s3[i]||0))/1024)});
return{P,Z};
}

async function scanAll(){
ov("Escaneando apps...");
setSt("Escaneando apps y bajando lista Universal-Debloater-Alliance...");
try{
const[,all,ins,dis,pr]=await Promise.all([
D1?null:fetch(U1).then(r=>{if(!r.ok)throw new Error("HTTP "+r.status);return r.json()}).then(j=>{D1=j}),
runSh("pm list packages -u"),runSh("pm list packages"),runSh("pm list packages -d"),scanProc()
]);
const on=new Set(parsePkgs(ins)),ds=new Set(parsePkgs(dis));
SC1={};
for(const id of parsePkgs(all).filter(x=>PKR1.test(x)))SC1[id]={id,...(D1[id]||{}),p:pr.P[id]||null,sz:pr.Z[id]||0,on:on.has(id),dis:ds.has(id)};
renderApps();
setSt(Object.keys(SC1).length+" paquetes, "+Object.values(SC1).filter(x=>x.p&&x.on).length+" abiertos.");
}catch(e){
setSt("Error al escanear: "+e.message);
console.error(e);
}
ov("");
}

function itOf(id){return SC1&&SC1[id]||{id,...(D1&&D1[id]||{}),p:null,sz:0,on:true,dis:false}}
function stTx(it){
if(!it.on)return"Desinstalada";
const p=it.p,a=[];
if(it.dis)a.push("Deshabilitada");
if(p)a.push("🧠 "+mb(p.r)+(p.s?" · 🔄 "+mb(p.s):"")+" · ⚡ "+Math.round(p.c)+"% · "+oomL(p.o));
if(it.sz)a.push("💾 "+mb(it.sz));
if(PR1.includes(it.id))a.push("Desinstalar esto bloquearia el telefono: solo a mano desde Comandos.");
return a.join(" · ");
}
function upd(it){if(it.el)it.el.replaceWith(it.el=mkAp(it));if(cfDlg.open&&CF1===it)cfDraw()}

async function togDis(it){
const o=(await runSh(it.dis?"pm enable "+it.id:"pm disable-user --user 0 "+it.id)).trim();
if(!/new state/i.test(o))throw new Error(o||"sin respuesta");
it.dis=!it.dis;upd(it);
}

function mkAp(it){
const lk=!it.on||PR1.includes(it.id);
return mkRow({ic:"📦",t:it.id,de:it.description||"(sin descripcion en la base UAD)",st:stTx(it),off:!it.on||it.dis,go:()=>cfOpen(it),
b:[["Configurar","⚙️",true,()=>cfOpen(it)],[it.dis?"Habilitar":"Deshabilitar",it.dis?"✅":"⛔",!lk,()=>togDis(it)]]});
}

function renderApps(){
const g={};for(const k in CN1)g[k]=[];
for(const it of Object.values(SC1))g[it.removal&&R1.includes(it.removal)?it.removal:"Unlisted"].push(it);
const sc=it=>it.p?it.p.r+it.p.s:-1;
apList.innerHTML="";
for(const k in CN1){
const its=g[k];if(!its.length)continue;
its.sort((a,b)=>sc(b)-sc(a)||(b.p?b.p.c:0)-(a.p?a.p.c:0)||a.id.localeCompare(b.id));
const det=document.createElement("details");det.open=k==="Recommended";
const sm=document.createElement("summary");const nr=its.filter(x=>x.p&&x.on).length;
sm.textContent=CN1[k]+" ("+its.length+(nr?", "+nr+" abiertas":"")+")";
det.appendChild(sm);
for(const it of its)det.appendChild(it.el=mkAp(it));
apList.appendChild(det);
if(k==="Recommended"){
const bq=document.createElement("blockquote");
bq.innerHTML="<p>Desinstalar alguna aplicacion de abajo puede causar problemas. Recuerda leer la descripcion de cada app. Sigue bajo tu responsabilidad.</p>";
apList.appendChild(bq);
}
}
}

function cfOpen(it){CF1=it;cfDraw();dOpen(cfDlg)}
function cfDraw(){
const it=CF1,id=it.id,lk=PR1.includes(id);
cf.innerHTML="";
const mk=(t,x,c)=>{const e=document.createElement(t);if(x)e.textContent=x;if(c)e.style.cssText=c;cf.appendChild(e);return e};
mk("h3",id);
const st=stTx(it);if(st)mk("p",st,"font-size:.85em;opacity:.85");
mk("p",it.description||"(sin descripcion en la base UAD)","white-space:pre-wrap");
if(it.removal||it.list)mk("p","Lista UAD: "+[it.removal&&CN1[it.removal],it.list].filter(Boolean).join(" · "),"font-size:.8em;opacity:.6");
const row=mk("div");row.className="adbRow";
const ms=document.createElement("p");ms.style.cssText="font-size:.85em;opacity:.85";
const bt=(t,ok,f)=>{const b=document.createElement("button");b.textContent=t;b.disabled=!ok;b.addEventListener("click",async()=>{b.disabled=true;ms.textContent="";try{await f()}catch(e){ms.textContent="Error: "+e.message}b.disabled=false});row.appendChild(b)};
bt("▶️ Abrir",it.on&&!it.dis,async()=>{const o=await runSh("monkey -p "+id+" -c android.intent.category.LAUNCHER 1");ms.textContent=/Events injected: 1/.test(o)?"Abierta en el telefono":o.trim().split("\n").pop()});
bt("🗑️ Desinstalar",it.on&&!lk,async()=>{
if(!confirm("Desinstalar "+id+" para el usuario actual? Se puede Reinstalar con el Boton Restaurar."))return;
const o=await uninst(id);if(!/Success/.test(o))throw new Error(o.trim());
it.on=false;it.p=null;upd(it);
});
bt("♻️ Restaurar",!it.on,async()=>{const o=await restr(id);if(!/installed/i.test(o))throw new Error(o.trim());it.on=true;upd(it)});
bt(it.dis?"✅ Habilitar":"⛔ Deshabilitar",it.on&&!lk,()=>togDis(it));
bt("💾 Respaldar APK",it.on,async()=>{ms.textContent="Copiando APK...";await bkApk(id);ms.textContent="Descargado"});
bt("🛒 Google Play",true,()=>{window.open("https://play.google.com/store/apps/details?id="+encodeURIComponent(id),"_blank","noopener")});
cf.appendChild(ms);
if(!it.on)return;
const bo=mk("p","Revisando...");
const ol=mk("div");
(async()=>{
const[ao,br]=await Promise.all([runSh("cmd appops get "+id),runSh("cmd package query-receivers --components -a android.intent.action.BOOT_COMPLETED 2>&1")]);
if(CF1!==it||!ol.isConnected)return;
const bl=br.split("\n").map(l=>l.trim().replace(/^ComponentInfo\{/,""));
bo.textContent="Arranca al encender: "+(bl.some(l=>l.startsWith(id+"/"))?"si":bl.some(l=>l.includes("/"))?"no":"no se pudo saber");
const ops=new Map();
for(const l of ao.split("\n")){
const m=l.trim().match(/^(Uid mode: )?([A-Z][A-Z0-9_]*): ([a-z]+)/);
if(!m||(m[1]&&ops.has(m[2])))continue;
ops.set(m[2],{md:m[3],u:!!m[1]});
}
if(!ops.size){ol.textContent=ao.trim()||"Sin permisos";return}
for(const[op,o]of[...ops].sort((a,b)=>a[0].localeCompare(b[0]))){
if(!OPR1.test(op))continue;
const lb=document.createElement("label");lb.className="adbOp";
const tx=document.createElement("span");tx.textContent=op;tx.title=o.md;
const cb=document.createElement("input");cb.type="checkbox";cb.checked=o.md==="allow"||o.md==="foreground";
cb.addEventListener("change",async()=>{
cb.disabled=true;
let r;
try{r=(await runSh("cmd appops set "+(o.u?"--uid ":"")+id+" "+op+" "+(cb.checked?"allow":"ignore"))).trim()}catch(e){r=e.message}
if(r){cb.checked=!cb.checked;tx.textContent=op+" - "+r}
cb.disabled=false;
});
lb.append(tx,cb);ol.appendChild(lb);
}
})().catch(e=>{bo.textContent="Error: "+e.message});
}

async function bkApk(id){
const ps=parsePkgs(await runSh("pm path "+id));
if(!ps.length)throw new Error("sin APK");
await syncDo(async sy=>{
if(ps.length===1){dl(await rdB(sy.read(ps[0])),id+".apk");return}
const z=await zjs(),w=new z.ZipWriter(new z.BlobWriter("application/zip"));
for(const x of ps)await w.add(x.split("/").pop(),new z.BlobReader(await rdB(sy.read(x))));
dl(await w.close(),id+".apks");
});
}

async function shot(){
await runSh("screencap -p /data/local/tmp/_sc.png");
const b=await syncDo(sy=>rdB(sy.read("/data/local/tmp/_sc.png")));
runSh("rm /data/local/tmp/_sc.png").catch(()=>{});
if(phImg.src)URL.revokeObjectURL(phImg.src);
phImg.src=URL.createObjectURL(new Blob([b],{type:"image/png"}));
}
async function devLoad(){
devEl.style.display="flex";
const g=secs(await runSh("echo @P;for k in ro.product.manufacturer ro.product.model ro.build.version.release ro.build.version.sdk ro.build.version.security_patch ro.boot.flash.locked ro.boot.verifiedbootstate ro.product.cpu.abi;do echo \"$k=$(getprop $k)\";done;echo @M;cat /proc/meminfo;echo @B;dumpsys battery;echo @C;cat /sys/class/power_supply/battery/cycle_count 2>/dev/null;echo @D;df -k /data 2>/dev/null;echo @U;cat /proc/uptime"),"P|M|B|C|D|U");
const kv=(a,re)=>{const o={};for(const l of a||[]){const m=l.trim().match(re);if(m)o[m[1]]=m[2].trim()}return o};
const P=kv(g.P,/^([\w.]+)=(.*)$/),M=kv(g.M,/^(\w+):\s+(\d+)/),B=kv(g.B,/^([\w ]+):\s*(.+)$/);
const df=(g.D||[]).map(l=>l.trim().split(/\s+/)).find(x=>x.length>=6&&/^\d+$/.test(x[1]));
const up=parseFloat((g.U||[])[0])||0,cy=((g.C||[])[0]||"").trim();
const HB={"1":"desconocida","2":"buena","3":"recalentada","4":"agotada","5":"sobretension","6":"falla","7":"fria"},SB={"2":"cargando","3":"descargando","4":"sin cargar","5":"llena"};
const bl=P["ro.boot.flash.locked"],vb=P["ro.boot.verifiedbootstate"];
const rows=[
["Modelo",[P["ro.product.manufacturer"],P["ro.product.model"]].filter(Boolean).join(" ")],
["Android",(P["ro.build.version.release"]||"?")+" (SDK "+(P["ro.build.version.sdk"]||"?")+")"],
["Parche",P["ro.build.version.security_patch"]],
["Bootloader",(bl==="1"?"Bloqueado":bl==="0"?"Desbloqueado":"?")+(vb?" ("+vb+")":"")],
["CPU",P["ro.product.cpu.abi"]],
["RAM",M.MemTotal?mb(+M.MemAvailable||0)+" libres de "+mb(+M.MemTotal):""],
["Swap",M.SwapTotal&&+M.SwapTotal?mb(+M.SwapTotal-(+M.SwapFree||0))+" usados de "+mb(+M.SwapTotal):"sin swap"],
["Bateria",B.level?B.level+"% · "+(SB[B.status]||"?")+" · salud "+(HB[B.health]||B.health||"?")+(B.temperature?" · "+(B.temperature/10).toFixed(1)+" °C":"")+(cy?" · "+cy+" ciclos":""):""],
["Almacenamiento",df?mb(+df[2])+" usados de "+mb(+df[1]):""],
["Encendido hace",up?Math.floor(up/3600)+" h "+Math.floor(up%3600/60)+" min":""]
];
devI.innerHTML="";
for(const[k,v]of rows){if(!v)continue;const t=document.createElement("dt");t.textContent=k;const d=document.createElement("dd");d.textContent=v;devI.append(t,d)}
await shot();
}
phImg.parentElement.addEventListener("click",()=>{if(A1)shot().catch(e=>setSt("Error captura: "+e.message))});

let FP1="/sdcard";
async function flLoad(p){
FP1=p;flPath.textContent=p;ov("Leyendo carpeta...");
try{
const es=(await syncDo(sy=>sy.readdir(p))).filter(e=>e.name!=="."&&e.name!=="..");
es.sort((a,b)=>((b.type===4)-(a.type===4))||a.name.localeCompare(b.name));
flList.innerHTML="";
if(!es.length)flList.textContent="Carpeta vacia";
for(const e of es){
const dir=e.type===4||e.type===10,fp=(p==="/"?"":p)+"/"+e.name;
const dt=new Date(Number(e.mtime)*1000).toLocaleDateString();
flList.appendChild(mkRow({ic:dir?"📁":"📄",t:e.name,de:dir?"Carpeta · "+dt:mb(Math.round(Number(e.size)/1024))+" · "+dt,
go:()=>dir?flLoad(fp):flGet(fp,e.name),
b:[["Borrar","🗑️",true,async()=>{if(!confirm("Borrar "+fp+"?"))return;await runSh("rm -rf "+q1(fp));await flLoad(p)}]]}));
}
}catch(e){setSt("Error archivos: "+e.message)}
ov("");
}
async function flGet(fp,n){ov("Descargando "+n+"...");try{dl(await syncDo(sy=>rdB(sy.read(fp))),n)}catch(e){setSt("Error: "+e.message)}ov("")}
el("adbFlUp").addEventListener("click",()=>{if(A1&&FP1!=="/")flLoad(FP1.replace(/\/[^/]+$/,"")||"/")});
el("adbFlPut").addEventListener("click",()=>{if(A1)flIn.click()});
flIn.addEventListener("change",async()=>{
for(const f of[...flIn.files]){ov("Subiendo "+f.name+"...");try{await push1(A1,(FP1==="/"?"":FP1)+"/"+f.name.replace(/\//g,"_"),new Uint8Array(await f.arrayBuffer()))}catch(e){setSt("Error: "+e.message)}}
flIn.value="";ov("");flLoad(FP1);
});

async function secLoad(){
ov("Revisando...");secList.innerHTML="";
try{
const g=secs(await runSh("echo @A;settings get secure enabled_accessibility_services;echo @D;dumpsys device_policy 2>/dev/null;echo @U;cmd appops query-op GET_USAGE_STATS allow 2>&1"),"A|D|U");
const ac=[...new Set((g.A||[]).join(":").split(":").map(x=>x.trim().split("/")[0]).filter(x=>PKR1.test(x)&&x.includes(".")))];
const dt=(g.D||[]).join("\n"),dv=new Set();
for(const m of dt.matchAll(/^\s+([A-Za-z0-9._]+)\/[\w.$]+:\s*$/gm))dv.add(m[1]);
for(const m of dt.matchAll(/ComponentInfo\{([A-Za-z0-9._]+)\//g))dv.add(m[1]);
const ut=(g.U||[]).map(x=>x.trim()).filter(Boolean),us=ut.some(x=>!PKR1.test(x))?null:ut;
const SG=[["♿ Accesibilidad activa","Pueden leer todo lo que aparece en pantalla y tocar por vos.",ac],["🛡️ Administradores del dispositivo","Pueden bloquear o borrar el telefono y evitar que se desinstalen.",[...dv]],["📊 Acceso a datos de uso","Ven que apps usas y cuanto tiempo.",us]];
for(const[t,de,ls]of SG){
const det=document.createElement("details");det.open=true;
const sm=document.createElement("summary");sm.textContent=t+" ("+(ls?ls.length:"?")+")";det.appendChild(sm);
const p=document.createElement("p");p.style.cssText="font-size:.85em;opacity:.8";p.textContent=ls?(ls.length?de+" Si no reconoces alguna, revisala.":"Ninguna."):"No disponible en esta version de Android.";det.appendChild(p);
for(const id of ls||[]){const it=itOf(id);det.appendChild(mkRow({ic:"📦",t:id,de:it.description||"",go:()=>cfOpen(it),b:[["Configurar","⚙️",true,()=>cfOpen(it)]]}))}
secList.appendChild(det);
}
}catch(e){setSt("Error revision: "+e.message)}
ov("");
}
el("adbSecRe").addEventListener("click",()=>{if(A1)secLoad()});

let curView="store";
function setView(v){
if(curView==="scr"&&v!=="scr")scrStop();
curView=v;
storeEl.style.display=v==="store"?"":"none";
lstEl.style.display=v==="apps"?"":"none";
flEl.style.display=v==="fl"?"":"none";
secEl.style.display=v==="sec"?"":"none";
cmdPnl.style.display=v==="cmd"?"":"none";
scrPnl.style.display=v==="scr"?"":"none";
if(v==="apps")scanAll();
if(v==="fl")flLoad(FP1);
if(v==="sec")secLoad();
}
for(const[b,v]of[[btnApps,"apps"],[btnFl,"fl"],[btnSec,"sec"]])b.addEventListener("click",()=>{if(A1)setView(curView===v?"store":v)});

function pkgIdFromUrl(u){
const m=u.match(/\/packages\/([^/?#]+)/);
return m?m[1]:null;
}

function mkStoreCard(app){
const a=document.createElement("a");
a.className="BMD1";a.href="#";
const img=document.createElement("img");
img.src=app.icon;img.alt=app.name;img.loading="lazy";img.decoding="async";
const cn=document.createElement("div");cn.className="BMD1-CN";
const h=document.createElement("h3");h.textContent=app.name;
const p=document.createElement("p");p.textContent=app.summary||"";
cn.appendChild(h);cn.appendChild(p);
a.appendChild(img);a.appendChild(cn);
let busy=false;
a.addEventListener("click",async ev=>{
ev.preventDefault();
if(busy)return;
if(!A1){p.textContent="Conecta el telefono primero";setTimeout(()=>p.textContent=app.summary||"",2500);return}
busy=true;
p.textContent="Obteniendo version...";
try{
const rp=await fetch(FN1+"?action=pkg&id="+encodeURIComponent(app.pkg));
const dp=await rp.json();
const vc=dp.suggestedVersionCode;
if(!vc)throw new Error("sin version disponible");
p.textContent="Descargando...";
const rd=await fetch(FN1+"?action=apk&pkg="+encodeURIComponent(app.pkg)+"&vc="+encodeURIComponent(vc));
if(!rd.ok)throw new Error("HTTP "+rd.status);
const buf=await rd.arrayBuffer();
p.textContent="Instalando...";
await pushInstall(new Uint8Array(buf));
p.textContent="Instalado";
}catch(e){
p.textContent="Error: "+e.message;
console.error(e);
}finally{
busy=false;
setTimeout(()=>p.textContent=app.summary||"",2000);
}
});
return a;
}

let SW=null,gfP=null;
const GF1=()=>window.GridFit?Promise.resolve(window.GridFit):gfP||(gfP=new Promise(r=>{const s=document.createElement("script");s.src="web/js/lib/GridFit.js";s.onload=s.onerror=()=>r(window.GridFit);document.head.appendChild(s)}));
function storeNav(){
if(!window.GridFit){GF1().then(g=>{if(g)storeNav()});return}
if(!SW){SW=GridFit.SW1(gridEl,{n:()=>Math.ceil(stCur.length/20),p:()=>stPg,go:i=>{stPg=i;renderStorePage(0,1)},
fill:(el,i)=>stCur.slice(i*20,i*20+20).forEach(app=>{const c=mkStoreCard(app);c.querySelector("img").loading="eager";el.appendChild(c)})});SW.pre()}
GridFit.PN1(pgEl,stPg,Math.ceil(stCur.length/20),i=>{const d=i>stPg?1:-1;stPg=i;renderStorePage(d);gridEl.scrollIntoView({behavior:"smooth",block:"start"})});
}
function renderStorePage(dir,sw){
gridEl.innerHTML="";
const s=stPg*20,slice=stCur.slice(s,s+20);
slice.forEach(app=>gridEl.appendChild(mkStoreCard(app)));
if(stCur.length>20){
pgEl.style.display="";
storeNav();
}else pgEl.style.display="none";
if(sw)return;
if(SW)SW.pre();
gridEl.style.setProperty("--d",dir?(dir>0?"24px":"-24px"):"0px");
gridEl.classList.remove("AN1");void gridEl.offsetWidth;gridEl.classList.add("AN1");
}


async function doStoreSearch(){
const q=searchInp.value.trim();
if(!q){stCur=[];stPg=0;renderStorePage();return}
if(stAC)stAC.abort();
stAC=new AbortController();
try{
const r=await fetch(FN1+"?action=search&q="+encodeURIComponent(q),{signal:stAC.signal});
const d=await r.json();
stCur=(d.apps||[]).map(app=>({name:app.name,summary:app.summary,icon:app.icon,pkg:pkgIdFromUrl(app.url)})).filter(a=>a.pkg);
stPg=0;renderStorePage();
}catch(e){
if(e.name==="AbortError")return;
gridEl.innerHTML="<p>Error al buscar apps 😔</p>";
}
}

searchInp.addEventListener("input",()=>{
clearTimeout(stDbt);
stDbt=setTimeout(doStoreSearch,5000);
});

searchInp.addEventListener("keydown",ev=>{
if(ev.key!=="Enter")return;
clearTimeout(stDbt);
doStoreSearch();
});

async function push1(a,path,bytes){
const sync=await a.sync();
try{
await sync.write({filename:path,file:new ReadableStream({start(c){c.enqueue(bytes);c.close()}})});
}finally{
await sync.dispose();
}
}

async function pushInstall(bytes){
const tmp="/data/local/tmp/_i.apk";
await push1(A1,tmp,bytes);
const out=await runSh("pm install "+tmp);
await runSh("rm "+tmp);
if(!/Success/.test(out))throw new Error(out.trim()||"pm install");
}

async function pushSplit(ps){
const c=await runSh("pm install-create -S "+ps.reduce((a,x)=>a+x.length,0));
const sid=(c.match(/\[(\d+)\]/)||[])[1];
if(!sid)throw new Error(c.trim()||"pm install-create");
try{
for(let i=0;i<ps.length;i++){
const f="/data/local/tmp/_s"+i+".apk";
await push1(A1,f,ps[i]);
const w=await runSh("pm install-write -S "+ps[i].length+" "+sid+" s"+i+" "+f);
await runSh("rm "+f);
if(!/Success/.test(w))throw new Error(w.trim()||"pm install-write");
}
const r=await runSh("pm install-commit "+sid);
if(!/Success/.test(r))throw new Error(r.trim()||"pm install-commit");
}catch(e){runSh("pm install-abandon "+sid).catch(()=>{});throw e}
}
async function apkParts(fs){
const ab=(abi1||"").replace(/-/g,"_"),ps=[];
for(const f of fs){
if(/\.apkm$/i.test(f.name))throw new Error(f.name+": APKM viene cifrado, no se puede instalar aca");
if(/\.apk$/i.test(f.name)){ps.push(new Uint8Array(await f.arrayBuffer()));continue}
const z=await zjs(),zr=new z.ZipReader(new z.BlobReader(f));
for(const e of await zr.getEntries()){
const n=e.filename;
if(/^Android\/obb\/[A-Za-z0-9._]+\/[^/]+\.obb$/.test(n)&&!n.includes("..")){setSt("Copiando "+n+"...");await push1(A1,"/sdcard/"+n,await e.getData(new z.Uint8ArrayWriter()));continue}
if(!/\.apk$/i.test(n)||/standalone/i.test(n))continue;
const am=n.match(/(arm64_v8a|armeabi_v7a|armeabi|x86_64|x86)\.apk$/);
if(am&&ab&&am[1]!==ab)continue;
ps.push(await e.getData(new z.Uint8ArrayWriter()));
}
await zr.close();
}
return ps;
}
fileInp.addEventListener("change",async()=>{
const fs=[...fileInp.files];
fileInp.value="";
if(!fs.length)return;
const n=fs.map(f=>f.name).join(", ");
setSt("Instalando "+n+"...");ov("Instalando...");
try{
const ps=await apkParts(fs);
if(!ps.length)throw new Error("no hay APK adentro");
if(ps.length===1)await pushInstall(ps[0]);else await pushSplit(ps);
setSt("Instalado: "+n);
}catch(e){
setSt("Error al instalar: "+e.message);
console.error(e);
}
ov("");
});

function cmdLogLn(s){cmdLog.textContent+=s+"\n";cmdLog.scrollTop=cmdLog.scrollHeight}

async function cmdExec(cmd){
if(!A1){cmdLogLn("! No hay dispositivo conectado");return}
cmdLogLn("$ "+cmd);
try{
const out=await runSh(cmd);
cmdLogLn(out.trim()||"(sin salida)");
}catch(e){
cmdLogLn("Error: "+e.message);
}
}

function renderCmdGrid(){
cmdGrid.innerHTML="";
for(const it of CMDS1){
const b=document.createElement("button");
b.textContent=it.n;
b.style.cssText="background:rgba(255,255,255,.09);border:1px solid rgba(255,255,255,.14);border-radius:10px;color:#fff;padding:6px 14px;cursor:pointer;font-size:.85em;font-family:inherit";
b.addEventListener("click",()=>cmdExec(it.c));
cmdGrid.appendChild(b);
}
}
renderCmdGrid();

cmdRun.addEventListener("click",()=>{
const v=cmdInp.value.trim();
if(!v)return;
cmdExec(v);
cmdInp.value="";
});
cmdInp.addEventListener("keydown",ev=>{
if(ev.key==="Enter")cmdRun.click();
});

btnCmd.addEventListener("click",()=>{
if(!A1)return;
setView(curView==="cmd"?"store":"cmd");
});

let scrCli=null,scrDec=null,scrVw=0,scrVh=0;

async function scrStart(){
scrSt.textContent="Descargando servidor...";
scrHold.innerHTML="";
try{
const rs=await fetch(SRVJ1);
if(!rs.ok)throw new Error("HTTP "+rs.status+" al obtener jar");
scrSt.textContent="Subiendo servidor al dispositivo...";
await AdbScrcpyClient.pushServer(A1,rs.body);
scrSt.textContent="Iniciando scrcpy...";
scrCli=await AdbScrcpyClient.start(A1,DefaultServerPath,new AdbScrcpyOptions3_3_3({control:true,audio:false,video:true,videoBitRate:4000000,maxSize:720},{version:"3.3.4"}));
let rend;
if(WebGLVideoFrameRenderer.isSupported)rend=new WebGLVideoFrameRenderer();
else rend=new BitmapVideoFrameRenderer();
scrHold.appendChild(rend.canvas);
rend.canvas.style.maxWidth="100%";rend.canvas.style.touchAction="none";rend.canvas.style.display="block";
if(!scrCli.videoStream){scrSt.textContent="Servidor sin video";return}
const{metadata,stream}=await scrCli.videoStream;
scrDec=new WebCodecsVideoDecoder({codec:metadata.codec,renderer:rend});
scrDec.sizeChanged(({width,height})=>{scrVw=width;scrVh=height});
stream.pipeTo(scrDec.writable).catch(e=>console.error(e));
scrHold.addEventListener("pointerdown",scrPtr);
scrHold.addEventListener("pointermove",scrPtr);
scrHold.addEventListener("pointerup",scrPtr);
scrHold.addEventListener("pointercancel",scrPtr);
scrSt.textContent=scrCli.controller?"Conectado":"Solo ver: sin control";
}catch(e){
if(e?.output){
scrSt.textContent="Error servidor: "+e.message;
console.error("scrcpy server output:",e.output.join("\n"));
}else{
scrSt.textContent="Error: "+e.message;
}
console.error(e);
}
}

const BTN1=[1,4,2,8,16];
async function scrPtr(ev){
ev.preventDefault();
if(!scrCli||!scrCli.controller||!scrVw)return;
const ms=ev.pointerType==="mouse";
let act;
if(ev.type==="pointerdown"){act=AndroidMotionEventAction.Down;try{scrHold.setPointerCapture(ev.pointerId)}catch(e){}}
else if(ev.type==="pointermove"){if(ev.buttons===0&&!ms)return;act=ev.buttons===0?AndroidMotionEventAction.HoverMove:AndroidMotionEventAction.Move}
else act=AndroidMotionEventAction.Up;
const cv=scrHold.querySelector("canvas")||scrHold,rc=cv.getBoundingClientRect();
const px=clamp((ev.clientX-rc.x)/rc.width,0,1)*scrVw;
const py=clamp((ev.clientY-rc.y)/rc.height,0,1)*scrVh;
const ab=act===AndroidMotionEventAction.Down||act===AndroidMotionEventAction.Up?(BTN1[ev.button]||AndroidMotionEventButton.Primary):0;
const bs=ms?ev.buttons:(act===AndroidMotionEventAction.Up?0:AndroidMotionEventButton.Primary);
try{
await scrCli.controller.injectTouch({
action:act,pointerId:ms?ScrcpyPointerId.Mouse:BigInt(ev.pointerId),
pointerX:px,pointerY:py,videoWidth:scrVw,videoHeight:scrVh,
pressure:act===AndroidMotionEventAction.Up||ev.buttons===0?0:1,actionButton:ab,buttons:bs
});
}catch(e){scrSt.textContent="Error control: "+e.message}
}

async function scrStop(){
scrHold.removeEventListener("pointerdown",scrPtr);
scrHold.removeEventListener("pointermove",scrPtr);
scrHold.removeEventListener("pointerup",scrPtr);
scrHold.removeEventListener("pointercancel",scrPtr);
if(scrCli){try{await scrCli.close()}catch(e){} scrCli=null}
scrDec?.dispose();scrDec=null;scrVw=0;scrVh=0;
scrHold.innerHTML="";
scrSt.textContent="Presiona Pantalla para iniciar";
}

btnScr.addEventListener("click",()=>{
if(!A1)return;
if(curView==="scr"){setView("store");return}
setView("scr");
scrStart();
});

async function onCnn(){
try{
setSt("Selecciona el dispositivo en el menu que aparece...");
const mgr=AdbDaemonWebUsbDeviceManager.BROWSER;
if(!mgr){setSt("WebUSB no disponible en este navegador.");return}
const dv=await mgr.requestDevice();
if(!dv){setSt("No elegiste ningun dispositivo.");return}
const cn=await dv.connect();
setSt("Autenticando (revisa el telefono si pide confirmar)...");
const tr=await AdbDaemonTransport.authenticate({serial:dv.serial,connection:cn,credentialStore:CS1});
const a=new Adb(tr);
A1=a;
a.disconnected.then(()=>{
if(A1!==a)return;
setView("store");
A1=null;
for(const b of [btnApps,btnFl,btnSec,btnCmd,btnScr]){b.style.opacity=".5";b.style.pointerEvents="none"}
if(cfDlg.open)cfDlg.close();
devEl.style.display="none";
howTo.style.display="";
setSt("Telefono desconectado.");
});
abi1=(await runSh("getprop ro.product.cpu.abi")).trim();
for(const b of [btnApps,btnFl,btnSec,btnCmd,btnScr])enable(b);
howTo.style.display="none";
setSt("Listo. Conectado: "+(A1.banner?.model||dv.serial)+" ("+abi1+")");
if(!searchInp.value.trim()){searchInp.value="document";doStoreSearch()}
devLoad().catch(e=>setSt("Error info: "+e.message));
}catch(e){
setSt("Error: "+e.message);
console.error(e);
}
}

const RPARTS1=["system","system_root","vendor","vendor_dlkm","odm","odm_dlkm","product","system_ext"];
const RCAND1=["/build.prop","/system/build.prop","/default.prop"];
async function runShR(cmd){return await AR1.subprocess.noneProtocol.spawnWaitText(cmd)}
const SL1=ms=>new Promise(r=>setTimeout(r,ms));
const repFmt=el("adbRepFmt"),repDfeIn=el("adbRepDfe"),repDfeN=el("adbRepDfeN");
let repDfe=null;
el("adbBtnRepDfe").addEventListener("click",()=>repDfeIn.click());
repDfeIn.addEventListener("change",()=>{repDfe=repDfeIn.files[0]||null;repDfeN.textContent=repDfe?repDfe.name:""});

async function repScan(){
const bl=(await runShR("ls /dev/block/mapper 2>/dev/null | grep -v control || ls /dev/block/by-name 2>/dev/null || ls /dev/block/bootdevice/by-name 2>/dev/null")).split(/\s+/).filter(Boolean).join(" ");
const out=await runShR("for p in "+RPARTS1.join(" ")+"; do [ -d /$p ] || continue; twrp mount /$p >/dev/null 2>&1; mount /$p >/dev/null 2>&1; mount -o rw,remount /$p >/dev/null 2>&1; m=$(grep \" /$p \" /proc/mounts | head -n1); if [ -z \"$m\" ]; then echo \"P $p no\"; elif echo \"$m\" | grep -q ' rw,'; then echo \"P $p rw\"; else echo \"P $p ro\"; fi; done");
const pt=[...out.matchAll(/^P (\S+) (\S+)\s*$/gm)].map(m=>({p:m[1],s:m[2]}));
const fl=[];
for(const x of pt){
if(x.s!=="rw")continue;
for(const c of RCAND1){
const path="/"+x.p+c;
if((await runShR("[ -f "+path+" ] && echo si || echo no")).trim()==="si")fl.push(path);
}
}
return{bl,pt,fl};
}

async function pubKeyLine(){
for await(const k of CS1.iterateKeys()){
const pub=adbGeneratePublicKey(k.buffer);
const b64=btoa(String.fromCharCode(...pub));
return b64+" "+k.name;
}
const nk=await CS1.generateKey();
const pub=adbGeneratePublicKey(nk.buffer);
const b64=btoa(String.fromCharCode(...pub));
return b64+" "+nk.name;
}

function resetRepUi(){
repStep1.style.display="";
repStep2.style.display="none";
repStep3.style.display="none";
repMsg.textContent="";
btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";
btnRepRun.style.pointerEvents="";btnRepRun.style.opacity="";
repFmt.checked=false;repDfe=null;repDfeIn.value="";repDfeN.textContent="";
}

function openRep(){resetRepUi();dOpen(repDlg)}
function closeRep(){repDlg.close()}

btnRep.addEventListener("click",openRep);
btnRepClose.addEventListener("click",closeRep);

btnRepTest.addEventListener("click",async()=>{
btnRepTest.style.pointerEvents="none";btnRepTest.style.opacity=".5";
repMsg.textContent="Conectando...";
try{
const mgr=AdbDaemonWebUsbDeviceManager.BROWSER;
if(!mgr){repMsg.textContent="WebUSB no disponible en este navegador.";btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";return}
const dv=await mgr.requestDevice();
if(!dv){repMsg.textContent="No se selecciono ningun dispositivo.";btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";return}
const cn=await dv.connect();
const tr=await AdbDaemonTransport.authenticate({serial:dv.serial,connection:cn,credentialStore:CS1});
AR1=new Adb(tr);

repMsg.textContent="Probando comando twrp...";
const out=await runShR("twrp 2>&1; echo EXIT:$?");
const low=out.toLowerCase();

if(low.includes("not appear to be running")||low.includes("waiting for twrp")){
repMsg.textContent="TWRP no responde, presiona 'Probar conexion' de nuevo.";
btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";
return;
}
if(low.includes("inaccessible")||low.includes("not found")||low.includes("no such file")||low.includes("unknown command")){
repMsg.textContent="El comando 'twrp' no existe en este recovery. Esto solo funciona con TWRP u otro custom recovery compatible, no con el recovery de fabrica.";
btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";
return;
}

repMsg.textContent="TWRP respondio correctamente. Montando particiones...";
const sc=await repScan();
repStep1.style.display="none";
repStep2.style.display="";
repPlan.textContent="Particiones: "+(sc.bl||"?")+
"\nMontadas: "+(sc.pt.map(x=>x.p+" ("+x.s+")").join(", ")||"ninguna")+
"\nArchivos a modificar: "+(sc.fl.join(", ")||"ninguno, se usara /default.prop")+
"\n\nSe copiara tu clave ADB publica y se habilitara ADB inseguro en las particiones de sistema disponibles. Al finalizar el telefono se reiniciara a Android normal, de esta manera poder usar scrcpy para poder controlar el dispositivo con el boton pantalla que encontraras en el menu.";
}catch(e){
repMsg.textContent="Error de conexion: "+e.message;
btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";
console.error(e);
}
});

btnRepRun.addEventListener("click",async()=>{
if(repFmt.checked&&!confirm("Formatear data borra TODO el telefono. Continuar?"))return;
btnRepRun.style.pointerEvents="none";btnRepRun.style.opacity=".5";
const done=[];
try{
if(repFmt.checked){
repPlan.textContent="Formateando data...";
await Promise.race([runShR("twrp format data"),SL1(120000)]);
done.push("data formateada");
}
if(repDfe){
repPlan.textContent="Instalando "+repDfe.name+"...";
await push1(AR1,"/tmp/DFE.zip",new Uint8Array(await repDfe.arrayBuffer()));
await Promise.race([runShR("twrp install /tmp/DFE.zip"),SL1(120000)]);
done.push("DFE instalado");
}
repPlan.textContent="Ejecutando...";
const key=await pubKeyLine();
const keySafe=key.replace(/'/g,"'\\''");
await runShR("twrp mount /data >/dev/null 2>&1; mount /data >/dev/null 2>&1; mkdir -p /data/misc/adb");
await runShR("echo '"+keySafe+"' > /data/misc/adb/adb_keys");
await runShR("chmod 600 /data/misc/adb/adb_keys");
await runShR("chown 2000:2000 /data/misc/adb/adb_keys");
done.push("/data/misc/adb/adb_keys (clave copiada)");

const sc=await repScan();
const found=sc.fl.length>0;
for(const path of sc.fl){
done.push(path);
await runShR("grep -q '^ro.adb.secure=' "+path+" && sed -i 's/^ro.adb.secure=.*/ro.adb.secure=0/' "+path+" || echo 'ro.adb.secure=0' >> "+path);
await runShR("grep -q '^persist.sys.usb.config=' "+path+" && sed -i 's/^persist.sys.usb.config=.*/persist.sys.usb.config=adb/' "+path+" || echo 'persist.sys.usb.config=adb' >> "+path);
}
if(!found){
await runShR("echo 'ro.adb.secure=0' >> /default.prop");
await runShR("echo 'persist.sys.usb.config=adb' >> /default.prop");
done.push("/default.prop (fallback)");
}

repStep2.style.display="none";
repStep3.style.display="";
repDone.textContent="Reiniciando a Android...";
try{await runShR("reboot")}catch(e2){console.error("reboot corto la conexion (normal):",e2)}
repDone.innerHTML="Listo. Archivos modificados: "+done.join(", ")+
"<br><br>Ahora Esperar a que el Telefono inicie para poder controlar el telefono con "+
'<a href="https://github.com/Genymobile/scrcpy/releases" target="_blank">scrcpy</a> desde el Boton Pantalla Aqui. Recuerda Conectar el Telefono.';
}catch(e){
repPlan.textContent="Error durante la reparacion: "+e.message;
btnRepRun.style.pointerEvents="";btnRepRun.style.opacity="";
console.error(e);
}
});

btnCnn.addEventListener("click",onCnn);

document.getElementById("content").addEventListener("contentUnload",function cu(){
if(A1)A1.close?.().catch(()=>{});
if(AR1)AR1.close?.().catch(()=>{});
if(scrCli)scrCli.close?.().catch(()=>{});
if(repDlg.open)repDlg.close();
if(cfDlg.open)cfDlg.close();
document.body.style.overflow="";
if(phImg.src)URL.revokeObjectURL(phImg.src);
if(stAC)stAC.abort();
document.getElementById("content").removeEventListener("contentUnload",cu);
},{once:true});

stOv.style.display="none";
setSt("Presiona Conectar para vincular tu telefono.");
}catch(e){
stOv.style.display="none";
setSt("Error al iniciar: "+e.message);
console.error(e);
}
})();
</script>