<div style="text-align:center;max-width:560px;margin:0 auto">
<h2>🚩 Antecedentes</h2>
<p>Busca un numero de WhatsApp en la base de reportes de <a href="https://github.com/weskerty/UnifiedReporting" target="_blank" rel="noopener">UnifiedReporting</a>.</p>
<form id="RU_F1" style="display:flex;gap:8px">
<input id="RU_Q1" type="search" inputmode="tel" enterkeyhint="search" autocomplete="off" placeholder="Numero o LID" style="flex:1;min-width:0">
<button id="RU_K1">🔍 Buscar</button>
</form>
<p id="RU_M1" aria-live="polite"></p>
<div id="RU_T1" hidden><table><thead><tr><th>Numero</th><th>LID</th><th>Categorias</th></tr></thead><tbody id="RU_B1"></tbody></table></div>
<p><small>Otros Motores de busqueda: <a href="https://listahu.org/" target="_blank" rel="noopener">ListaHũ</a></small></p>

<script>
(()=>{
const $=i=>document.getElementById(i),F=$('RU_F1'),Q=$('RU_Q1'),K=$('RU_K1'),M=$('RU_M1'),T=$('RU_T1'),B=$('RU_B1');
const D=s=>String(s||'').replace(/\D/g,'').replace(/^0*(?:595)?/,''),C=(s,q)=>(s=D(s)).includes(q)&&q.length*2>s.length;
const E={__proto__:null,'🧸':'Pederastia','🧃':'VendePatria','⚡':'Nazi','📩':'Spam o acoso al privado','🎰':'Cripto estafa, ruleta o juegos de azar'};
F.onsubmit=e=>{
  e.preventDefault();
  const q=D(Q.value);
  T.hidden=true;
  if(q.length<5)return M.textContent='Escribi mas digitos';
  K.disabled=true;M.textContent='Buscando...';
  fetch('https://raw.githubusercontent.com/weskerty/UnifiedReporting/web-data/reportados.json').then(r=>{if(!r.ok)throw r.status;return r.json()}).then(d=>{
    const h=d.filter(r=>C(r.numero,q)||C(r.lid,q));
    B.textContent='';
    for(const r of h){const t=B.insertRow();for(const v of[r.numero,r.lid,Object.entries(r.categorias||{}).map(([k,n])=>`${k} ${E[k.replace(/️/g,'')]||''} ×${n}`).join('\n')])t.insertCell().innerText=v||''}
    T.hidden=!h.length;
    M.textContent=h.length?'⚠️ Reportes: '+h.length:'✅ Sin reportes';
  }).catch(e=>M.textContent='Error Reportes '+(+e||'')).finally(()=>K.disabled=false);
};
})();
</script>

</div>
