<style>
#CT_W{max-width:560px;margin:0 auto;display:flex;flex-direction:column;gap:10px;text-align:center}
#CT_W textarea{width:100%;box-sizing:border-box}
#CT_W .CT_R{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;font-size:.85rem}
#CT_W input[type=number]{width:70px;box-sizing:border-box}
#CT_N{margin:0;font-size:1.2rem;font-weight:600}
#CT_N.CT_X{color:#e5484d}
#CT_M{margin:0;font-size:.8rem;opacity:.8}
</style>
<div id="CT_W">
<h2>Contador</h2>
<p>Cuenta caracteres, palabras y lineas.</p>
<textarea id="CT_I" rows="6" placeholder="Mensaje"></textarea>
<div class="CT_R">
<label>Limite <input id="CT_L" type="number" min="1" value="300"></label>
<label title="Cuanto cuenta cada emoji">Emoji <input id="CT_E" type="number" min="0" value="1"></label>
<label title="Vacio = largo real del link">Link <input id="CT_K" type="number" min="0" placeholder="real"></label>
</div>
<p id="CT_N">0 / 300</p>
<p id="CT_M"></p>
</div>
<script>
!function(){
const $=i=>document.getElementById(i),I=$('CT_I'),L=$('CT_L'),E=$('CT_E'),K=$('CT_K'),N=$('CT_N'),T=$('CT_M');
const TE=new TextEncoder();
const SG=window.Intl&&Intl.Segmenter?new Intl.Segmenter(undefined,{granularity:'grapheme'}):null;
const GR=t=>SG?[...SG.segment(t)].map(s=>s.segment):[...t];
const EM=/\p{Extended_Pictographic}|\p{Regional_Indicator}/u;
function RN(){
const t=I.value,lim=+L.value||300,ew=E.value===''?1:+E.value,kw=K.value===''?null:+K.value;
let n=0;
t.split(/(https?:\/\/\S+)/).forEach((p,i)=>{
if(i%2&&kw!==null){n+=kw;return}
GR(p).forEach(g=>{n+=EM.test(g)?ew:1});
});
const w=(t.trim().match(/\S+/g)||[]).length,l=t?t.split(/\r?\n/).length:0;
N.textContent=n+' / '+lim;
N.classList.toggle('CT_X',n>lim);
T.textContent='Palabras '+w+' · Lineas '+l+' · Bytes '+TE.encode(t).length+(n>lim?' · Te pasas por '+(n-lim):'');
}
[I,L,E,K].forEach(e=>e.oninput=RN);
RN();
}();
</script>