<style>
#JS_W{max-width:560px;margin:0 auto;display:flex;flex-direction:column;gap:10px;text-align:center}
#JS_W textarea{width:100%;box-sizing:border-box}
#JS_W .JS_R{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;align-items:center}
#JS_O{font-family:monospace;font-size:.8rem;white-space:pre;text-align:left}
#JS_M{margin:0;font-size:.8rem;opacity:.8}
</style>
<div id="JS_W">
<h2>Lector JSON</h2>
<div class="JS_R"><button id="JS_L">Cargar JSON</button><select id="JS_V"><option value="0">Indentado</option><option value="1">Plano (ruta = valor)</option></select><label><input id="JS_S" type="checkbox" checked> Ordenar claves</label></div>
<input id="JS_F" type="file" accept=".json,application/json" hidden>
<textarea id="JS_O" rows="14" readonly placeholder="Resultado"></textarea>
<div class="JS_R"><button id="JS_C">Copiar</button></div>
<p id="JS_M"></p>
</div>
<script>
!function(){
const $=i=>document.getElementById(i),O=$('JS_O'),S=$('JS_S'),V=$('JS_V'),T=$('JS_M');
let src='',nm='';
const SO=v=>Array.isArray(v)?v.map(SO):v&&typeof v=='object'?Object.fromEntries(Object.keys(v).sort().map(k=>[k,SO(v[k])])):v;
const ob=v=>v&&typeof v=='object',em=v=>!Object.keys(v).length;
const P=v=>v===null?'null':typeof v=='string'?v.replace(/\r?\n/g,'\\n'):String(v);
const LF=v=>ob(v)?'(vacio)':P(v);
const TR=(v,d)=>{
const pad='  '.repeat(d),o=[];
if(Array.isArray(v))v.forEach(x=>{
if(!ob(x)||em(x))o.push(pad+'- '+LF(x));
else{const s=TR(x,d+1);s[0]=pad+'- '+s[0].trimStart();o.push(...s)}
});
else Object.keys(v).forEach(k=>{
const x=v[k];
if(!ob(x)||em(x))o.push(pad+k+': '+LF(x));
else o.push(pad+k+':',...TR(x,d+1));
});
return o;
};
const FL=(v,p,o)=>{
if(!ob(v)||em(v))o.push((p||'(raiz)')+' = '+LF(v));
else if(Array.isArray(v))v.forEach((x,i)=>FL(x,p+'['+i+']',o));
else Object.keys(v).forEach(k=>FL(v[k],p?p+'.'+k:k,o));
return o;
};
function RN(){
if(!src)return;
try{
let v=JSON.parse(src);
if(S.checked)v=SO(v);
O.value=V.value=='1'?FL(v,'',[]).join('\n'):!ob(v)||em(v)?LF(v):TR(v,0).join('\n');
T.textContent=nm+' ('+O.value.split('\n').length+' lineas)';
}catch(e){O.value='';T.textContent='Error '+e.message}
}
$('JS_L').onclick=()=>$('JS_F').click();
$('JS_F').onchange=async e=>{
const f=e.target.files[0];
if(!f)return;
nm=f.name;src=await f.text();
e.target.value='';
RN();
};
S.onchange=V.onchange=RN;
$('JS_C').onclick=()=>{O.select();navigator.clipboard?navigator.clipboard.writeText(O.value):document.execCommand('copy');T.textContent='Copiado'};
}();
</script>