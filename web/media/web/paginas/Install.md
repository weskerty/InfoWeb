<div style="text-align:center;">
<style>
.app-btn{margin:10px auto 0;padding:8px 18px;border-radius:20px;border:1px solid rgba(255,255,255,.2);background:rgba(255,255,255,.08);color:rgba(255,255,255,.85);font-size:.78rem;letter-spacing:.05em;cursor:pointer;transition:background .2s,transform .15s}
.app-btn:hover{background:rgba(255,255,255,.16);transform:translateY(-1px)}
.app-btn:disabled{opacity:.5;cursor:default;transform:none}
</style>

<div id="INS_W">
  <h2>Instalar Aplicacion</h2>
  <p>Al instalar como aplicacion gastas menos saldo al navegar por aqui, carga mas rapido y tienes casi todo disponible incluso sin conexion. Util si tienes datos limitados para no gastar saldo innecesariamente.</p>
  <button id="PI" class="app-btn" style="display:none">📲 Instalar App 💕</button>
  <h3 style="display:flex;justify-content:center;">⬆️ Pruebalo ⬆️</h3>
  <p>y si no te gusta se desinstala como cualquier otra app 🤗</p>
  <div style="display:flex;justify-content:center;">
    <img src="web/adjuntos/Install/UnInstall.avif"
    style="width:320px;height:120px;object-fit:cover;border-radius:12px">
  </div>
</div>

<div id="NT_W">
<h2>Notificaciones</h2>
<p>Tambien puedes activar notificaciones para recibir ofertas y nuevos productos</p>
<button id="NT" class="app-btn" style="display:none"></button>
</div>

<div id="NC_W" style="display:none">
  <p style="font-size:3rem;margin:0">😿</p>
  <p>Tu Navegador no es compatible con las Aplicaciones Web</p>
</div>

<script>
(function(){
  const w=document.getElementById('INS_W');
  const pi=document.querySelector('pwa-install');

  function show(){
    w.style.display='';
    if(pi&&customElements.get('pwa-install'))pi.showDialog(true);
  }
  function hide(){w.style.display='none';}

  if(window._PWA)show();
  else hide();
  window.addEventListener('beforeinstallprompt',show);
  window.addEventListener('appinstalled',hide);

  (async()=>{
    if(!window.PS1)await new Promise(r=>{const s=document.createElement('script');s.src='web/js/lib/Push.js';s.onload=s.onerror=r;document.head.appendChild(s)});
    if(window.PS1?.(document.getElementById('NT')))return;
    document.getElementById('NT_W').style.display='none';
    if(!window._PWA)document.getElementById('NC_W').style.display='';
  })();
})();
</script>
</div>