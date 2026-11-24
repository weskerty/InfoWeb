<style>
.GA1{text-align:left}
.GA1 [hidden]{display:none!important}
.GA_H{margin:0 0 14px}
.GA_L{display:grid;gap:12px;align-items:start}
.GA1 .GA_NV{display:grid;gap:6px;padding:10px;border:1px solid var(--RD_L);border-radius:16px;box-shadow:var(--RD_SH)}
.GA1 .GA_NV button{display:flex;align-items:center;justify-content:flex-start;gap:10px;width:100%;min-height:42px;padding:0 12px;border-radius:10px;font:500 .92rem var(--font);white-space:nowrap}
.GA_NV b{font-weight:400;font-size:1.2rem;line-height:1}
.GA1 button:disabled{opacity:.4;cursor:default}
.GA_M{position:relative;min-width:0;min-height:340px;padding:16px;border:1px solid var(--RD_L);border-radius:16px;box-shadow:var(--RD_SH)}
.GA1 .GA_ST{margin:0 0 14px;padding:8px 12px;border-radius:10px;background:var(--RD_M);color:var(--RD_F2);font-size:.88rem;line-height:1.4;overflow-wrap:anywhere}
.GA1 .GA_TX{margin:0 0 12px;color:var(--RD_MF);font-size:.9rem;line-height:1.5}
.GA1 h3{margin:18px 0 10px;font-size:1.05rem}
.GA1 section>h3:first-child{margin-top:0}
.GA_TB{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin:0 0 12px}
.GA_TB input{flex:1 1 160px;min-width:0}
.GA_PR{margin:0 0 14px;padding:10px 12px;border:1px solid var(--RD_L);border-radius:12px}
.GA1 .GA_PR p{margin:0;font-size:.85rem;line-height:1.4;color:var(--RD_F2);overflow-wrap:anywhere}
.GA_PB{height:8px;margin:8px 0;border-radius:4px;background:var(--RD_M);overflow:hidden}
.GA_PB>i{display:block;height:100%;width:0;background:var(--ok);transition:width .3s}
.GA_HE{display:flex;flex-direction:column;align-items:center;gap:12px;padding:10px 0 18px;text-align:center}
.GA_HE>b{font-size:3rem;font-weight:400;line-height:1}
.GA1 .GA_HE p{margin:0}
#adbDev{display:flex;gap:16px;align-items:flex-start;flex-wrap:wrap;justify-content:center;margin:0 0 14px}
.adbPh{width:130px;flex-shrink:0;border:3px solid rgba(255,255,255,.35);border-radius:20px;padding:8px 4px 12px;background:#000;cursor:pointer}
.adbPh::before{content:'';display:block;width:34px;height:4px;border-radius:2px;background:rgba(255,255,255,.3);margin:0 auto 6px}
.adbPh img{width:100%;min-height:200px;display:block;border-radius:6px;background:#111}
#adbDevI{flex:1;min-width:190px;display:grid;grid-template-columns:auto 1fr;gap:4px 10px;font-size:.85em;margin:0}
#adbDevI dt{opacity:.65}
#adbDevI dd{margin:0}
.GA_AC{justify-content:center}
.adbAp::before{content:none}
.adbAp{cursor:pointer}
.adbAp.off{opacity:.55}
.adbAp-i{width:58px;height:58px;display:flex;align-items:center;justify-content:center;font-size:1.7rem;background:rgba(0,0,0,.25);flex-shrink:0}
.BMD1>img.adbAp-i{padding:8px;object-fit:contain}
.adbAp .BMD1-CN{padding-right:8px}
.GA1 .BMD1-CN p{font-size:.82rem;line-height:1.4;color:var(--RD_MF)}
.GA1 .BMD1-CN .GA_DS{display:-webkit-box;-webkit-box-orient:vertical;-webkit-line-clamp:2;overflow:hidden}
.GA1 .BMD1-CN .adbAp-s{font-size:.76rem;color:var(--RD_F2)}
.adbAp-b{display:flex;gap:6px;padding-right:10px;flex-shrink:0}
.adbAp-b button{min-width:38px;height:38px;padding:0 6px}
.adbOp{display:flex;align-items:center;justify-content:space-between;gap:10px;padding:6px 0;border-bottom:1px solid var(--RD_L);font-size:.85em;word-break:break-all}
.GA_CH{display:flex;align-items:center;gap:12px;margin:0 44px 10px 0}
.GA_CH img{width:52px;height:52px;flex:none}
.GA1 .GA_CH h3,.GA1 .GA_CH p{margin:0;word-break:break-all}
.GA_CR{display:flex;flex-wrap:wrap;align-items:center;gap:2px;margin:0 0 8px;font-size:.88rem;color:var(--RD_MF)}
.GA_CB{min-height:32px;padding:4px 8px;border:0;border-radius:8px;background:none;color:var(--RD_F2);font:inherit;cursor:pointer}
@media(hover:hover){.GA_CB:hover{background:var(--RD_M)}}
.GA_FL{border:1px solid var(--RD_L);border-radius:14px;overflow:hidden}
.GA_FR{display:flex;align-items:center;gap:10px;min-height:48px;padding:6px 12px;border-bottom:1px solid var(--RD_L);cursor:pointer}
.GA_FR:last-child{border-bottom:0}
@media(hover:hover){.GA_FR:hover{background:var(--RD_M)}}
.GA_FR.on{background:var(--RD_BS)}
.GA_FL.dr{outline:2px dashed var(--ok);outline-offset:-4px}
.GA_CK{width:20px;height:20px;margin:0;flex:none;accent-color:var(--ok)}
.GA_FI{flex:none;width:28px;text-align:center;font-size:1.25rem}
.GA_FN{flex:1;min-width:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.GA_FM{flex:none;color:var(--RD_MF);font-size:.76rem;text-align:right}
.GA1 .GA_FV{margin:0;padding:18px;text-align:center}
.GA_FL>button{display:block;width:100%;border:0;border-radius:0}
.GA_FA{position:sticky;bottom:8px;z-index:4;display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-top:10px;padding:10px;border:1px solid var(--RD_L);border-radius:16px;background:var(--RD_DG);box-shadow:0 8px 30px rgba(0,0,0,.4)}
.GA_FA span{flex:1 1 100%;color:var(--RD_MF);font-size:.82rem}
.GA_FA i{font-style:normal}
@media(max-width:480px){.GA_FA i{display:none}.GA_FA button{flex:1 1 0;min-width:0;padding-inline:0}}
.GA_BK{display:grid;gap:8px;margin:0 0 14px}
.GA_BK>label,.GA_BK>div{display:flex;align-items:center;gap:12px;padding:10px 12px;border:1px solid var(--RD_L);border-radius:14px}
.GA_BK>label{cursor:pointer}
.GA_BK span{flex:1;min-width:0}
.GA_BK b{display:block;font-weight:500}
.GA_BK small{display:block;color:var(--RD_MF);font-size:.78rem;overflow-wrap:anywhere}
.GA_SC{text-align:center}
.GA_KB{justify-content:center}
#adbScrHold{display:inline-block;max-width:100%;outline:none;touch-action:none}
#adbScrHold canvas{display:block;max-width:100%;max-height:75vh;touch-action:none;border-radius:10px}
#adbScrHold:focus-visible canvas{outline:2px solid var(--ok)}
.GA_KF{margin-top:12px}
.GA_LG{height:240px;margin:0 0 10px;padding:10px 12px;overflow-y:auto;border:1px solid var(--RD_L);border-radius:10px;background:rgba(0,0,0,.35);font-size:.8em;white-space:pre-wrap;word-break:break-all}
.GA_PVM{text-align:center}
.GA_PVM :is(img,video){display:block;max-width:100%;max-height:60vh;margin:0 auto 12px;border-radius:10px}
.GA_PVM audio{width:100%;margin:0 0 12px}
.GA_PVM .GA_LG{text-align:left}
.GA_SD{width:min(360px,calc(100vw - 32px))}
.GA_RBL{display:grid;gap:8px}
#adbStOv{position:absolute;inset:0;z-index:50;display:none;flex-direction:column;align-items:center;justify-content:center;gap:14px;backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);background:rgba(0,0,0,.25);border-radius:inherit}
body.low-perf #adbStOv{backdrop-filter:none;background:var(--rdm-bg)}
#adbStOv img{width:56px;height:56px}
#adbStOv span{color:#fff;font-size:.95em}
@media(orientation:landscape){.GA_L{grid-template-columns:168px minmax(0,1fr)}.GA1 .GA_NV{position:sticky;top:12px}}
@media(orientation:portrait){.GA1 .GA_NV{grid-template-columns:repeat(4,minmax(0,1fr));padding:8px}.GA1 .GA_NV button{flex-direction:column;justify-content:center;gap:4px;min-height:60px;padding:6px 2px;font-size:.72rem}.GA_M{padding:14px 12px}.GA_FA{margin-right:30px}}
</style>
<div class="GA1" id="GA1">
<h2 class="NB_TT GA_H">💚 Gestor Android</h2>
<div class="GA_L">
<nav class="GA_NV" id="GA_NV" aria-label="Secciones">
<button type="button" data-v="ini" aria-pressed="true"><b>🏠</b>Inicio</button>
<button type="button" data-v="apps" aria-pressed="false" disabled><b>📱</b>Apps</button>
<button type="button" data-v="fl" aria-pressed="false" disabled><b>📁</b>Archivos</button>
<button type="button" data-v="bk" aria-pressed="false" disabled><b>💾</b>Copias</button>
<button type="button" data-v="scr" aria-pressed="false" disabled><b>🖥️</b>Pantalla</button>
<button type="button" data-v="tda" aria-pressed="false"><b>🛒</b>Tienda</button>
<button type="button" data-v="sec" aria-pressed="false" disabled><b>🕵️</b>Anti espia</button>
<button type="button" data-v="cmd" aria-pressed="false" disabled><b>📟</b>Comandos</button>
</nav>
<div class="GA_M" id="GA_M">
<p id="adbSt" class="GA_ST" role="status">Iniciando...</p>
<div id="GA_PR" class="GA_PR" hidden><p id="GA_PRT"></p><div class="GA_PB"><i id="GA_PRB"></i></div><button type="button" id="GA_PRX">✖️ Cancelar</button></div>
<section id="GA_ini">
<div id="GA_D0">
<div class="GA_HE"><b>🔌</b><p>Conecta tu Android con un cable USB</p><button type="button" id="adbBtnCnn" class="RD_B1 GL_C">🔌 Conectar</button></div>
<details id="adbHowTo"><summary>Como activar ADB</summary>
<ol>
<li>Ajustes &gt; Acerca del telefono: toca 7 veces "Numero de compilacion".</li>
<li>Ajustes &gt; Sistema &gt; Opciones de desarrollador: activa "Depuracion USB".</li>
<li>Conecta el cable y toca Conectar.</li>
<li>En el telefono acepta "Permitir depuracion USB" (marca Permitir siempre).</li>
</ol>
</details>
<p class="GA_TX">Pantalla rota con TWRP instalado: <button type="button" id="adbBtnRep">🩹 Reparar acceso</button></p>
</div>
<div id="GA_D1" hidden>
<div id="adbDev"><div class="adbPh" title="Actualizar captura"><img id="adbPhImg" alt="Pantalla del telefono"></div><dl id="adbDevI"></dl></div>
<div class="GA_TB GA_AC"><button type="button" id="GA_DR">🔄 Actualizar</button><button type="button" id="GA_RBB">🔁 Reiniciar</button><button type="button" id="GA_DX">⏏️ Desconectar</button></div>
</div>
</section>
<section id="GA_apps" hidden>
<div class="GA_TB"><input id="GA_AQ" type="search" placeholder="Filtrar apps" aria-label="Filtrar apps" autocomplete="off"><button type="button" id="adbApIns">📥 Instalar APK</button><button type="button" id="adbApScan">🔄 Escanear</button></div>
<div id="adbApList"></div>
</section>
<section id="GA_fl" hidden>
<div class="BS1" id="GA_QP"></div>
<div class="GA_CR" id="GA_CR"></div>
<div class="GA_FL" id="adbFlList"></div>
<div class="GA_FA"><span id="GA_FC"></span><button type="button" id="GA_FD" aria-label="Descargar" disabled>⬇️<i> Descargar</i></button><button type="button" id="GA_FE" aria-label="Renombrar" disabled>✏️<i> Renombrar</i></button><button type="button" id="GA_FB" aria-label="Borrar" disabled>🗑️<i> Borrar</i></button><button type="button" id="GA_FK" aria-label="Nueva carpeta">📁<i> Nueva carpeta</i></button><button type="button" id="adbFlPut" aria-label="Subir">📤<i> Subir</i></button></div>
<input type="file" id="adbFlIn" multiple hidden>
</section>
<section id="GA_bk" hidden>
<h3>💾 Guardar copia</h3>
<p class="GA_TX" id="GA_BKT">Se guarda en una carpeta de tu PC. Si repetis la copia en la misma carpeta, solo se suma lo nuevo.</p>
<div class="GA_BK" id="GA_BKL"></div>
<button type="button" id="GA_BKG" class="RD_B1 GL_C">💾 Elegir carpeta y copiar</button>
<h3>♻️ Restaurar</h3>
<p class="GA_TX">Elegi la carpeta de una copia o sus archivos sueltos (.vcf, SMS.xml, Llamadas.xml, WiFi.json, .apk). Tambien sirven los .xml de SMS Backup &amp; Restore.</p>
<button type="button" id="GA_RSE" class="RD_B1">📂 Elegir copia</button>
<input type="file" id="GA_RSF" multiple accept=".vcf,.xml,.json,.apk,.apks" hidden>
<div class="GA_BK" id="GA_RSL"></div>
</section>
<section id="GA_scr" class="GA_SC" hidden>
<div class="GA_TB GA_KB"><button type="button" id="GA_SS">⏹️ Detener</button><button type="button" data-k="4">◀️ Atras</button><button type="button" data-k="3">🏠 Inicio</button><button type="button" data-k="187">🗂️ Recientes</button><button type="button" data-k="25" aria-label="Bajar volumen">🔉</button><button type="button" data-k="24" aria-label="Subir volumen">🔊</button><button type="button" data-k="26" aria-label="Boton de encendido">🔒</button></div>
<p id="adbScrSt" class="GA_TX">Presiona Iniciar</p>
<div id="adbScrHold" tabindex="0" aria-label="Pantalla del telefono"></div>
<form class="GA_TB GA_KF" id="GA_KF"><input id="GA_KT" type="text" placeholder="Escribir en el telefono" aria-label="Texto para el telefono" autocomplete="off" enterkeyhint="send"><button>⌨️ Enviar</button></form>
</section>
<section id="GA_tda" hidden>
<form class="GA_TB" id="GA_SF"><input id="adbSearchInp" type="search" placeholder="Buscar apps en F-Droid" aria-label="Buscar apps" autocomplete="off" enterkeyhint="search"><button aria-label="Buscar">🔍</button></form>
<div id="adbStoreGrid"></div>
<div id="adbStorePg" class="PG1"></div>
</section>
<section id="GA_sec" hidden>
<div class="GA_TB"><button type="button" id="adbSecRe">🔄 Revisar de nuevo</button></div>
<div id="adbSecList"></div>
</section>
<section id="GA_cmd" hidden>
<div class="GA_TB" id="adbCmdGrid"></div>
<pre id="adbCmdLog" class="GA_LG"></pre>
<form class="GA_TB" id="GA_CF"><input id="adbCmdInp" type="text" placeholder="comando adb shell..." aria-label="Comando" autocomplete="off" spellcheck="false"><button>Ejecutar</button></form>
</section>
<div id="adbStOv"><img id="adbStOvImg" alt=""><span>Iniciando...</span></div>
</div>
</div>
<input type="file" id="adbFileApk" accept=".apk,.apks,.xapk,.apkm,.zip" multiple hidden>
<dialog id="adbCfDlg" class="DX1"><button data-x="1" aria-label="Cerrar">✕</button><div id="adbCf"></div></dialog>
<dialog id="GA_PV" class="DX1"><button data-x="1" aria-label="Cerrar">✕</button><div class="GA_CH"><h3 id="GA_PVN"></h3></div><p id="GA_PVI" class="GA_TX"></p><div id="GA_PVM" class="GA_PVM"></div><div class="GA_TB"><button type="button" id="GA_PVD">⬇️ Descargar</button><button type="button" id="GA_PVB">🗑️ Borrar</button></div></dialog>
<dialog id="GA_RB" class="DX1 GA_SD"><button data-x="1" aria-label="Cerrar">✕</button><h3>🔁 Reiniciar</h3><div class="GA_RBL"><button type="button" data-r="">📱 Android</button><button type="button" data-r="recovery">🛟 Recovery</button><button type="button" data-r="bootloader">⚙️ Bootloader</button><button type="button" data-r="-p">📴 Apagar</button></div></dialog>
<dialog id="adbRepDlg" class="DX1">
<button data-x="1" aria-label="Cerrar">✕</button>
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
</div>

<script>
(async()=>{
const CMDS1=[
{n:"Info bateria",c:"dumpsys battery"},
{n:"Espacio libre",c:"df -h /data"},
{n:"Reiniciar",c:"reboot"},
{n:"Anti-Kill Termux",c:"device_config set_sync_disabled_for_tests persistent;device_config put activity_manager max_phantom_processes 2147483647;device_config put runtime_native_boot use_freezer false;settings put global settings_enable_monitor_phantom_procs false;am set-inactive com.termux false;cmd deviceidle whitelist +com.termux;cmd power set-mode 0;dumpsys deviceidle disable;cmd appops set --uid com.termux RUN_IN_BACKGROUND allow;cmd appops set --uid com.termux RUN_ANY_IN_BACKGROUND allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_ACTIVITY_BG_START_RESTRICTION allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_HIBERNATION allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_POWER_RESTRICTIONS allow;cmd appops set --uid com.termux SYSTEM_EXEMPT_FROM_SUSPENSION allow;cmd appops set --uid com.termux WAKE_LOCK allow;cmd appops set --uid com.termux REQUEST_IGNORE_BATTERY_OPTIMIZATIONS allow;cmd appops set --uid com.termux ACTIVATE_PLATFORM_VPN allow;cmd appops set --uid com.termux INTERACT_ACROSS_PROFILES allow;cmd appops set --uid com.termux SCHEDULE_EXACT_ALARM allow;cmd appops set --uid com.termux START_FOREGROUND allow;echo listo anti-kill"}
];
const $=id=>document.getElementById(id);
const CT=$("content"),stOv=$("adbStOv"),stEl=$("adbSt"),wa=window.__CFG?.waitAnim;
const DLG=[...$("GA1").querySelectorAll("dialog")],HM=new Map();
let GONE=0,A1=null,AR1=null,scrCli=null,scrDec=null,stAC=null,BK_X=0,BK_R=0,PVU=null,CSL=null;
function setSt(s){stEl.textContent=s}
if(wa){$("adbStOvImg").src=wa;stOv.style.display="flex"}
CT.addEventListener("contentUnload",()=>{
GONE=1;BK_X=1;
if(CSL)document.removeEventListener("contentState",CSL);
for(const d of DLG)if(d.open)d.close();
if(A1)A1.close?.().catch(()=>{});
if(AR1)AR1.close?.().catch(()=>{});
if(scrCli)scrCli.close?.().catch(()=>{});
scrDec?.dispose?.();
const im=$("adbPhImg");if(im.src.startsWith("blob:"))URL.revokeObjectURL(im.src);
if(PVU)URL.revokeObjectURL(PVU);
if(stAC)stAC.abort();
document.body.style.overflow="";
},{once:true});
try{
const{AdbDaemonTransport,Adb,adbGeneratePublicKey,AdbDaemonWebUsbDeviceManager,AdbWebCredentialStore,DefaultServerPath,AndroidMotionEventAction,AndroidMotionEventButton,AndroidKeyEventAction,ScrcpyPointerId,clamp,AdbScrcpyClient,AdbScrcpyOptions3_3_3,WebCodecsVideoDecoder,WebGLVideoFrameRenderer,BitmapVideoFrameRenderer}=await import("/web/js/lib/Tango/tango.mjs");
if(GONE)return;

const U1="https://raw.githubusercontent.com/Universal-Debloater-Alliance/universal-android-debloater-next-generation/main/resources/assets/uad_lists.json";
const R1=["Recommended","Advanced","Expert","Unsafe"];
const PR1=["com.android.systemui","com.android.settings","com.android.phone","com.android.shell","android"];
const FN1="/api/fdroid",SRVJ1="web/js/lib/Binarios/scrcpy-server-v3.3.4",JR1="web/js/lib/Binarios/ga1.jar",JP1="/data/local/tmp/ga1.jar";
const PKR1=/^[A-Za-z0-9._]+$/,OPR1=/^[A-Z][A-Z0-9_]*$/;
const CN1={Recommended:"Recomendado",Advanced:"Avanzado",Expert:"Experto",Unsafe:"Inseguro",Unlisted:"Sin listar"};
const NC1=new Set(["apps","fl","bk","scr","sec","cmd"]);
const FSA=!!window.showDirectoryPicker;
const CS1=new AdbWebCredentialStore("WebADBDebloater");
let D1=null,abi1="",SDK1=0,MD1="",SC1=null,CF1=null,ZJ1=null,LB1=null,JOK=null,VC1="ini",FP1="/sdcard",FE1=[],FT1=0,FL_N=300,PVE=null,RS1=null;
let stCur=[],stPg=0,stDbt=null;
const OP1=new Set(["Recommended"]),FS1=new Set();

const SL1=ms=>new Promise(r=>setTimeout(r,ms));
function ov(t){if(!wa)return;stOv.querySelector("span").textContent=t||"";stOv.style.display=t?"flex":"none"}
function mb(k){return k>=1048576?(k/1048576).toFixed(1)+" GB":k>=1024?Math.round(k/1024)+" MB":Math.round(k)+" KB"}
function mbB(b){return mb(b/1024)}
function oomL(o){return o<0?"Sistema":o===0?"Al frente":o<900?"Segundo plano":"En cache"}
function q1(x){return"'"+String(x).replace(/'/g,"'\\''")+"'"}
function FN0(s){return String(s).replace(/[\\/:*?"<>|\x00-\x1f]/g,"_").trim()||"_"}
function dl(b,n){const u=URL.createObjectURL(b),a=document.createElement("a");a.href=u;a.download=n;a.click();setTimeout(()=>URL.revokeObjectURL(u),15000)}
async function rdB(st){const r=st.getReader(),c=[];for(;;){const{done,value}=await r.read();if(done)break;c.push(value)}return new Blob(c)}
async function syncDo(f){const sy=await A1.sync();try{return await f(sy)}finally{await sy.dispose()}}
function zjs(){return ZJ1||(ZJ1=import("https://cdn.jsdelivr.net/npm/@zip.js/zip.js@2.24.0/+esm"))}
function secs(o,ks){const sec={};let cur=null;const re=new RegExp("^@("+ks+")\\s*$");for(const ln of o.split("\n")){const m=ln.match(re);if(m){cur=m[1];sec[cur]=[];continue}if(cur)sec[cur].push(ln)}return sec}
async function runSh(cmd){return await A1.subprocess.noneProtocol.spawnWaitText(cmd)}
function parsePkgs(txt){const a=[];for(const ln of txt.split("\n")){const m=ln.match(/^package:(\S+)/);if(m)a.push(m[1])}return a}
function icU(i){return i?"data:image/webp;base64,"+i:""}
async function push1(a,path,bytes){const sy=await a.sync();try{await sy.write({filename:path,file:new ReadableStream({start(c){c.enqueue(bytes);c.close()}})})}finally{await sy.dispose()}}
async function wrF(d,n,x){const w=await(await d.getFileHandle(n,{create:true})).createWritable();try{await w.write(x);await w.close()}catch(e){await w.abort().catch(()=>{});throw e}}
async function fhEx(d,n){try{await d.getFileHandle(n);return true}catch(e){return false}}
async function jsRd(d,n){try{return JSON.parse(await(await(await d.getFileHandle(n)).getFile()).text())}catch(e){return null}}

async function jar(a,on){
const ad=A1;
if(JOK!==ad){const r=await fetch(JR1);if(!r.ok)throw new Error("HTTP "+r.status);await push1(ad,JP1,new Uint8Array(await r.arrayBuffer()));JOK=ad}
const p=await ad.subprocess.noneProtocol.spawn("CLASSPATH="+JP1+" app_process / ga.M "+a);
const rd=p.output.getReader(),td=new TextDecoder();let b="",er="";
const ln=s=>{s=s.trim();if(s[0]!=="{")return;let o;try{o=JSON.parse(s)}catch(e){return}if(o.e)er=o.e;else if(!o.ok&&on)on(o)};
for(;;){const{done,value}=await rd.read();if(done)break;b+=td.decode(value,{stream:true});let i;while((i=b.indexOf("\n"))>=0){ln(b.slice(0,i));b=b.slice(i+1)}}
ln(b+td.decode());
if(er)throw new Error(er);
}

const prEl=$("GA_PR"),prT=$("GA_PRT"),prB=$("GA_PRB");let prL=0;
function pr(t,f,fz){const n=Date.now();if(!fz&&n-prL<150)return;prL=n;prT.textContent=t;if(f!=null)prB.style.width=Math.min(100,f*100).toFixed(1)+"%"}
$("GA_PRX").addEventListener("click",()=>{BK_X=1;pr("Cancelando...",null,1)});
async function job(f){
if(BK_R){setSt("Espera que termine la tarea en curso.");return}
BK_R=1;BK_X=0;prT.textContent="";prB.style.width="0";prEl.hidden=false;
try{const r=await f();setSt(BK_X?"Cancelado.":r||"Listo.")}catch(e){setSt(BK_X?"Cancelado.":"Error: "+e.message);console.error(e)}
BK_R=0;prEl.hidden=true;
}

const NV=$("GA_NV"),VW={};
for(const b of NV.querySelectorAll("button"))VW[b.dataset.v]=$("GA_"+b.dataset.v);
function go(v,p,h){
if(NC1.has(v)&&!A1)v="ini";
const ch=v!==VC1,fp=v==="fl"&&p&&p!==FP1;
if(h&&(ch||fp))window.__HS3?.("GV",{v,p:v==="fl"?p||FP1:null});
if(VC1==="scr"&&ch)scrStop();
VC1=v;
for(const k in VW)VW[k].hidden=k!==v;
for(const b of NV.querySelectorAll("button"))b.setAttribute("aria-pressed",String(b.dataset.v===v));
if(ch&&$("GA_M").getBoundingClientRect().top<0)$("GA_M").scrollIntoView({block:"start"});
if(v==="apps"&&ch)scanAll();
if(v==="fl"&&(ch||fp))flLoad(p||FP1);
if(v==="sec"&&ch)secLoad();
if(v==="scr"&&ch)scrStart();
if(v==="tda"&&ch&&!stCur.length&&!searchInp.value.trim()){searchInp.value="document";doStoreSearch()}
}
NV.addEventListener("click",e=>{const b=e.target.closest("button");if(b&&!b.disabled)go(b.dataset.v,null,1)});
CSL=e=>{const s=e.detail||{},d=HM.get(s.GA);for(const x of DLG)if(x.open&&x!==d)x.close();const g=s.GV;go(g?g.v:"ini",g?g.p:null,0)};
document.addEventListener("contentState",CSL);
function dOpen(d){if(!d.open){d.showModal();const t=Math.random();HM.set(t,d);window.__HS3?.("GA",t)}document.body.style.overflow="hidden"}
for(const d of DLG){d.addEventListener("close",()=>{document.body.style.overflow="";if(!GONE&&HM.get(history.state?.GA)===d)history.back()});d.querySelector("[data-x]")?.addEventListener("click",()=>d.close())}
function cnUi(on){for(const b of NV.querySelectorAll("button"))if(NC1.has(b.dataset.v))b.disabled=!on;$("GA_D0").hidden=on;$("GA_D1").hidden=!on}

function mkRow(o){
const d=document.createElement("div");d.className="BMD1 adbAp"+(o.off?" off":"");d.tabIndex=0;d.setAttribute("role","button");
let ic;if(o.im){ic=document.createElement("img");ic.src=o.im;ic.alt=""}else{ic=document.createElement("span");ic.textContent=o.ic}ic.className="adbAp-i";
const cn=document.createElement("div");cn.className="BMD1-CN";
const h=document.createElement("h3");h.textContent=o.t;cn.appendChild(h);
for(const[k,c]of[["de",""],["ds","GA_DS"],["st","adbAp-s"]])if(o[k]){const x=document.createElement("p");if(c)x.className=c;x.textContent=o[k];cn.appendChild(x)}
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

const apList=$("adbApList"),aq=$("GA_AQ"),cfDlg=$("adbCfDlg"),cf=$("adbCf"),fileInp=$("adbFileApk");
$("adbApScan").addEventListener("click",()=>{if(A1)scanAll()});
$("adbApIns").addEventListener("click",()=>{if(A1)fileInp.click()});
aq.addEventListener("input",()=>renderApps());
async function uninst(id){return await runSh("pm uninstall --user 0 "+id)}
async function restr(id){return await runSh("cmd package install-existing "+id)}

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
const[,all,ins,dis,pr2]=await Promise.all([
D1?null:fetch(U1).then(r=>{if(!r.ok)throw new Error("HTTP "+r.status);return r.json()}).then(j=>{D1=j}),
runSh("pm list packages -u"),runSh("pm list packages"),runSh("pm list packages -d"),scanProc()
]);
const on=new Set(parsePkgs(ins)),ds=new Set(parsePkgs(dis));
SC1={};
for(const id of parsePkgs(all).filter(x=>PKR1.test(x))){const l=LB1&&LB1.get(id);SC1[id]={id,...(D1[id]||{}),p:pr2.P[id]||null,sz:pr2.Z[id]||0,on:on.has(id),dis:ds.has(id),n:l?l.n:"",ic:l?l.i:""}}
renderApps();
setSt(Object.keys(SC1).length+" paquetes, "+Object.values(SC1).filter(x=>x.p&&x.on).length+" abiertos.");
}catch(e){
setSt("Error al escanear: "+e.message);
console.error(e);
}
ov("");
icLoad();
}

async function icLoad(){
if(LB1||!A1)return;
const a=A1;LB1=new Map();
try{
await jar("apps",o=>{if(A1!==a||!PKR1.test(o.p||""))return;LB1.set(o.p,o);const it=SC1&&SC1[o.p];if(it){it.n=o.n||"";it.ic=o.i||"";if(it.el&&it.el.isConnected)upd(it)}});
if(A1!==a)return;
if(VC1==="apps")renderApps();
if(VC1==="sec")secLoad();
}catch(e){if(A1===a){LB1=null;setSt("Error Iconos: "+e.message)}}
}

function itOf(id){const it=SC1&&SC1[id]||{id,...(D1&&D1[id]||{}),p:null,sz:0,on:true,dis:false};const l=LB1&&LB1.get(id);if(l&&!it.n){it.n=l.n||"";it.ic=l.i||""}return it}
function stTx(it){
if(!it.on)return"Desinstalada";
const p=it.p,a=[];
if(it.dis)a.push("Deshabilitada");
if(p)a.push("🧠 "+mb(p.r)+(p.s?" · 🔄 "+mb(p.s):"")+" · ⚡ "+Math.round(p.c)+"% · "+oomL(p.o));
if(it.sz)a.push("💾 "+mb(it.sz));
if(PR1.includes(it.id))a.push("Desinstalar esto bloquearia el telefono: solo a mano desde Comandos.");
return a.join(" · ");
}
function upd(it){if(it.el&&it.el.isConnected)it.el.replaceWith(it.el=mkAp(it));if(cfDlg.open&&CF1===it)cfDraw()}

async function togDis(it){
const o=(await runSh(it.dis?"pm enable "+it.id:"pm disable-user --user 0 "+it.id)).trim();
if(!/new state/i.test(o))throw new Error(o||"sin respuesta");
it.dis=!it.dis;upd(it);
}

function mkAp(it){
const lk=!it.on||PR1.includes(it.id);
return mkRow({im:icU(it.ic),ic:"📦",t:it.n||it.id,de:it.n&&it.n!==it.id?it.id:"",ds:it.description||"",st:stTx(it),off:!it.on||it.dis,go:()=>cfOpen(it),
b:[["Configurar","⚙️",true,()=>cfOpen(it)],[it.dis?"Habilitar":"Deshabilitar",it.dis?"✅":"⛔",!lk,()=>togDis(it)]]});
}

function renderApps(){
if(!SC1)return;
const q=aq.value.trim().toLowerCase(),g={};for(const k in CN1)g[k]=[];
for(const it of Object.values(SC1)){if(q&&!it.id.toLowerCase().includes(q)&&!(it.n||"").toLowerCase().includes(q))continue;g[it.removal&&R1.includes(it.removal)?it.removal:"Unlisted"].push(it)}
const sc=it=>it.p?it.p.r+it.p.s:-1;
apList.replaceChildren();
let tot=0;
for(const k in CN1){
const its=g[k];if(!its.length)continue;tot+=its.length;
its.sort((a,b)=>sc(b)-sc(a)||(b.p?b.p.c:0)-(a.p?a.p.c:0)||(a.n||a.id).localeCompare(b.n||b.id));
const det=document.createElement("details");det.open=q?true:OP1.has(k);
det.addEventListener("toggle",()=>{if(!aq.value.trim())det.open?OP1.add(k):OP1.delete(k)});
const sm=document.createElement("summary");const nr=its.filter(x=>x.p&&x.on).length;
sm.textContent=CN1[k]+" ("+its.length+(nr?", "+nr+" abiertas":"")+")";
det.appendChild(sm);
for(const it of its)det.appendChild(it.el=mkAp(it));
apList.appendChild(det);
if(k==="Recommended"&&!q){const bq=document.createElement("blockquote");const p=document.createElement("p");p.textContent="Desinstalar alguna aplicacion de abajo puede causar problemas. Recuerda leer la descripcion de cada app. Sigue bajo tu responsabilidad.";bq.appendChild(p);apList.appendChild(bq)}
}
if(!tot){const p=document.createElement("p");p.className="GA_TX";p.textContent="Sin resultados";apList.appendChild(p)}
}

function cfOpen(it){CF1=it;cfDraw();dOpen(cfDlg)}
function cfDraw(){
const it=CF1,id=it.id,lk=PR1.includes(id);
cf.replaceChildren();
const mk=(t,x,c)=>{const e=document.createElement(t);if(x)e.textContent=x;if(c)e.style.cssText=c;cf.appendChild(e);return e};
const hd=mk("div");hd.className="GA_CH";
if(it.ic){const im=document.createElement("img");im.src=icU(it.ic);im.alt="";hd.appendChild(im)}
const ht=document.createElement("div"),h=document.createElement("h3");h.textContent=it.n||id;ht.appendChild(h);
if(it.n&&it.n!==id){const p=document.createElement("p");p.className="GA_TX";p.textContent=id;ht.appendChild(p)}
hd.appendChild(ht);
const st=stTx(it);if(st)mk("p",st,"font-size:.85em;opacity:.85");
mk("p",it.description||"(sin descripcion en la base UAD)","white-space:pre-wrap");
if(it.removal||it.list)mk("p","Lista UAD: "+[it.removal&&CN1[it.removal],it.list].filter(Boolean).join(" · "),"font-size:.8em;opacity:.6");
const row=mk("div");row.className="GA_TB";
const ms=document.createElement("p");ms.style.cssText="font-size:.85em;opacity:.85";
const bt=(t,ok,f)=>{const b=document.createElement("button");b.textContent=t;b.disabled=!ok;b.addEventListener("click",async()=>{b.disabled=true;ms.textContent="";try{await f()}catch(e){ms.textContent="Error: "+e.message}b.disabled=false});row.appendChild(b)};
bt("▶️ Abrir",it.on&&!it.dis,async()=>{const o=await runSh("monkey -p "+id+" -c android.intent.category.LAUNCHER 1");ms.textContent=/Events injected: 1/.test(o)?"Abierta en el telefono":o.trim().split("\n").pop()});
bt("🗑️ Desinstalar",it.on&&!lk,async()=>{
if(!confirm("Desinstalar "+(it.n||id)+" para el usuario actual? Se puede Reinstalar con el Boton Restaurar."))return;
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

async function apksZip(ps){const z=await zjs(),w=new z.ZipWriter(new z.BlobWriter("application/zip"));await syncDo(async sy=>{for(const x of ps)await w.add(x.split("/").pop(),new z.BlobReader(await rdB(sy.read(x))))});return await w.close()}
async function bkApk(id){
const ps=parsePkgs(await runSh("pm path "+id));
if(!ps.length)throw new Error("sin APK");
if(ps.length===1)dl(await syncDo(sy=>rdB(sy.read(ps[0]))),id+".apk");
else dl(await apksZip(ps),id+".apks");
}

const devI=$("adbDevI"),phImg=$("adbPhImg");
async function shot(){
await runSh("screencap -p /data/local/tmp/_sc.png");
const b=await syncDo(sy=>rdB(sy.read("/data/local/tmp/_sc.png")));
runSh("rm /data/local/tmp/_sc.png").catch(()=>{});
if(phImg.src.startsWith("blob:"))URL.revokeObjectURL(phImg.src);
phImg.src=URL.createObjectURL(new Blob([b],{type:"image/png"}));
}
async function devLoad(){
const g=secs(await runSh("echo @P;for k in ro.product.manufacturer ro.product.model ro.build.version.release ro.build.version.sdk ro.build.version.security_patch ro.boot.flash.locked ro.boot.verifiedbootstate ro.product.cpu.abi;do echo \"$k=$(getprop $k)\";done;echo @M;cat /proc/meminfo;echo @B;dumpsys battery;echo @C;cat /sys/class/power_supply/battery/cycle_count 2>/dev/null;echo @D;df -k /data 2>/dev/null;echo @U;cat /proc/uptime"),"P|M|B|C|D|U");
const kv=(a,re)=>{const o={};for(const l of a||[]){const m=l.trim().match(re);if(m)o[m[1]]=m[2].trim()}return o};
const P=kv(g.P,/^([\w.]+)=(.*)$/),M=kv(g.M,/^(\w+):\s+(\d+)/),B=kv(g.B,/^([\w ]+):\s*(.+)$/);
const df=(g.D||[]).map(l=>l.trim().split(/\s+/)).find(x=>x.length>=6&&/^\d+$/.test(x[1]));
const up=parseFloat((g.U||[])[0])||0,cy=((g.C||[])[0]||"").trim();
const HB={"1":"desconocida","2":"buena","3":"recalentada","4":"agotada","5":"sobretension","6":"falla","7":"fria"},SB={"2":"cargando","3":"descargando","4":"sin cargar","5":"llena"};
const bl=P["ro.boot.flash.locked"],vb=P["ro.boot.verifiedbootstate"];
MD1=[P["ro.product.manufacturer"],P["ro.product.model"]].filter(Boolean).join(" ");
const rows=[
["Modelo",MD1],
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
devI.replaceChildren();
for(const[k,v]of rows){if(!v)continue;const t=document.createElement("dt");t.textContent=k;const d=document.createElement("dd");d.textContent=v;devI.append(t,d)}
await shot();
}
phImg.parentElement.addEventListener("click",()=>{if(A1)shot().catch(e=>setSt("Error captura: "+e.message))});
$("GA_DR").addEventListener("click",()=>{if(A1)devLoad().catch(e=>setSt("Error Info: "+e.message))});
$("GA_DX").addEventListener("click",()=>{if(A1)A1.close().catch(()=>{})});
$("GA_RBB").addEventListener("click",()=>{if(A1)dOpen($("GA_RB"))});
for(const b of $("GA_RB").querySelectorAll("[data-r]"))b.addEventListener("click",()=>{$("GA_RB").close();if(A1&&confirm(b.textContent.trim()+"?"))runSh("reboot "+b.dataset.r).catch(()=>{})});

const flList=$("adbFlList"),flIn=$("adbFlIn"),crEl=$("GA_CR"),qpEl=$("GA_QP");
const QP1=[["📱","Interno","/sdcard"],["📷","Camara","/sdcard/DCIM"],["⬇️","Descargas","/sdcard/Download"],["🟢","WhatsApp","/sdcard/Android/media/com.whatsapp/WhatsApp"],["🗂️","Raiz","/"]];
for(const[i,t,p]of QP1){const b=document.createElement("button");b.type="button";b.className="BS2";b.dataset.p=p;b.textContent=i+" "+t;b.addEventListener("click",()=>go("fl",p,1));qpEl.appendChild(b)}
const EX1={img:/^(jpe?g|png|gif|webp|bmp|avif|heic|heif)$/,vid:/^(mp4|mkv|webm|3gp|mov|m4v)$/,aud:/^(mp3|m4a|ogg|opus|wav|flac|aac|amr)$/,txt:/^(txt|log|json|xml|csv|md|vcf|ini|conf|prop)$/};
const MT1={jpg:"image/jpeg",jpeg:"image/jpeg",png:"image/png",gif:"image/gif",webp:"image/webp",bmp:"image/bmp",avif:"image/avif",mp4:"video/mp4",m4v:"video/mp4",webm:"video/webm",mkv:"video/x-matroska",mov:"video/quicktime","3gp":"video/3gpp",mp3:"audio/mpeg",m4a:"audio/mp4",ogg:"audio/ogg",opus:"audio/ogg",wav:"audio/wav",flac:"audio/flac",aac:"audio/aac",amr:"audio/amr"};
function jp(d,n){return(d==="/"?"":d)+"/"+n}
function isD(e){return e.type===4||e.type===10}
function ext(n){return n.includes(".")?n.split(".").pop().toLowerCase():""}
function ftIc(e){if(isD(e))return"📁";const x=ext(e.name);return EX1.img.test(x)?"🖼️":EX1.vid.test(x)?"🎬":EX1.aud.test(x)?"🎵":/^(apk|apks|xapk|apkm)$/.test(x)?"📦":/^(zip|rar|7z|tar|gz|tgz)$/.test(x)?"🗜️":"📄"}
async function flLoad(p){
const tk=++FT1;FP1=p;FS1.clear();FL_N=300;ov("Leyendo carpeta...");
let es=[];
try{es=(await syncDo(sy=>sy.readdir(p))).filter(e=>e.name!=="."&&e.name!=="..");es.sort((a,b)=>(isD(b)-isD(a))||a.name.localeCompare(b.name))}
catch(e){setSt("Error Archivos: "+e.message)}
if(tk!==FT1)return;
FE1=es;flDraw();ov("");
}
function flCrumb(){
crEl.replaceChildren();
const add=(t,p)=>{const b=document.createElement("button");b.type="button";b.className="GA_CB";b.textContent=t;b.addEventListener("click",()=>go("fl",p,1));crEl.appendChild(b)};
add("🗂️","/");
const ps=FP1.split("/").filter(Boolean);
ps.forEach((s,i)=>{const sp=document.createElement("span");sp.textContent="›";crEl.appendChild(sp);add(s,"/"+ps.slice(0,i+1).join("/"))});
for(const b of qpEl.children)b.setAttribute("aria-pressed",String(b.dataset.p===FP1));
}
function flDraw(){
flCrumb();flList.replaceChildren();
if(!FE1.length){const p=document.createElement("p");p.className="GA_TX GA_FV";p.textContent="Carpeta vacia";flList.appendChild(p)}
for(const e of FE1.slice(0,FL_N)){
const fp=jp(FP1,e.name),r=document.createElement("div");r.className="GA_FR"+(FS1.has(e.name)?" on":"");r.tabIndex=0;r.setAttribute("role","button");
const ck=document.createElement("input");ck.type="checkbox";ck.className="GA_CK";ck.checked=FS1.has(e.name);ck.setAttribute("aria-label","Elegir "+e.name);
ck.addEventListener("click",ev=>ev.stopPropagation());
ck.addEventListener("change",()=>{ck.checked?FS1.add(e.name):FS1.delete(e.name);r.classList.toggle("on",ck.checked);flSel()});
const ic=document.createElement("span");ic.className="GA_FI";ic.textContent=ftIc(e);
const nm=document.createElement("span");nm.className="GA_FN";nm.textContent=e.name;
const mt=document.createElement("span");mt.className="GA_FM";const dt=new Date(Number(e.mtime)*1000).toLocaleDateString();mt.textContent=isD(e)?dt:mbB(Number(e.size))+" · "+dt;
r.append(ck,ic,nm,mt);
const op=()=>isD(e)?go("fl",fp,1):pvOpen(e,fp);
r.addEventListener("click",op);r.addEventListener("keydown",ev=>{if(ev.key==="Enter"&&ev.target===r)op()});
flList.appendChild(r);
}
if(FE1.length>FL_N){const b=document.createElement("button");b.type="button";b.textContent="Mostrar mas ("+(FE1.length-FL_N)+")";b.addEventListener("click",()=>{FL_N+=300;flDraw()});flList.appendChild(b)}
flSel();
}
function flSel(){const n=FS1.size;$("GA_FC").textContent=n?n+(n>1?" elegidos":" elegido"):FE1.length+" elementos · toca para abrir, marca para elegir";$("GA_FD").disabled=!n;$("GA_FB").disabled=!n;$("GA_FE").disabled=n!==1}
async function pvOpen(e,fp){
PVE={e,fp};pvClr();
$("GA_PVN").textContent=e.name;$("GA_PVI").textContent=mbB(Number(e.size))+" · "+new Date(Number(e.mtime)*1000).toLocaleString()+" · "+fp;
dOpen($("GA_PV"));
const x=ext(e.name),z=Number(e.size),k=EX1.img.test(x)?"img":EX1.vid.test(x)?"video":EX1.aud.test(x)?"audio":EX1.txt.test(x)?"pre":"";
if(!k||z>{img:30,video:150,audio:60,pre:1}[k]*1048576)return;
const pm=$("GA_PVM"),p=document.createElement("p");p.className="GA_TX";p.textContent="Cargando...";pm.appendChild(p);
try{
const b=await syncDo(sy=>rdB(sy.read(fp)));
if(PVE?.fp!==fp||!$("GA_PV").open)return;
pm.replaceChildren();
if(k==="pre"){const t=document.createElement("pre");t.className="GA_LG";t.textContent=await b.text();pm.appendChild(t);return}
PVU=URL.createObjectURL(new Blob([b],{type:MT1[x]||""}));
const m=document.createElement(k);m.src=PVU;if(k==="img")m.alt=e.name;else m.controls=true;pm.appendChild(m);
}catch(er){p.textContent="Error: "+er.message}
}
function pvClr(){$("GA_PVM").replaceChildren();if(PVU){URL.revokeObjectURL(PVU);PVU=null}}
$("GA_PV").addEventListener("close",()=>{pvClr();PVE=null});
$("GA_PVD").addEventListener("click",()=>{const v=PVE;if(v&&A1)job(()=>saveOne(v.fp,v.e.name,Number(v.e.size)))});
$("GA_PVB").addEventListener("click",async()=>{const v=PVE;if(!v||!A1||!confirm("Borrar "+v.fp+"?"))return;$("GA_PV").close();ov("Borrando...");try{await runSh("rm -rf "+q1(v.fp))}catch(e){setSt("Error: "+e.message)}flLoad(FP1)});

async function cpTo(sy,src,fh,pf){
const w=await fh.createWritable();let ok=0;
try{
const r=sy.read(src).getReader();let n=0;
try{for(;;){if(BK_X)throw new Error("Cancelado");const{done,value}=await r.read();if(done)break;await w.write(value);n+=value.length;pf&&pf(n)}}
catch(e){r.cancel().catch(()=>{});throw e}
await w.close();ok=1;
}finally{if(!ok)await w.abort().catch(()=>{})}
}
async function saveOne(fp,n,z){
if(window.showSaveFilePicker){
let fh;try{fh=await showSaveFilePicker({suggestedName:n})}catch(e){if(e.name==="AbortError")return"Cancelado.";throw e}
await syncDo(sy=>cpTo(sy,fp,fh,v=>pr("⬇️ "+n+" · "+mbB(v)+" de "+mbB(z),z?v/z:null)));
return"Guardado: "+n;
}
pr("⬇️ "+n,null,1);dl(await syncDo(sy=>rdB(sy.read(fp))),n);return"Descargado: "+n;
}
async function walk(sy,p,rel,L){
let es;try{es=await sy.readdir(p)}catch(e){return}
for(const e of es){
if(BK_X)return;if(e.name==="."||e.name==="..")continue;
const fp=p+"/"+e.name,r=rel+"/"+e.name;
if(e.type===4)await walk(sy,fp,r,L);else if(e.type===8)L.push({s:fp,r,z:Number(e.size),m:Number(e.mtime)});
}
}
async function cpList(L,dir,mf,lb){
const tot=L.reduce((a,x)=>a+x.z,0),DC=new Map();let done=0,n=0,sk=0,er=0,i=0;
const gd=async r=>{let d=dir,k="";for(const s of r.split("/").slice(0,-1)){k+="/"+s;let h=DC.get(k);if(!h){h=await d.getDirectoryHandle(FN0(s),{create:true});DC.set(k,h)}d=h}return d};
let sy=await A1.sync();
try{
for(const x of L){
if(BK_X||!A1)break;i++;
const nm=FN0(x.r.split("/").pop()),tx=v=>(lb?lb+" · ":"")+i+"/"+L.length+" · "+mbB(done+v)+" de "+mbB(tot)+" · "+nm;
if(mf)mf[x.r]=x.m;
try{
const d=await gd(x.r);
let f=null;try{f=await(await d.getFileHandle(nm)).getFile()}catch(e){}
if(f&&f.size===x.z){sk++;done+=x.z;pr(tx(0),tot?done/tot:i/L.length);continue}
await cpTo(sy,x.s,await d.getFileHandle(nm,{create:true}),v=>pr(tx(v),tot?(done+v)/tot:i/L.length));
n++;
}catch(e){if(BK_X)break;er++;await sy.dispose().catch(()=>{});sy=await A1.sync()}
done+=x.z;
}
}finally{await sy.dispose().catch(()=>{})}
return n+" copiados"+(sk?", "+sk+" ya estaban":"")+(er?", "+er+" con error":"");
}
async function flDown(){
const sel=FE1.filter(e=>FS1.has(e.name));
if(!sel.length)return"";
if(sel.length===1&&!isD(sel[0]))return saveOne(jp(FP1,sel[0].name),sel[0].name,Number(sel[0].size));
if(!FSA){let n=0;for(const e of sel){if(BK_X)break;if(isD(e))continue;pr("⬇️ "+e.name,null,1);dl(await syncDo(sy=>rdB(sy.read(jp(FP1,e.name)))),e.name);n++}return n+" descargados (las carpetas necesitan Chrome o Edge en PC)"}
let dh;try{dh=await showDirectoryPicker({id:"ga1",mode:"readwrite"})}catch(e){if(e.name==="AbortError")return"Cancelado.";throw e}
const L=[];pr("Buscando archivos...",null,1);
await syncDo(async sy=>{for(const e of sel){const fp=jp(FP1,e.name);if(isD(e))await walk(sy,fp,e.name,L);else L.push({s:fp,r:e.name,z:Number(e.size),m:Number(e.mtime)})}});
return"Descargados en "+dh.name+": "+await cpList(L,dh,null,"⬇️");
}
async function upFiles(fs,dir){
const tot=fs.reduce((a,f)=>a+f.size,0);let n=0,done=0;
await syncDo(async sy=>{for(const f of fs){
if(BK_X||!A1)break;
const nm=f.name.replace(/\//g,"_");let v=0;
await sy.write({filename:jp(dir,nm),mtime:Math.floor(f.lastModified/1000),file:f.stream().pipeThrough(new TransformStream({transform(c,t){if(BK_X)throw new Error("Cancelado");v+=c.length;pr("📤 "+nm+" · "+mbB(done+v)+" de "+mbB(tot),tot?(done+v)/tot:null);t.enqueue(c)}}))});
done+=f.size;n++;
}});
return n+" subidos a "+dir;
}
async function upRun(fs){if(!fs.length||!A1)return;const d=FP1;await job(()=>upFiles(fs,d));if(VC1==="fl"&&FP1===d)flLoad(d)}
$("GA_FD").addEventListener("click",()=>{if(A1)job(flDown)});
$("adbFlPut").addEventListener("click",()=>{if(A1)flIn.click()});
flIn.addEventListener("change",()=>{const fs=[...flIn.files];flIn.value="";upRun(fs)});
flList.addEventListener("dragover",e=>{if(!A1||!e.dataTransfer.types.includes("Files"))return;e.preventDefault();flList.classList.add("dr")});
flList.addEventListener("dragleave",()=>flList.classList.remove("dr"));
flList.addEventListener("drop",e=>{flList.classList.remove("dr");if(!A1||!e.dataTransfer.files.length)return;e.preventDefault();upRun([...e.dataTransfer.files])});
$("GA_FE").addEventListener("click",async()=>{
const n=[...FS1][0];if(!n||!A1)return;
const t=(prompt("Nuevo nombre",n)||"").trim();if(!t||t===n)return;
if(t.includes("/")){setSt("El nombre no puede tener /");return}
const o=(await runSh("mv "+q1(jp(FP1,n))+" "+q1(jp(FP1,t))+" 2>&1")).trim();if(o)setSt("Error: "+o);
flLoad(FP1);
});
$("GA_FK").addEventListener("click",async()=>{
if(!A1)return;
const t=(prompt("Nombre de la carpeta")||"").trim();if(!t)return;
if(t.includes("/")){setSt("El nombre no puede tener /");return}
const o=(await runSh("mkdir "+q1(jp(FP1,t))+" 2>&1")).trim();if(o)setSt("Error: "+o);
flLoad(FP1);
});
$("GA_FB").addEventListener("click",async()=>{
const ns=[...FS1];if(!ns.length||!A1)return;
if(!confirm("Borrar "+ns.length+(ns.length>1?" elementos":" elemento")+"? No se puede deshacer."))return;
ov("Borrando...");
try{await runSh("rm -rf "+ns.map(n=>q1(jp(FP1,n))).join(" "))}catch(e){setSt("Error: "+e.message)}
flLoad(FP1);
});

const BKI=[
["ct","👥","Contactos","Contactos.vcf",1],
["sms","💬","SMS","SMS.xml, compatible con SMS Backup & Restore",1],
["cl","📞","Llamadas","Llamadas.xml",1],
["wf","📶","Redes Wi-Fi","WiFi.json con las contrasenas: guardalo en un lugar seguro",1],
["dc","📷","Fotos y videos","DCIM, Pictures y Movies",1,["DCIM","Pictures","Movies"]],
["dl","📄","Descargas y documentos","Download y Documents",0,["Download","Documents"]],
["mu","🎵","Musica y grabaciones","Music y Recordings",0,["Music","Recordings"]],
["wa","🟢","WhatsApp","Fotos, audios y copias cifradas de los chats",0,["Android/media/com.whatsapp","Android/media/com.whatsapp.w4b"]],
["ap","📦","Apps instaladas","Solo el APK, sin los datos de cada app",0]
];
for(const[k,i,t,d,on,ds]of BKI){
const fo=!!ds||k==="ap",lb=document.createElement("label"),sp=document.createElement("span"),b=document.createElement("b"),sm=document.createElement("small");
b.textContent=i+" "+t;sm.textContent=fo&&!FSA?"Necesita Chrome o Edge en PC":d;sp.append(b,sm);
const ck=document.createElement("input");ck.type="checkbox";ck.id="GA_K_"+k;ck.checked=!!on&&(FSA||!fo);ck.disabled=fo&&!FSA;
lb.append(sp,ck);$("GA_BKL").appendChild(lb);
}
if(!FSA){$("GA_BKG").textContent="💾 Descargar copia";$("GA_BKT").textContent="Cada parte se descarga como un archivo. Para copiar fotos, videos y apps usa Chrome o Edge en PC."}
function xe(s){return String(s).replace(/[\x00-\x08\x0b\x0c\x0e-\x1f]/g,"").replace(/[&<>"'\n\r\t]/g,c=>"&#"+c.charCodeAt(0)+";")}
function rdt(d){const x=new Date(+d);return isNaN(x)?"":x.toLocaleString()}
function xSms(a){return"<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>\n<smses count=\""+a.length+"\">\n"+a.map(o=>"  <sms "+Object.entries(o).map(([k,v])=>k+"=\""+xe(v)+"\"").join(" ")+" readable_date=\""+xe(rdt(o.date))+"\" contact_name=\"(Unknown)\" />").join("\n")+"\n</smses>\n"}
function xCalls(a){return"<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>\n<calls count=\""+a.length+"\">\n"+a.map(o=>"  <call "+["number","duration","date","type","presentation"].filter(k=>o[k]!=null).map(k=>k+"=\""+xe(o[k])+"\"").join(" ")+" readable_date=\""+xe(rdt(o.date))+"\" contact_name=\""+xe(o.name||"(Unknown)")+"\" />").join("\n")+"\n</calls>\n"}
async function bkData(k){
if(k==="ct"){let v="",n=0;await jar("vcf",o=>{if(o.v)v+=o.v;if(o.n!=null)n=o.n});return["Contactos.vcf",v,n]}
if(k==="wf"){const a=[];await jar("wifi",o=>a.push(o));return["WiFi.json",JSON.stringify(a,null,1),a.length]}
const sm=k==="sms",a=[];
await jar(sm?"sms":"calls",o=>{if(!(Object.keys(o).length===1&&"n" in o))a.push(o)});
return[sm?"SMS.xml":"Llamadas.xml",sm?xSms(a):xCalls(a),a.length];
}
async function bkDirs(root,ds,lb){
const L=[];pr(lb+": buscando archivos...",null,1);
await syncDo(async sy=>{for(const d of ds)await walk(sy,"/sdcard/"+d,d,L)});
if(BK_X)return"cancelado";
if(!L.length)return"sin archivos";
const mf=await jsRd(root,"Archivos.json")||{};
const r=await cpList(L,await root.getDirectoryHandle("Archivos",{create:true}),mf,lb);
await wrF(root,"Archivos.json",JSON.stringify(mf));
return r;
}
async function bkApks(root){
const ad=await root.getDirectoryHandle("APK",{create:true});
let L=[...(await runSh("pm list packages -3 --show-versioncode 2>/dev/null")).matchAll(/^package:(\S+)(?:\s+versionCode:(\d+))?/gm)];
if(!L.length)L=[...(await runSh("pm list packages -3")).matchAll(/^package:(\S+)()/gm)];
L=L.filter(m=>PKR1.test(m[1]));
let n=0,sk=0,er=0,i=0;
for(const m of L){
if(BK_X||!A1)break;i++;
const id=m[1],nm=id+(m[2]?"-"+m[2]:"");
pr("📦 "+i+"/"+L.length+" · "+id,i/L.length,1);
if(await fhEx(ad,nm+".apk")||await fhEx(ad,nm+".apks")){sk++;continue}
try{
const ps=parsePkgs(await runSh("pm path "+id));if(!ps.length)continue;
if(ps.length===1){const fh=await ad.getFileHandle(nm+".apk",{create:true});await syncDo(sy=>cpTo(sy,ps[0],fh))}
else await wrF(ad,nm+".apks",await apksZip(ps));
n++;
}catch(e){if(BK_X)break;er++}
}
return n+" copiadas"+(sk?", "+sk+" ya estaban":"")+(er?", "+er+" con error":"");
}
async function bkRun(){
const ks=BKI.filter(x=>$("GA_K_"+x[0]).checked);
if(!ks.length)return"Elegi algo para copiar.";
let root=null;
if(FSA){let dh;try{dh=await showDirectoryPicker({id:"ga1",mode:"readwrite"})}catch(e){if(e.name==="AbortError")return"Cancelado.";throw e}root=await dh.getDirectoryHandle(FN0("Copia "+(MD1||"Android")),{create:true})}
const rs=[];
for(const[k,i,t,,,ds]of ks){
if(BK_X||!A1)break;
pr(i+" "+t+"...",0,1);
let r;
try{
if(k==="ap")r=await bkApks(root);
else if(ds)r=await bkDirs(root,ds,i+" "+t);
else{const[n,x,c]=await bkData(k);if(root)await wrF(root,n,x);else dl(new Blob([x]),n);r=c}
}catch(e){if(BK_X)break;r="error ("+e.message+")"}
rs.push(t+": "+r);
}
return(BK_X?"Cancelado. ":"✅ Copia lista"+(root?" en "+root.name:"")+". ")+rs.join(" · ");
}
$("GA_BKG").addEventListener("click",()=>{if(A1)job(bkRun)});

function smsRows(els){const K=["address","date","date_sent","type","body","read","seen","status","subject","service_center","protocol","locked"];return els.map(e=>{const o={};for(const k of K){const v=e.getAttribute(k);if(v!=null&&v!=="null")o[k]=v}return o}).filter(o=>o.address&&o.date)}
function callRows(els){return els.map(e=>{const o={};for(const k of["number","date","duration","type","presentation"]){const v=e.getAttribute(k);if(v!=null&&v!=="null")o[k]=v}const n=e.getAttribute("contact_name");if(n&&n!=="(Unknown)"&&n!=="null")o.name=n;return o}).filter(o=>o.date)}
async function rsRows(cmd,rows,op){
const tmp="/data/local/tmp/ga_in.jsonl";
await push1(A1,tmp,new TextEncoder().encode(rows.map(o=>JSON.stringify(o)).join("\n")));
if(op)await runSh("cmd appops set com.android.shell "+op+" allow");
let r={i:0,d:0};
try{await jar(cmd+" "+tmp,o=>{if("i" in o){r=o;pr("♻️ "+(o.i+o.d)+" de "+rows.length,(o.i+o.d)/rows.length,1)}})}
finally{if(op)runSh("cmd appops set com.android.shell "+op+" default").catch(()=>{});runSh("rm "+tmp).catch(()=>{})}
return r;
}
async function rsXml(f,tg){
pr("Leyendo "+f.name+"...",null,1);
const d=new DOMParser().parseFromString(await f.text(),"text/xml");
if(d.querySelector("parsererror"))throw new Error(f.name+" no es un XML valido");
const sm=tg==="sms",rows=sm?smsRows([...d.getElementsByTagName("sms")]):callRows([...d.getElementsByTagName("call")]);
if(!rows.length)return"Nada para restaurar en "+f.name;
try{const r=await rsRows(sm?"smsin":"callin",rows,sm?"WRITE_SMS":"");return(sm?"💬 SMS: ":"📞 Llamadas: ")+r.i+" restaurados"+(r.d?", "+r.d+" ya estaban":"")}
catch(e){if(/bloqueado/.test(e.message))throw new Error("Android no dejo escribir los SMS. Restauralos con la app SMS Backup & Restore usando SMS.xml");throw e}
}
async function rsCt(f){
const P="/sdcard/Download/Contactos.vcf";
pr("👥 Copiando contactos al telefono...",null,1);
await push1(A1,P,new Uint8Array(await f.arrayBuffer()));
let id="";
for(let i=0;i<6&&!id;i++){const o=await runSh("content query --uri content://media/external/file --projection _id --where \"_data LIKE '%/Download/Contactos.vcf'\"");id=(o.match(/_id=(\d+)/)||[])[1]||"";if(!id)await SL1(1000)}
if(id){const o=await runSh("am start -a android.intent.action.VIEW -d content://media/external/file/"+id+" -t text/x-vcard --grant-read-uri-permission 2>&1");if(!/Error/i.test(o))return"👥 Mira el telefono: elegi la app de Contactos y donde guardarlos."}
return"👥 Contactos.vcf quedo en Descargas del telefono: abrilo desde Contactos > Importar.";
}
async function rsWf(f){
if(SDK1&&SDK1<30)throw new Error("Restaurar Wi-Fi necesita Android 11 o mas nuevo");
let a;try{a=JSON.parse(await f.text())}catch(e){a=null}
if(!Array.isArray(a))throw new Error(f.name+" no es una lista de redes");
const T=new Set(["open","owe","wpa2","wpa3"]),ok=a.filter(w=>w&&typeof w.s==="string"&&w.s&&T.has(w.k)&&(w.k==="open"||w.k==="owe"||typeof w.p==="string"));
let i=0;
for(const w of ok){if(BK_X||!A1)break;i++;pr("📶 "+i+"/"+ok.length+" · "+w.s,i/ok.length,1);await runSh("cmd wifi add-network "+q1(w.s)+" "+w.k+(w.k==="wpa2"||w.k==="wpa3"?" "+q1(w.p):"")+(w.h?" -h":""))}
const now=new Set();await jar("wifi",o=>now.add(o.s));
return"📶 Wi-Fi: "+ok.filter(w=>now.has(w.s)).length+" de "+a.length+" redes guardadas en el telefono"+(a.length>ok.length?" (empresariales y WEP no se pueden restaurar)":"");
}
async function rsAr(dh){
const L=[];pr("📷 Buscando archivos en la copia...",null,1);
const wk=async(d,rel)=>{for await(const[n,h]of d.entries()){if(BK_X)return;const r=rel?rel+"/"+n:n;if(h.kind==="directory")await wk(h,r);else L.push({h,r})}};
await wk(dh,"");
if(!L.length)return"La carpeta Archivos esta vacia";
const fs=[];for(const x of L)fs.push(await x.h.getFile());
const tot=fs.reduce((a,f)=>a+f.size,0);let n=0,sk=0,er=0,done=0;
let sy=await A1.sync();
try{
for(let j=0;j<L.length;j++){
if(BK_X||!A1)break;
const x=L[j],f=fs[j],p="/sdcard/"+x.r,tx=v=>"📷 "+(j+1)+"/"+L.length+" · "+mbB(done+v)+" de "+mbB(tot)+" · "+f.name;
let st=null;try{st=await sy.lstat(p)}catch(e){}
if(st&&st.mode&&Number(st.size)===f.size){sk++;done+=f.size;pr(tx(0),tot?done/tot:null);continue}
try{let v=0;await sy.write({filename:p,mtime:RS1.mf[x.r]||Math.floor(f.lastModified/1000),file:f.stream().pipeThrough(new TransformStream({transform(c,t){if(BK_X)throw new Error("Cancelado");v+=c.length;pr(tx(v),tot?(done+v)/tot:null);t.enqueue(c)}}))});n++}
catch(e){if(BK_X)break;er++;await sy.dispose().catch(()=>{});sy=await A1.sync()}
done+=f.size;
}
}finally{await sy.dispose().catch(()=>{})}
return"📷 Archivos: "+n+" copiados al telefono"+(sk?", "+sk+" ya estaban":"")+(er?", "+er+" con error":"");
}
async function rsAp(v){
const fs=[];
if(Array.isArray(v))fs.push(...v);else for await(const[n,h]of v.entries())if(h.kind==="file"&&/\.apks?$/i.test(n))fs.push(await h.getFile());
const inst=new Map();for(const m of(await runSh("pm list packages --show-versioncode 2>/dev/null")).matchAll(/^package:(\S+)\s+versionCode:(\d+)/gm))inst.set(m[1],+m[2]);
let n=0,sk=0,er=0,i=0;
for(const f of fs){
if(BK_X||!A1)break;i++;
const m=f.name.match(/^([A-Za-z0-9._]+)-(\d+)\.apks?$/);
if(m&&inst.has(m[1])&&inst.get(m[1])>=+m[2]){sk++;continue}
pr("📦 Instalando "+i+"/"+fs.length+" · "+f.name,i/fs.length,1);
try{const ps=await apkParts([f]);if(!ps.length)throw new Error("sin APK");if(ps.length===1)await pushInstall(ps[0]);else await pushSplit(ps);n++}catch(e){er++}
}
return"📦 Apps: "+n+" instaladas"+(sk?", "+sk+" ya estaban":"")+(er?", "+er+" con error":"");
}
function rsDraw(){
const L=$("GA_RSL"),f=RS1.f;L.replaceChildren();
const it=[["👥","Contactos",f.ct,rsCt],["💬","SMS",f.sms,x=>rsXml(x,"sms")],["📞","Llamadas",f.cl,x=>rsXml(x,"call")],["📶","Redes Wi-Fi",f.wf,rsWf],["📷","Archivos: fotos, videos, WhatsApp...",RS1.ar,rsAr],["📦","Apps (APK)",Array.isArray(RS1.ap)&&!RS1.ap.length?null:RS1.ap,rsAp]];
let c=0;
for(const[i,t,v,fn]of it){
if(!v)continue;c++;
const d=document.createElement("div"),sp=document.createElement("span"),b=document.createElement("b"),sm=document.createElement("small");
b.textContent=i+" "+t;sm.textContent=Array.isArray(v)?v.length+" APK":v.name;sp.append(b,sm);
const bt=document.createElement("button");bt.type="button";bt.textContent="♻️ Restaurar";
bt.addEventListener("click",()=>{if(!A1){setSt("Conecta el telefono primero.");return}job(()=>fn(v))});
d.append(sp,bt);L.appendChild(d);
}
if(!c){const p=document.createElement("p");p.className="GA_TX";p.textContent="No hay nada para restaurar en "+RS1.n+".";L.appendChild(p)}
}
async function rsHas(d){for(const n of["Contactos.vcf","SMS.xml","Llamadas.xml","WiFi.json"])if(await fhEx(d,n))return true;for(const n of["Archivos","APK"]){try{await d.getDirectoryHandle(n);return true}catch(e){}}return false}
$("GA_RSE").addEventListener("click",async()=>{
if(!FSA){$("GA_RSF").click();return}
let dh;try{dh=await showDirectoryPicker({id:"ga1",mode:"read"})}catch(e){if(e.name!=="AbortError")setSt("Error: "+e.message);return}
if(!await rsHas(dh))for await(const[n,h]of dh.entries())if(h.kind==="directory"&&n.startsWith("Copia ")&&await rsHas(h)){dh=h;break}
const g=async n=>{try{return await(await dh.getFileHandle(n)).getFile()}catch(e){return null}},gd=async n=>{try{return await dh.getDirectoryHandle(n)}catch(e){return null}};
RS1={n:dh.name,f:{ct:await g("Contactos.vcf"),sms:await g("SMS.xml"),cl:await g("Llamadas.xml"),wf:await g("WiFi.json")},ar:await gd("Archivos"),ap:await gd("APK"),mf:await jsRd(dh,"Archivos.json")||{}};
rsDraw();
});
$("GA_RSF").addEventListener("change",()=>{
const fs=[...$("GA_RSF").files];$("GA_RSF").value="";if(!fs.length)return;
const by=re=>fs.find(x=>re.test(x.name))||null;
RS1={n:"los archivos elegidos",f:{ct:by(/\.vcf$/i),sms:by(/sms.*\.xml$/i),cl:by(/(llamadas|calls).*\.xml$/i),wf:by(/\.json$/i)},ar:null,ap:fs.filter(x=>/\.apks?$/i.test(x.name)),mf:{}};
rsDraw();
});

const scrSt=$("adbScrSt"),scrHold=$("adbScrHold"),scrBtn=$("GA_SS");
let scrVw=0,scrVh=0,SCT=0;
async function scrStart(){
if(scrCli||!A1)return;
const tk=++SCT;scrBtn.textContent="⏹️ Detener";
scrSt.textContent="Descargando servidor...";
scrHold.replaceChildren();
try{
const rs=await fetch(SRVJ1);
if(!rs.ok)throw new Error("HTTP "+rs.status+" al obtener jar");
scrSt.textContent="Subiendo servidor al dispositivo...";
await AdbScrcpyClient.pushServer(A1,rs.body);
scrSt.textContent="Iniciando scrcpy...";
const cl=await AdbScrcpyClient.start(A1,DefaultServerPath,new AdbScrcpyOptions3_3_3({control:true,audio:false,video:true,videoBitRate:4000000,maxSize:720},{version:"3.3.4"}));
if(tk!==SCT||GONE){cl.close().catch(()=>{});return}
scrCli=cl;
(async()=>{for await(const l of cl.output){if(tk!==SCT)break;if(/INJECT_EVENTS/.test(l))scrSt.textContent="El telefono no deja controlar la pantalla. En Xiaomi activa Opciones de desarrollador > Depuracion USB (ajustes de seguridad) y vuelve a conectar.";else if(/\] ERROR:/.test(l))scrSt.textContent="Error scrcpy: "+l.replace(/^.*\] ERROR: /,"")}})().catch(()=>{});
const rend=WebGLVideoFrameRenderer.isSupported?new WebGLVideoFrameRenderer():new BitmapVideoFrameRenderer();
scrHold.appendChild(rend.canvas);
if(!cl.videoStream){scrSt.textContent="Servidor sin video";return}
const{metadata,stream}=await cl.videoStream;
scrDec=new WebCodecsVideoDecoder({codec:metadata.codec,renderer:rend});
scrDec.sizeChanged(({width,height})=>{scrVw=width;scrVh=height});
stream.pipeTo(scrDec.writable).catch(e=>{if(tk===SCT)console.error(e)});
scrSt.textContent=cl.controller?"Conectado: toca, arrastra, usa la rueda o el teclado sobre la pantalla":"Solo ver: sin control";
}catch(e){
if(tk!==SCT)return;
scrSt.textContent=(e?.output?"Error servidor: ":"Error: ")+e.message;
if(e?.output)console.error("scrcpy server output:",e.output.join("\n"));
console.error(e);scrBtn.textContent="▶️ Iniciar";
}
}
async function scrStop(){
SCT++;
const c=scrCli;scrCli=null;
if(c){try{await c.close()}catch(e){}}
scrDec?.dispose();scrDec=null;scrVw=0;scrVh=0;
scrHold.replaceChildren();
scrBtn.textContent="▶️ Iniciar";scrSt.textContent="Detenido.";
}
scrBtn.addEventListener("click",()=>{if(!A1)return;if(scrCli||scrBtn.textContent.includes("Detener"))scrStop();else scrStart()});
const BTN1=[1,4,2,8,16];
function scrXY(ev){const cv=scrHold.querySelector("canvas")||scrHold,rc=cv.getBoundingClientRect();return[clamp((ev.clientX-rc.x)/rc.width,0,1)*scrVw,clamp((ev.clientY-rc.y)/rc.height,0,1)*scrVh]}
async function scrPtr(ev){
if(!scrCli||!scrCli.controller||!scrVw)return;
ev.preventDefault();
const ms=ev.pointerType==="mouse";
let act;
if(ev.type==="pointerdown"){act=AndroidMotionEventAction.Down;scrHold.focus({preventScroll:true});try{scrHold.setPointerCapture(ev.pointerId)}catch(e){}}
else if(ev.type==="pointermove"){if(ev.buttons===0&&!ms)return;act=ev.buttons===0?AndroidMotionEventAction.HoverMove:AndroidMotionEventAction.Move}
else act=AndroidMotionEventAction.Up;
const[px,py]=scrXY(ev);
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
for(const t of["pointerdown","pointermove","pointerup","pointercancel"])scrHold.addEventListener(t,scrPtr);
scrHold.addEventListener("wheel",ev=>{const c=scrCli?.controller;if(!c||!scrVw)return;ev.preventDefault();const[px,py]=scrXY(ev);c.injectScroll({pointerX:px,pointerY:py,videoWidth:scrVw,videoHeight:scrVh,scrollX:-Math.sign(ev.deltaX),scrollY:-Math.sign(ev.deltaY),buttons:0}).catch(()=>{})},{passive:false});
async function key(k){
if(!A1)return;
const c=scrCli?.controller;
try{
if(c){await c.injectKeyCode({action:AndroidKeyEventAction.Down,keyCode:k,repeat:0,metaState:0});await c.injectKeyCode({action:AndroidKeyEventAction.Up,keyCode:k,repeat:0,metaState:0})}
else await runSh("input keyevent "+k);
}catch(e){scrSt.textContent="Error: "+e.message}
}
for(const b of $("GA_scr").querySelectorAll("[data-k]"))b.addEventListener("click",()=>key(+b.dataset.k));
const KM1={Enter:66,Backspace:67,Delete:112,Escape:4,ArrowUp:19,ArrowDown:20,ArrowLeft:21,ArrowRight:22,Tab:61};
scrHold.addEventListener("keydown",ev=>{
const c=scrCli?.controller;if(!c||ev.ctrlKey||ev.metaKey||ev.altKey)return;
const k=KM1[ev.key];
if(k){ev.preventDefault();key(k)}else if(ev.key.length===1){ev.preventDefault();c.injectText(ev.key).catch(()=>{})}
});
$("GA_KF").addEventListener("submit",async ev=>{
ev.preventDefault();
const t=$("GA_KT").value;if(!t||!A1)return;
$("GA_KT").value="";
try{const c=scrCli?.controller;if(c)await c.injectText(t);else await runSh("input text "+q1(t.replace(/ /g,"%s")))}catch(e){scrSt.textContent="Error: "+e.message}
});

const gridEl=$("adbStoreGrid"),pgEl=$("adbStorePg"),searchInp=$("adbSearchInp");
function pkgIdFromUrl(u){const m=u.match(/\/packages\/([^/?#]+)/);return m?m[1]:null}
function mkStoreCard(app){
const a=document.createElement("a");
a.className="BMD1";a.href="#";
const img=document.createElement("img");
img.src=app.icon;img.alt=app.name;img.loading="lazy";img.decoding="async";
const cn=document.createElement("div");cn.className="BMD1-CN";
const h=document.createElement("h3");h.textContent=app.name;
const p=document.createElement("p");p.textContent=app.summary||"";
cn.append(h,p);a.append(img,cn);
let busy=false;
a.addEventListener("click",async ev=>{
ev.preventDefault();
if(busy)return;
if(!A1){p.textContent="Conecta el telefono primero";setTimeout(()=>p.textContent=app.summary||"",2500);return}
busy=true;
p.textContent="Obteniendo version...";
try{
const dp=await(await fetch(FN1+"?action=pkg&id="+encodeURIComponent(app.pkg))).json();
const vc=dp.suggestedVersionCode;
if(!vc)throw new Error("sin version disponible");
p.textContent="Descargando...";
const rd=await fetch(FN1+"?action=apk&pkg="+encodeURIComponent(app.pkg)+"&vc="+encodeURIComponent(vc));
if(!rd.ok)throw new Error("HTTP "+rd.status);
const buf=await rd.arrayBuffer();
p.textContent="Instalando...";
await pushInstall(new Uint8Array(buf));
p.textContent="Instalado";
}catch(e){p.textContent="Error: "+e.message;console.error(e)}
finally{busy=false;setTimeout(()=>p.textContent=app.summary||"",2000)}
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
gridEl.replaceChildren();
stCur.slice(stPg*20,stPg*20+20).forEach(app=>gridEl.appendChild(mkStoreCard(app)));
if(stCur.length>20)storeNav();else pgEl.replaceChildren();
if(sw)return;
if(SW)SW.pre();
gridEl.style.setProperty("--d",dir?(dir>0?"24px":"-24px"):"0px");
gridEl.classList.remove("AN1");void gridEl.offsetWidth;gridEl.classList.add("AN1");
}
async function doStoreSearch(){
clearTimeout(stDbt);
const q=searchInp.value.trim();
if(!q){stCur=[];stPg=0;renderStorePage();return}
if(stAC)stAC.abort();
stAC=new AbortController();
try{
const d=await(await fetch(FN1+"?action=search&q="+encodeURIComponent(q),{signal:stAC.signal})).json();
stCur=(d.apps||[]).map(app=>({name:app.name,summary:app.summary,icon:app.icon,pkg:pkgIdFromUrl(app.url)})).filter(a=>a.pkg);
stPg=0;renderStorePage();
}catch(e){
if(e.name==="AbortError")return;
gridEl.replaceChildren();const p=document.createElement("p");p.className="GA_TX";p.textContent="Error al buscar apps";gridEl.appendChild(p);
}
}
searchInp.addEventListener("input",()=>{clearTimeout(stDbt);stDbt=setTimeout(doStoreSearch,5000)});
$("GA_SF").addEventListener("submit",ev=>{ev.preventDefault();doStoreSearch()});

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
if(!fs.length||!A1)return;
const n=fs.map(f=>f.name).join(", ");
setSt("Instalando "+n+"...");ov("Instalando...");
try{
const ps=await apkParts(fs);
if(!ps.length)throw new Error("no hay APK adentro");
if(ps.length===1)await pushInstall(ps[0]);else await pushSplit(ps);
setSt("Instalado: "+n);
}catch(e){setSt("Error al instalar: "+e.message);console.error(e)}
ov("");
});

const secList=$("adbSecList");
async function secLoad(){
if(!A1)return;
ov("Revisando...");secList.replaceChildren();
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
const p=document.createElement("p");p.className="GA_TX";p.textContent=ls?(ls.length?de+" Si no reconoces alguna, revisala.":"Ninguna."):"No disponible en esta version de Android.";det.appendChild(p);
for(const id of ls||[]){const it=itOf(id);det.appendChild(mkRow({im:icU(it.ic),ic:"📦",t:it.n||id,de:it.n&&it.n!==id?id:"",ds:it.description||"",go:()=>cfOpen(it),b:[["Configurar","⚙️",true,()=>cfOpen(it)]]}))}
secList.appendChild(det);
}
}catch(e){setSt("Error revision: "+e.message)}
ov("");
icLoad();
}
$("adbSecRe").addEventListener("click",()=>{if(A1)secLoad()});

const cmdLog=$("adbCmdLog"),cmdInp=$("adbCmdInp");
function cmdLogLn(s){cmdLog.textContent+=s+"\n";cmdLog.scrollTop=cmdLog.scrollHeight}
async function cmdExec(cmd){
if(!A1){cmdLogLn("! No hay dispositivo conectado");return}
cmdLogLn("$ "+cmd);
try{cmdLogLn((await runSh(cmd)).trim()||"(sin salida)")}catch(e){cmdLogLn("Error: "+e.message)}
}
for(const it of CMDS1){const b=document.createElement("button");b.type="button";b.textContent=it.n;b.addEventListener("click",()=>cmdExec(it.c));$("adbCmdGrid").appendChild(b)}
$("GA_CF").addEventListener("submit",ev=>{ev.preventDefault();const v=cmdInp.value.trim();if(!v)return;cmdExec(v);cmdInp.value=""});

async function onCnn(){
try{
const mgr=AdbDaemonWebUsbDeviceManager.BROWSER;
if(!mgr){setSt("Este navegador no tiene WebUSB: usa Chrome o Edge.");return}
setSt("Elegi el telefono en el menu que aparece...");
const dv=await mgr.requestDevice();
if(!dv){setSt("No elegiste ningun dispositivo.");return}
ov("Conectando...");
const cn=await dv.connect();
setSt("Autenticando: revisa el telefono si pide permiso...");
const tr=await AdbDaemonTransport.authenticate({serial:dv.serial,connection:cn,credentialStore:CS1});
const a=new Adb(tr);
A1=a;JOK=null;SC1=null;LB1=null;MD1="";
a.disconnected.then(()=>{
if(A1!==a)return;
A1=null;JOK=null;SC1=null;LB1=null;BK_X=1;
if(scrCli)scrStop();
for(const d of DLG)if(d.open&&d!==repDlg)d.close();
cnUi(0);go("ini",null,0);
setSt("Telefono desconectado.");
});
const g=secs(await runSh("echo @A;getprop ro.product.cpu.abi;echo @S;getprop ro.build.version.sdk"),"A|S");
abi1=(g.A||[]).join("").trim();SDK1=+(g.S||[]).join("").trim()||0;
cnUi(1);
setSt("Conectado: "+(a.banner?.model||dv.serial)+" ("+abi1+")");
devLoad().catch(e=>setSt("Error Info: "+e.message));
}catch(e){setSt("Error: "+e.message);console.error(e)}
ov("");
}
$("adbBtnCnn").addEventListener("click",onCnn);

const RPARTS1=["system","system_root","vendor","vendor_dlkm","odm","odm_dlkm","product","system_ext"];
const RCAND1=["/build.prop","/system/build.prop","/default.prop"];
async function runShR(cmd){return await AR1.subprocess.noneProtocol.spawnWaitText(cmd)}
const repDlg=$("adbRepDlg"),repMsg=$("adbRepMsg"),repStep1=$("adbRepStep1"),repStep2=$("adbRepStep2"),repStep3=$("adbRepStep3");
const repPlan=$("adbRepPlan"),repDone=$("adbRepDone"),btnRepTest=$("adbBtnRepTest"),btnRepRun=$("adbBtnRepRun");
const repFmt=$("adbRepFmt"),repDfeIn=$("adbRepDfe"),repDfeN=$("adbRepDfeN");
let repDfe=null;
$("adbBtnRepDfe").addEventListener("click",()=>repDfeIn.click());
repDfeIn.addEventListener("change",()=>{repDfe=repDfeIn.files[0]||null;repDfeN.textContent=repDfe?repDfe.name:""});
async function repScan(){
const bl=(await runShR("ls /dev/block/mapper 2>/dev/null | grep -v control || ls /dev/block/by-name 2>/dev/null || ls /dev/block/bootdevice/by-name 2>/dev/null")).split(/\s+/).filter(Boolean).join(" ");
const out=await runShR("for p in "+RPARTS1.join(" ")+"; do [ -d /$p ] || continue; twrp mount /$p >/dev/null 2>&1; mount /$p >/dev/null 2>&1; mount -o rw,remount /$p >/dev/null 2>&1; m=$(grep \" /$p \" /proc/mounts | head -n1); if [ -z \"$m\" ]; then echo \"P $p no\"; elif echo \"$m\" | grep -q ' rw,'; then echo \"P $p rw\"; else echo \"P $p ro\"; fi; done");
const pt=[...out.matchAll(/^P (\S+) (\S+)\s*$/gm)].map(m=>({p:m[1],s:m[2]}));
const fl=[];
for(const x of pt){
if(x.s!=="rw")continue;
for(const c of RCAND1){const path="/"+x.p+c;if((await runShR("[ -f "+path+" ] && echo si || echo no")).trim()==="si")fl.push(path)}
}
return{bl,pt,fl};
}
async function pubKeyLine(){
for await(const k of CS1.iterateKeys()){const pub=adbGeneratePublicKey(k.buffer);return btoa(String.fromCharCode(...pub))+" "+k.name}
const nk=await CS1.generateKey();const pub=adbGeneratePublicKey(nk.buffer);return btoa(String.fromCharCode(...pub))+" "+nk.name;
}
function resetRepUi(){
repStep1.style.display="";repStep2.style.display="none";repStep3.style.display="none";
repMsg.textContent="";
btnRepTest.style.pointerEvents="";btnRepTest.style.opacity="";
btnRepRun.style.pointerEvents="";btnRepRun.style.opacity="";
repFmt.checked=false;repDfe=null;repDfeIn.value="";repDfeN.textContent="";
}
$("adbBtnRep").addEventListener("click",()=>{resetRepUi();dOpen(repDlg)});
btnRepTest.addEventListener("click",async()=>{
btnRepTest.style.pointerEvents="none";btnRepTest.style.opacity=".5";
const rel=()=>{btnRepTest.style.pointerEvents="";btnRepTest.style.opacity=""};
repMsg.textContent="Conectando...";
try{
const mgr=AdbDaemonWebUsbDeviceManager.BROWSER;
if(!mgr){repMsg.textContent="WebUSB no disponible en este navegador.";rel();return}
const dv=await mgr.requestDevice();
if(!dv){repMsg.textContent="No se selecciono ningun dispositivo.";rel();return}
const cn=await dv.connect();
const tr=await AdbDaemonTransport.authenticate({serial:dv.serial,connection:cn,credentialStore:CS1});
AR1=new Adb(tr);
repMsg.textContent="Probando comando twrp...";
const low=(await runShR("twrp 2>&1; echo EXIT:$?")).toLowerCase();
if(low.includes("not appear to be running")||low.includes("waiting for twrp")){repMsg.textContent="TWRP no responde, presiona 'Probar conexion' de nuevo.";rel();return}
if(low.includes("inaccessible")||low.includes("not found")||low.includes("no such file")||low.includes("unknown command")){repMsg.textContent="El comando 'twrp' no existe en este recovery. Esto solo funciona con TWRP u otro custom recovery compatible, no con el recovery de fabrica.";rel();return}
repMsg.textContent="TWRP respondio correctamente. Montando particiones...";
const sc=await repScan();
repStep1.style.display="none";repStep2.style.display="";
repPlan.textContent="Particiones: "+(sc.bl||"?")+
"\nMontadas: "+(sc.pt.map(x=>x.p+" ("+x.s+")").join(", ")||"ninguna")+
"\nArchivos a modificar: "+(sc.fl.join(", ")||"ninguno, se usara /default.prop")+
"\n\nSe copiara tu clave ADB publica y se habilitara ADB inseguro en las particiones de sistema disponibles. Al finalizar el telefono se reiniciara a Android normal, de esta manera poder usar scrcpy para poder controlar el dispositivo con el boton pantalla que encontraras en el menu.";
}catch(e){repMsg.textContent="Error de conexion: "+e.message;rel();console.error(e)}
});
btnRepRun.addEventListener("click",async()=>{
if(repFmt.checked&&!confirm("Formatear data borra TODO el telefono. Continuar?"))return;
btnRepRun.style.pointerEvents="none";btnRepRun.style.opacity=".5";
const done=[];
try{
if(repFmt.checked){repPlan.textContent="Formateando data...";await Promise.race([runShR("twrp format data"),SL1(120000)]);done.push("data formateada")}
if(repDfe){repPlan.textContent="Instalando "+repDfe.name+"...";await push1(AR1,"/tmp/DFE.zip",new Uint8Array(await repDfe.arrayBuffer()));await Promise.race([runShR("twrp install /tmp/DFE.zip"),SL1(120000)]);done.push("DFE instalado")}
repPlan.textContent="Ejecutando...";
const key=(await pubKeyLine()).replace(/'/g,"'\\''");
await runShR("twrp mount /data >/dev/null 2>&1; mount /data >/dev/null 2>&1; mkdir -p /data/misc/adb");
await runShR("echo '"+key+"' > /data/misc/adb/adb_keys");
await runShR("chmod 600 /data/misc/adb/adb_keys");
await runShR("chown 2000:2000 /data/misc/adb/adb_keys");
done.push("/data/misc/adb/adb_keys (clave copiada)");
const sc=await repScan();
for(const path of sc.fl){
done.push(path);
await runShR("grep -q '^ro.adb.secure=' "+path+" && sed -i 's/^ro.adb.secure=.*/ro.adb.secure=0/' "+path+" || echo 'ro.adb.secure=0' >> "+path);
await runShR("grep -q '^persist.sys.usb.config=' "+path+" && sed -i 's/^persist.sys.usb.config=.*/persist.sys.usb.config=adb/' "+path+" || echo 'persist.sys.usb.config=adb' >> "+path);
}
if(!sc.fl.length){await runShR("echo 'ro.adb.secure=0' >> /default.prop");await runShR("echo 'persist.sys.usb.config=adb' >> /default.prop");done.push("/default.prop (fallback)")}
repStep2.style.display="none";repStep3.style.display="";
repDone.textContent="Reiniciando a Android...";
try{await runShR("reboot")}catch(e2){console.error("reboot corto la conexion (normal):",e2)}
repDone.textContent="Listo. Archivos modificados: "+done.join(", ")+". Espera a que el telefono inicie, toca Conectar y usa Pantalla para controlarlo.";
}catch(e){repPlan.textContent="Error durante la reparacion: "+e.message;btnRepRun.style.pointerEvents="";btnRepRun.style.opacity="";console.error(e)}
});

stOv.style.display="none";
setSt(navigator.usb?"Presiona Conectar para vincular tu telefono.":"Este navegador no tiene WebUSB: usa Chrome o Edge.");
}catch(e){
stOv.style.display="none";
setSt("Error al iniciar: "+e.message);
console.error(e);
}
})();
</script>
