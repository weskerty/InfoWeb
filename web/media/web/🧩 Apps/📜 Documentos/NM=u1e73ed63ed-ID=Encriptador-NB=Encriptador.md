<style>
#EN_W{max-width:560px;margin:0 auto;display:flex;flex-direction:column;gap:10px;text-align:center}
#EN_W :is(textarea,select,input){width:100%;box-sizing:border-box}
#EN_W .EN_R{display:flex;gap:8px;justify-content:center;flex-wrap:wrap}
#EN_M{margin:0;font-size:.8rem;opacity:.8}
</style>
<div id="EN_W">
<h2>Mensajes Secretos</h2>
<p>Cifra y descifra con codigos, simbolos o tu propio diccionario.</p>
<textarea id="EN_I" rows="5" placeholder="Mensaje"></textarea>
<select id="EN_S"></select>
<input id="EN_K" type="text" style="display:none">
<div class="EN_R"><button id="EN_E">Cifrar</button><button id="EN_D">Descifrar</button></div>
<textarea id="EN_O" rows="5" readonly placeholder="Resultado"></textarea>
<div class="EN_R"><button id="EN_C">Copiar</button><button id="EN_X">Usar como mensaje</button><button id="EN_L" title=".txt con símbolos separados por espacios">Cargar Diccionario</button></div>
<input id="EN_F" type="file" accept=".txt,.csv" hidden>
<p id="EN_M"></p>
</div>
<script>
!function(){
const $=i=>document.getElementById(i),I=$('EN_I'),O=$('EN_O'),S=$('EN_S'),K=$('EN_K'),T=$('EN_M');
const TE=new TextEncoder(),TD=new TextDecoder('utf-8',{fatal:true});
const B2=s=>[...TE.encode(s)],BS=b=>TD.decode(Uint8Array.from(b));
const B64=b=>btoa(b.map(x=>String.fromCharCode(x)).join('')),U64=s=>[...atob(s.trim())].map(x=>x.charCodeAt(0));
const RG=(s,n)=>Array.from({length:n},(_,i)=>String.fromCodePoint(s+i));
const CS=()=>{if(!crypto.subtle)throw'Requiere HTTPS'};
const HX=b=>[...new Uint8Array(b)].map(x=>x.toString(16).padStart(2,'0')).join('');
const RX=(b,p)=>[t=>B2(t).map(x=>x.toString(b).padStart(p,'0')).join(' '),t=>{const a=t.trim().split(/\s+/).map(x=>parseInt(x,b));if(a.some(x=>!(x>=0&&x<256)))throw'Formato';return BS(a)}];
const BN=al=>{
const N=BigInt(al.length),sp=al.every(s=>[...s].length==1)?'':' ',mp=new Map(al.map((s,i)=>[s,BigInt(i)]));
return[t=>{
if(t.length>8000)throw'Mensaje largo';
let n=BigInt('0x1'+B2(t).map(x=>x.toString(16).padStart(2,'0')).join('')),o=[];
while(n>0n){o.push(al[Number(n%N)]);n/=N}
return o.reverse().join(sp);
},t=>{
let n=0n;
for(const s of sp?t.trim().split(/\s+/):[...t.replace(/\s/g,'')]){if(!mp.has(s))throw'Simbolo';n=n*N+mp.get(s)}
const h=n.toString(16);
if(h[0]!='1')throw'Formato';
return BS((h.slice(1).match(/../g)||[]).map(x=>parseInt(x,16)));
}];
};
const SF=(t,f)=>{let i=0;return t.replace(/[a-z]/gi,c=>{const b=c<'a'?65:97;return String.fromCharCode(b+((c.charCodeAt(0)-b+f(i++))%26+26)%26)})};
const AT=t=>t.replace(/[a-z]/gi,c=>{const b=c<'a'?65:97;return String.fromCharCode(b+25-(c.charCodeAt(0)-b))});
const VG=(k,s)=>{k=k.replace(/[^a-z]/gi,'').toLowerCase();if(!k)throw'Clave';return t=>SF(t,i=>s*(k.charCodeAt(i%k.length)-97))};
const MO=Object.fromEntries('A .-|B -...|C -.-.|D -..|E .|F ..-.|G --.|H ....|I ..|J .---|K -.-|L .-..|M --|N -.|O ---|P .--.|Q --.-|R .-.|S ...|T -|U ..-|V ...-|W .--|X -..-|Y -.--|Z --..|0 -----|1 .----|2 ..---|3 ...--|4 ....-|5 .....|6 -....|7 --...|8 ---..|9 ----.|. .-.-.-|, --..--|? ..--..|! -.-.--'.split('|').map(s=>s.split(' ')));
const MR=Object.fromEntries(Object.entries(MO).map(([a,b])=>[b,a]));
const HS=a=>[async t=>{CS();return HX(await crypto.subtle.digest(a,TE.encode(t)))},()=>{throw'Hash no se puede revertir'},0];
const AK=async(p,s)=>{CS();const m=await crypto.subtle.importKey('raw',TE.encode(p),'PBKDF2',false,['deriveKey']);return crypto.subtle.deriveKey({name:'PBKDF2',salt:s,iterations:100000,hash:'SHA-256'},m,{name:'AES-GCM',length:256},false,['encrypt','decrypt'])};
const AE=async(t,k)=>{
if(!k)throw'Clave';
const s=crypto.getRandomValues(new Uint8Array(16)),v=crypto.getRandomValues(new Uint8Array(12)),c=new Uint8Array(await crypto.subtle.encrypt({name:'AES-GCM',iv:v},await AK(k,s),TE.encode(t)));
return B64([...s,...v,...c]);
};
const AD=async(t,k)=>{
if(!k)throw'Clave';
const b=Uint8Array.from(U64(t));
try{return TD.decode(await crypto.subtle.decrypt({name:'AES-GCM',iv:b.slice(16,28)},await AK(k,b.slice(0,16)),b.slice(28)))}catch(e){throw'Clave'}
};
const M=[
['Codigos','Base64',t=>B64(B2(t)),t=>BS(U64(t)),0],
['Codigos','URL',encodeURIComponent,decodeURIComponent,0],
['Codigos','Hexadecimal',...RX(16,2),0],
['Codigos','Binario',...RX(2,8),0],
['Codigos','Octal',...RX(8,3),0],
['Codigos','Decimal',...RX(10,0),0],
['Codigos','Morse',t=>t.normalize('NFD').replace(/[\u0300-\u036f]/g,'').toUpperCase().split(/\s+/).map(w=>[...w].map(c=>MO[c]).filter(Boolean).join(' ')).filter(Boolean).join(' / '),t=>t.trim().split(/\s*\/\s*/).map(w=>w.split(/\s+/).map(c=>MR[c]||'?').join('')).join(' '),0],
['Clasicos','Cesar',(t,k)=>SF(t,()=>+k||3),(t,k)=>SF(t,()=>-(+k||3)),1],
['Clasicos','ROT13',t=>SF(t,()=>13),t=>SF(t,()=>13),0],
['Clasicos','Atbash',AT,AT,0],
['Clasicos','Vigenere',(t,k)=>VG(k,1)(t),(t,k)=>VG(k,-1)(t),2],
['Simbolos','Emoji animales y objetos',...BN(RG(0x1F400,256)),0],
['Simbolos','Emoji caras',...BN(RG(0x1F600,80)),0],
['Simbolos','Jeroglificos',...BN(RG(0x13000,256)),0],
['Simbolos','Cuneiforme',...BN(RG(0x12000,256)),0],
['Simbolos','Runas',...BN(RG(0x16A0,75)),0],
['Simbolos','Braille',...BN(RG(0x2800,256)),0],
['Simbolos','Domino',...BN(RG(0x1F030,100)),0],
['Hash (solo cifrar)','SHA-1',...HS('SHA-1')],
['Hash (solo cifrar)','SHA-256',...HS('SHA-256')],
['Hash (solo cifrar)','SHA-512',...HS('SHA-512')],
['Seguro','AES-256 con clave',AE,AD,2]
];
function RO(){
const g={};
S.innerHTML='';
M.forEach((m,i)=>{const og=g[m[0]]||(g[m[0]]=S.appendChild(document.createElement('optgroup')));og.label=m[0];og.appendChild(new Option(m[1],i))});
}
function SK(){const k=M[S.value][4];K.style.display=k?'':'none';K.placeholder=k==1?'Desplazamiento (3)':'Clave'}
async function RN(d){
try{O.value=await M[S.value][d?3:2](I.value,K.value);T.textContent=''}
catch(e){O.value='Error '+(d?'Descifrar ':'Cifrar ')+(typeof e=='string'?e:'Formato')}
}
RO();
SK();
S.onchange=SK;
$('EN_E').onclick=()=>RN(0);
$('EN_D').onclick=()=>RN(1);
$('EN_C').onclick=()=>{O.select();navigator.clipboard?navigator.clipboard.writeText(O.value):document.execCommand('copy');T.textContent='Copiado'};
$('EN_X').onclick=()=>{I.value=O.value;O.value=''};
$('EN_L').onclick=()=>$('EN_F').click();
$('EN_F').onchange=async e=>{
const f=e.target.files[0];
if(!f)return;
const al=[...new Set((await f.text()).split(/[\s,]+/).filter(Boolean))];
e.target.value='';
if(al.length<2){T.textContent='Error Diccionario minimo 2 simbolos';return}
M.push(['Mi diccionario',`${f.name} (${al.length})`,...BN(al),0]);
RO();
S.value=M.length-1;
SK();
T.textContent='Diccionario cargado '+al.length+' simbolos';
};
}();
</script>