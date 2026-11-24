<style>
#RM_W{max-width:560px;margin:0 auto;display:flex;flex-direction:column;gap:10px;text-align:center}
#RM_W textarea{width:100%;box-sizing:border-box}
#RM_W .RM_R{display:flex;gap:8px;justify-content:center;flex-wrap:wrap}
#RM_O{box-sizing:border-box;min-height:7.5em;padding:8px;text-align:left;white-space:pre-wrap;word-break:break-word;border:1px solid currentColor;border-radius:4px;border-color:rgba(128,128,128,.5)}
#RM_O:empty::before{content:'Resultado';opacity:.5}
#RM_O a{color:#53bdeb;cursor:pointer;font-weight:600}
#RM_M{margin:0;font-size:.8rem;opacity:.8}
</style>
<div id="RM_W">
<h2>Readmore</h2>
<p>Para Ocultar Presiona Enter 2 Veces (↵).</p>
<textarea id="RM_I" rows="5" placeholder="Mensaje"></textarea>
<div id="RM_O"></div>
<div class="RM_R"><button id="RM_C">Copiar</button></div>
<p id="RM_M"></p>
</div>
<script>
!function(){
const $=i=>document.getElementById(i),I=$('RM_I'),O=$('RM_O'),T=$('RM_M');
const R=String.fromCharCode(8206).repeat(4001);
let V='';
I.oninput=()=>{
V=I.value.replace(/\r?\n\r?\n/g,'\n'+R);
const p=V.split(R);
O.textContent='';T.textContent='';
if(p.length<2){O.textContent=V;return}
const a=document.createElement('a');
a.textContent='Leer mas';
a.onclick=()=>{O.textContent=p.join('')};
O.append(p[0].trimEnd()+' ... ',a);
};
$('RM_C').onclick=()=>{
if(navigator.clipboard)navigator.clipboard.writeText(V);
else{const t=document.createElement('textarea');t.value=V;document.body.appendChild(t);t.select();document.execCommand('copy');t.remove()}
T.textContent='Copiado';
};
}();
</script>