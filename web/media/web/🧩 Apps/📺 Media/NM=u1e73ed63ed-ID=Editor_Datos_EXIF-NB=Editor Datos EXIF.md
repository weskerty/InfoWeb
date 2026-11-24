<div style="text-align:center;position:relative;padding-top:0;margin-top:0" id="ex-app">
<style>
.EX0{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 18px;min-height:1.5em;overflow-wrap:break-word}
.EX1{border:1px dashed rgba(255,255,255,.25);border-radius:var(--r-md);padding:26px 16px;background:rgba(255,255,255,.04);cursor:pointer;transition:border-color .2s,background .2s}
.EX1:hover,.EX1.on{border-color:rgba(var(--accent-2-rgb),.6);background:rgba(var(--accent-2-rgb),.08)}
.EX1 p{margin:6px 0 0;color:rgba(255,255,255,.5);font-size:.85em}
.EX2{display:grid;grid-template-columns:repeat(auto-fit,minmax(142px,1fr));gap:10px;text-align:left;margin-bottom:12px}
.EX3{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.09);border-radius:var(--r-sm);padding:10px 12px}
.EX3 b{display:block;font-size:.72rem;color:rgba(255,255,255,.5);font-weight:400;letter-spacing:.03em;margin-bottom:3px}
.EX3 span{font-size:1rem;font-weight:600;overflow-wrap:break-word}
.EX4{display:grid;gap:3px;text-align:left;margin-bottom:8px}
.EX4 label{font-size:.72rem;color:rgba(255,255,255,.5);letter-spacing:.03em}
.EX4 input{width:100%;font-size:.85em}
.EX4 input[readonly]{opacity:.55}
.EX5{font-family:monospace;font-size:.72rem;text-align:left;white-space:pre;overflow-x:auto;background:rgba(0,0,0,.3);border-radius:10px;padding:10px;margin:0 0 10px;color:rgba(255,255,255,.75);max-height:36vh;overflow-y:auto}
.EX6{text-align:left;font-family:monospace;font-size:.78rem;max-height:46vh;overflow:auto;border:1px solid rgba(255,255,255,.09);border-radius:var(--r-sm);background:rgba(0,0,0,.2)}
.EX6 div{padding:4px 8px;cursor:pointer;border-bottom:1px solid rgba(255,255,255,.05);white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.EX6 div:hover{background:rgba(255,255,255,.07)}
.EX6 div.on{background:rgba(var(--accent-2-rgb),.18)}
.EX6 i{color:rgba(255,255,255,.4);font-style:normal}
.EX7{color:rgba(255,255,255,.45);font-size:.8em;margin:10px 0 0}
.EX8{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:14px 0 4px}
.EX9{font-family:monospace;font-size:.78rem;width:100%;min-height:120px;resize:vertical;white-space:pre;overflow-wrap:normal}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🏷️</div>
<div class="EX0" id="ex-st">Editor de Metadatos</div>

<div class="EX1" id="ex-drop">
<div style="font-size:2rem;line-height:1">📂</div>
<b>Elegi uno o varios archivos, o arrastralos aca</b>
<p>Foto, video, audio, PDF. Con varios se limpian todos de una. Nada sale de tu equipo.</p>
</div>
<input type="file" id="ex-in" multiple style="display:none">
<div class="EX8"><button id="ex-dir">📁 Limpiar una carpeta entera</button></div>

<div id="ex-body" class="hide">

<div class="EX2" id="ex-info"></div>

<details open>
<summary>✏️ Campos</summary>
<section>
<div id="ex-fields"></div>
<p class="EX7" id="ex-fnote"></p>
<div class="EX8"><input id="ex-ak" list="ex-al" placeholder="Campo (ej: Artist)" style="flex:1 1 140px"><input id="ex-av" placeholder="Valor" style="flex:2 1 180px"><button id="ex-ab">➕ Agregar</button></div>
<datalist id="ex-al"><option value="Artist"><option value="Copyright"><option value="ImageDescription"><option value="Title"><option value="Author"><option value="Comment"><option value="Keywords"><option value="DateTimeOriginal"><option value="Make"><option value="Model"><option value="GPSPosition"></datalist>
</section>
</details>

<details open>
<summary>🧱 Estructura</summary>
<section>
<div class="EX6" id="ex-tree"></div>
<p class="EX7">Cada fila es un bloque real del archivo. Toca uno para verlo y editarlo en crudo.</p>
</section>
</details>

<details>
<summary>🔬 Crudo</summary>
<section>
<div id="ex-hnone" class="EX7">Elegi un bloque en Estructura.</div>
<div id="ex-hwrap" class="hide">
<pre class="EX5" id="ex-dump"></pre>
<textarea class="EX9" id="ex-hex" spellcheck="false"></textarea>
<p class="EX7">Se muestran hasta 4 KB. Al aplicar tiene que quedar la misma cantidad de bytes: si cambia, se corren los tamanos del contenedor y el archivo queda roto.</p>
<div class="EX8"><button id="ex-hap">Aplicar al bloque</button></div>
</div>
</section>
</details>

<div class="EX8">
<button id="ex-save">💾 Guardar cambios</button>
<button id="ex-geo">📍 Quitar ubicacion</button>
<button id="ex-strip">🧹 Borrar todo</button>
<button id="ex-dl">⬇️ Descargar</button>
</div>
<p class="EX7" id="ex-note"></p>

</div>


<script>
(function(){
  const $=i=>document.getElementById(i);
  if(!$('ex-drop'))return;

  const ETU='https://cdn.jsdelivr.net/npm/@uswriting/exiftool@1.0.9/+esm';
  const ETW='https://cdn.jsdelivr.net/npm/@6over3/zeroperl-ts@1.0.10/dist/esm/zeroperl.wasm';
  const MBL='https://cdn.jsdelivr.net/npm/mediabunny@1.66.3/dist/bundles/mediabunny.min.mjs';
  const PDL='https://cdn.jsdelivr.net/npm/pdf-lib@1.17.1/dist/pdf-lib.esm.min.js';
  const ETF=()=>fetch(ETW);
  const RO=new Set(['File','Composite','JFIF','RIFF','MPEG']);
  const RS=/^(ImageWidth|ImageHeight|BitDepth|ColorType|Compression|Filter|Interlace)$/;
  const LOC=/GPS|Location|GeoTag/i;
  const SA=['-all=','--icc_profile:all','-tagsfromfile','@','-Orientation'];
  const MBF={mp3:'Mp3',flac:'Flac',ogg:'Ogg',wav:'Wav'};
  const MBK={Title:'title',Artist:'artist',Album:'album',Comment:'comment',Genre:'genre',Description:'description'};
  const PDK={Title:'Title',Author:'Author',Subject:'Subject',Keywords:'Keywords',Creator:'Creator',Producer:'Producer'};
  const WK=(fm,nm)=>fm==='pdf'?'pdf':(MBF[fm]||fm==='mkv')?'mb':'et';
  let ETP=null;
  const ETL=()=>ETP||(ETP=import(ETU).catch(e=>{ETP=null;throw e}));

  let U=null,NM='',MT='',FM='',BK=[],SL=-1,RW=[],GP=null;

  const CH=(u,p,n)=>{let s='';for(let i=0;i<n;i++)s+=String.fromCharCode(u[p+i]);return s};
  const F=n=>{const x=['B','KB','MB','GB'];let i=0;n=Math.abs(n);while(n>=1024&&i<3){n/=1024;i++}return (i?n.toFixed(n<10?2:1):Math.round(n))+' '+x[i]};
  const msg=t=>{$('ex-st').textContent=t};
  const note=t=>{$('ex-note').textContent=t};

  function FMT(u){
    const s=CH(u,0,12);
    if(u[0]===0xFF&&u[1]===0xD8)return 'jpeg';
    if(u[0]===0x89&&s.slice(1,4)==='PNG')return 'png';
    if(s.slice(0,4)==='RIFF')return s.slice(8,12)==='WEBP'?'webp':(s.slice(8,12)==='WAVE'?'wav':'riff');
    if(CH(u,4,4)==='ftyp'){const b=CH(u,8,4);return (b==='heic'||b==='heix'||b==='mif1')?'heic':(b==='avif'?'avif':'mp4')}
    if(u[0]===0x1A&&u[1]===0x45&&u[2]===0xDF&&u[3]===0xA3)return 'mkv';
    if(s.slice(0,3)==='ID3')return 'mp3';
    if(s.slice(0,4)==='fLaC')return 'flac';
    if(s.slice(0,4)==='OggS')return 'ogg';
    if(s.slice(0,3)==='GIF')return 'gif';
    if(s.slice(0,2)==='II'||s.slice(0,2)==='MM')return 'tiff';
    if(s.slice(0,4)==='%PDF')return 'pdf';
    if(u[0]===0xFF&&(u[1]&0xE0)===0xE0)return 'mp3';
    return 'bin';
  }
  const ISO=f=>f==='mp4'||f==='heic'||f==='avif';

  const JM={0xC0:'SOF0',0xC1:'SOF1',0xC2:'SOF2',0xC4:'DHT',0xDB:'DQT',0xDA:'SOS',0xDD:'DRI',0xFE:'COM'};
  function JL(u,p,m,l){
    if(m<0xE0||m>0xEF)return '';
    const t=CH(u,p+4,Math.min(Math.max(l-2,0),26));
    if(t.indexOf('Exif')===0)return 'EXIF';
    if(t.indexOf('http://ns.adobe.com/xap')===0)return 'XMP';
    if(t.indexOf('Photoshop')===0)return 'IPTC';
    if(t.indexOf('ICC_PROFILE')===0)return 'ICC';
    if(t.indexOf('JFIF')===0)return 'JFIF';
    if(t.indexOf('Adobe')===0)return 'Adobe';
    if(t.indexOf('http://ns.google.com')===0)return 'Google';
    return '';
  }

  const PNL={IHDR:'Cabecera',PLTE:'Paleta',IDAT:'Imagen',IEND:'Fin',tEXt:'Texto',zTXt:'Texto comprimido',iTXt:'Texto UTF-8',eXIf:'EXIF',tIME:'Fecha',iCCP:'ICC',pHYs:'Resolucion',gAMA:'Gamma',sRGB:'sRGB',tRNS:'Transparencia',acTL:'Animacion'};

  const BCONT=new Set(['moov','trak','mdia','minf','stbl','udta','edts','dinf','ilst','moof','traf','mvex','tref','iprp','ipco','meta']);
  const ID3L={TIT2:'Titulo',TPE1:'Artista',TALB:'Album',TYER:'Ano',TDRC:'Fecha',TCON:'Genero',COMM:'Comentario',TRCK:'Pista',TPE2:'Artista del album',TCOM:'Compositor',APIC:'Caratula',TENC:'Codificado por',TSSE:'Programa',TPOS:'Disco',TCOP:'Copyright'};
  const MP4L={'©nam':'Titulo','©ART':'Artista','©alb':'Album','©day':'Fecha','©cmt':'Comentario','©gen':'Genero','©too':'Programa','©wrt':'Compositor',desc:'Descripcion',ldes:'Descripcion larga',covr:'Caratula',aART:'Artista del album'};
  const EBL={0x1A45DFA3:'EBML',0x18538067:'Segmento',0x1549A966:'Info',0x1654AE6B:'Pistas',0xAE:'Pista',0x1254C367:'Etiquetas',0x7373:'Etiqueta',0x67C8:'Campo',0x45A3:'Nombre',0x4487:'Valor',0x1F43B675:'Cluster',0x114D9B74:'Indice',0x1C53BB6B:'Cues',0x1941A469:'Adjuntos',0x1043A770:'Capitulos',0x7BA9:'Titulo',0x4D80:'Programa',0x5741:'Aplicacion',0x4461:'Fecha'};
  const EMAS=new Set([0x1A45DFA3,0x18538067,0x1549A966,0x1654AE6B,0xAE,0x1254C367,0x7373,0x67C8,0x1941A469,0x1043A770]);

  function vint(u,p,keep){
    const b=u[p];
    if(b===undefined||b===0)return null;
    let m=0x80,n=1;
    while(n<=8&&!(b&m)){m>>=1;n++}
    if(n>8)return null;
    let v=keep?b:(b&(m-1));
    for(let i=1;i<n;i++)v=v*256+u[p+i];
    return {v,n};
  }

  function scan(u,fm){
    const o=[],dv=new DataView(u.buffer,u.byteOffset,u.byteLength);
    if(fm==='jpeg'){
      o.push({off:0,len:2,hd:2,type:'SOI',label:'Inicio',d:0});
      let p=2;
      while(p<u.length-1){
        if(u[p]!==0xFF){p++;continue}
        const m=u[p+1];
        if(m===0xFF){p++;continue}
        if(m===0x01||(m>=0xD0&&m<=0xD7)){p+=2;continue}
        if(m===0xD9){o.push({off:p,len:2,hd:2,type:'EOI',label:'Fin',d:0});break}
        if(p+4>u.length)break;
        const l=(u[p+2]<<8)|u[p+3];
        if(l<2||p+2+l>u.length)break;
        const nm=JM[m]||(m>=0xE0&&m<=0xEF?'APP'+(m-0xE0):'0x'+m.toString(16));
        o.push({off:p,len:l+2,hd:4,type:nm,label:JL(u,p,m,l),d:0});
        if(m===0xDA){
          let q=p+2+l;
          while(q<u.length-1&&!(u[q]===0xFF&&u[q+1]===0xD9))q++;
          o.push({off:p+2+l,len:q-(p+2+l),hd:0,type:'DATOS',label:'Imagen comprimida',d:0});
          p=q;continue;
        }
        p+=2+l;
      }
    } else if(fm==='png'){
      o.push({off:0,len:8,hd:8,type:'PNG',label:'Firma',d:0});
      let p=8;
      while(p+12<=u.length){
        const l=dv.getUint32(p),t=CH(u,p+4,4);
        if(p+l+12>u.length)break;
        o.push({off:p,len:l+12,hd:8,type:t,label:PNL[t]||'',d:0});
        p+=l+12;
        if(t==='IEND')break;
      }
    } else if(fm==='webp'||fm==='wav'||fm==='riff'){
      o.push({off:0,len:12,hd:12,type:CH(u,8,4),label:'Contenedor RIFF',d:0});
      let p=12;
      while(p+8<=u.length){
        const t=CH(u,p,4),l=dv.getUint32(p+4,true);
        if(p+8+l>u.length)break;
        o.push({off:p,len:l+8,hd:8,type:t,label:'',d:1});
        p+=8+l+(l&1);
      }
    } else if(ISO(fm)){
      (function bx(st,en,d,pt){
        let p=st;
        while(p+8<=en){
          let l=dv.getUint32(p),t=CH(u,p+4,4),h=8;
          if(l===1){if(p+16>en)break;l=Number(dv.getBigUint64(p+8));h=16}
          else if(l===0)l=en-p;
          if(l<h||p+l>en)break;
          o.push({off:p,len:l,hd:h,type:t,label:MP4L[t]||'',d,path:pt+'/'+t});
          if(t==='meta')bx(p+h+4,p+l,d+1,pt+'/'+t);
          else if(BCONT.has(t))bx(p+h,p+l,d+1,pt+'/'+t);
          else if(pt.slice(-4)==='ilst')bx(p+h,p+l,d+1,pt+'/'+t);
          p+=l;
        }
      })(0,u.length,0,'');
    } else if(fm==='mkv'){
      (function eb(st,en,d){
        let p=st,g=0;
        while(p<en&&g<600){
          const i=vint(u,p,true);
          if(!i)break;
          const s=vint(u,p+i.n,false);
          if(!s)break;
          const hd=i.n+s.n;
          let l=s.v;
          if(l>en-p-hd)l=en-p-hd;
          o.push({off:p,len:hd+l,hd,type:'0x'+i.v.toString(16).toUpperCase(),label:EBL[i.v]||'',d});
          if(EMAS.has(i.v)&&d<5)eb(p+hd,p+hd+l,d+1);
          p+=hd+l;g++;
        }
      })(0,u.length,0);
    } else if(fm==='mp3'){
      let end=0;
      if(CH(u,0,3)==='ID3'){
        const sz=((u[6]&127)<<21)|((u[7]&127)<<14)|((u[8]&127)<<7)|(u[9]&127);
        end=Math.min(10+sz,u.length);
        o.push({off:0,len:end,hd:10,type:'ID3v2.'+u[3],label:'Etiqueta',d:0});
        const v4=u[3]>=4;
        let p=10;
        while(p+10<=end){
          const id=CH(u,p,4);
          if(!/^[A-Z0-9]{4}$/.test(id))break;
          const fs=v4?(((u[p+4]&127)<<21)|((u[p+5]&127)<<14)|((u[p+6]&127)<<7)|(u[p+7]&127)):(((u[p+4]<<24)|(u[p+5]<<16)|(u[p+6]<<8)|u[p+7])>>>0);
          if(fs<0||p+10+fs>end)break;
          o.push({off:p,len:10+fs,hd:10,type:id,label:ID3L[id]||'',d:1});
          p+=10+fs;
        }
      }
      const tg=u.length-128;
      const au=tg>0&&CH(u,tg,3)==='TAG'?tg:u.length;
      o.push({off:end,len:au-end,hd:0,type:'AUDIO',label:'Audio',d:0});
      if(au<u.length)o.push({off:au,len:128,hd:3,type:'ID3v1',label:'Etiqueta vieja',d:0});
    } else if(fm==='flac'){
      o.push({off:0,len:4,hd:4,type:'fLaC',label:'Firma',d:0});
      const FB=['STREAMINFO','PADDING','APPLICATION','SEEKTABLE','VORBIS_COMMENT','CUESHEET','PICTURE'];
      let p=4;
      while(p+4<=u.length){
        const last=u[p]&0x80,ty=u[p]&0x7f,l=(u[p+1]<<16)|(u[p+2]<<8)|u[p+3];
        if(p+4+l>u.length)break;
        o.push({off:p,len:4+l,hd:4,type:FB[ty]||('BLOQUE'+ty),label:'',d:0});
        p+=4+l;
        if(last)break;
      }
      o.push({off:p,len:u.length-p,hd:0,type:'AUDIO',label:'Audio',d:0});
    } else if(fm==='gif'){
      o.push({off:0,len:Math.min(13,u.length),hd:13,type:CH(u,0,6),label:'Cabecera',d:0});
    }
    if(!o.length)o.push({off:0,len:u.length,hd:0,type:'ARCHIVO',label:'Sin estructura conocida',d:0});
    return o;
  }

  function tree(){
    const t=$('ex-tree');t.textContent='';
    BK.forEach((b,i)=>{
      const d=document.createElement('div');
      d.style.paddingLeft=(8+b.d*16)+'px';
      const n=document.createElement('span');
      n.textContent=b.type+' ';
      const e=document.createElement('i');
      e.textContent=(b.label?b.label+' ':'')+'· '+F(b.len);
      d.appendChild(n);d.appendChild(e);
      d.onclick=()=>{SL=i;tree();hex()};
      if(i===SL)d.className='on';
      t.appendChild(d);
    });
  }

  function hex(){
    if(SL<0||!BK[SL]){$('ex-hnone').classList.remove('hide');$('ex-hwrap').classList.add('hide');return}
    $('ex-hnone').classList.add('hide');$('ex-hwrap').classList.remove('hide');
    const b=BK[SL],n=Math.min(b.len,4096);
    let d='',h='';
    for(let i=0;i<n;i+=16){
      let a='',x='';
      for(let j=0;j<16;j++){
        if(i+j<n){const v=U[b.off+i+j];x+=v.toString(16).padStart(2,'0')+' ';a+=(v>=32&&v<127)?String.fromCharCode(v):'.'}
        else x+='   ';
      }
      d+=(b.off+i).toString(16).padStart(8,'0')+'  '+x+' '+a+'\n';
      h+=x.trim()+'\n';
    }
    $('ex-dump').textContent=d;
    $('ex-hex').value=h.trim();
  }

  function hap(){
    if(SL<0)return;
    const b=BK[SL],n=Math.min(b.len,4096);
    const t=$('ex-hex').value.trim().split(/[^0-9a-fA-F]+/).filter(Boolean);
    if(t.length!==n){note('Error Crudo: hay '+t.length+' bytes y hacen falta '+n);return}
    const v=new Uint8Array(n);
    for(let i=0;i<n;i++){
      const x=parseInt(t[i],16);
      if(isNaN(x)||x>255){note('Error Crudo: byte invalido en la posicion '+i);return}
      v[i]=x;
    }
    U.set(v,b.off);
    note('Bloque aplicado. Falta descargar.');
    load(U,NM,MT,true);
  }

  const EN=nm=>'a'+((nm.match(/\.[A-Za-z0-9]{1,6}$/)||[''])[0]).toLowerCase();

  async function ER(u,nm){
    const E=await ETL();
    const r=await E.parseMetadata({name:EN(nm),data:u},{fetch:ETF,args:['-j','-G1','-a','-s','-sep',', ','-c','%+.6f','-m','-q','-q'],transform:d=>JSON.parse(d)[0]});
    if(!r.success){E.dispose().catch(()=>{});throw new Error(r.error)}
    return r.data;
  }

  async function PW(u,tags,all){
    const P=await import(PDL);
    const d=await P.PDFDocument.load(u,{updateMetadata:false}),c=d.context,N=P.PDFName.of('Metadata');
    if(all){
      const ir=c.trailerInfo.Info;
      if(ir){c.delete(ir);c.trailerInfo.Info=undefined}
      const m=d.catalog.get(N);
      if(m){if(m instanceof P.PDFRef)c.delete(m);d.catalog.delete(N)}
      const sn=new Set(),st=[c.trailerInfo.Root];
      while(st.length){
        const o=st.pop();
        if(o instanceof P.PDFRef){if(!sn.has(o.tag)){sn.add(o.tag);const x=c.lookup(o);if(x)st.push(x)}}
        else if(o instanceof P.PDFDict){for(const [,v] of o.entries())st.push(v)}
        else if(o instanceof P.PDFArray)st.push(...o.asArray());
        else if(o instanceof P.PDFStream)st.push(o.dict);
      }
      for(const [r] of c.enumerateIndirectObjects())if(!sn.has(r.tag))c.delete(r);
    }
    for(const k in tags){
      const f=PDK[k.split(':').pop()];
      if(!f)continue;
      const v=tags[k];
      if(!v){const i=c.trailerInfo.Info&&c.lookup(c.trailerInfo.Info);if(i)i.delete(P.PDFName.of(f))}
      else d['set'+f](f==='Keywords'?v.split(',').map(s=>s.trim()):v);
    }
    return d.save({useObjectStreams:false});
  }

  async function MW(u,nm,tags,all){
    const MB=await import(MBL),fm=FMT(u),of=fm==='mkv'?(/\.webm$/i.test(nm)?'WebM':'Mkv'):MBF[fm];
    const out=new MB.Output({format:new MB[of+'OutputFormat'](),target:new MB.BufferTarget()});
    const cv=await MB.Conversion.init({input:new MB.Input({source:new MB.BufferSource(u),formats:MB.ALL_FORMATS}),output:out,copy:{shiftTolerance:1},tags:all?{creationTime:null}:t=>{
      const o={...t,raw:{...(t.raw||{})}};
      for(const k in tags){
        const n=k.split(':').pop();
        if(MBK[n])o[MBK[n]]=tags[k]||undefined;
        else if(LOC.test(n))for(const r in o.raw)if(LOC.test(r))delete o.raw[r];
      }
      return o;
    }});
    if(!cv.isValid)throw new Error('formato no soportado');
    await cv.execute();
    return new Uint8Array(out.target.buffer);
  }

  async function EW(u,nm,tags,all){
    const kd=WK(FMT(u),nm);
    if(kd==='pdf')return PW(u,tags,all);
    if(kd==='mb')return MW(u,nm,tags,all);
    const E=await ETL();
    const r=await E.writeMetadata({name:EN(nm),data:u},tags,{fetch:ETF,args:['-m','-q','-q','-sep',', '].concat(all?SA:[])});
    if(!r.success){E.dispose().catch(()=>{});throw new Error(r.error)}
    return new Uint8Array(r.data);
  }

  async function readFields(){
    RW=[];GP=null;
    const o=await ER(U,NM),kd=WK(FM,NM);
    for(const k in o){
      const i=k.indexOf(':'),g=i<0?'':k.slice(0,i),n=k.slice(i+1);
      if(i<0||g==='ExifTool'||g==='System')continue;
      let v=o[k];
      if(v&&typeof v==='object')v=JSON.stringify(v);
      v=String(v);
      if(k==='Composite:GPSPosition')GP=v;
      const ed=!/^\(Binary data/.test(v)&&(kd==='pdf'?!!PDK[n]:kd==='mb'?(FM!=='mkv'&&(!!MBK[n]||LOC.test(n))):!(RO.has(g)||/^Track\d+$/.test(g)||(g==='QuickTime'&&!/^(Create|Modify)Date$/.test(n))||(g==='PNG'&&RS.test(n))));
      RW.push({k,g,n,v,ed});
    }
    RW.sort((a,b)=>b.ed-a.ed);
  }

  function fields(){
    const c=$('ex-fields');c.textContent='';
    let g=null;
    RW.forEach(r=>{
      if(r.g!==g){g=r.g;const h=document.createElement('h3');h.textContent=g;c.appendChild(h)}
      const w=document.createElement('div');w.className='EX4';
      const l=document.createElement('label');l.textContent=r.n;
      const inp=document.createElement('input');
      inp.type='text';inp.value=r.v;
      if(!r.ed)inp.readOnly=true;
      else inp.oninput=()=>{r.v=inp.value;r.mod=true};
      w.appendChild(l);w.appendChild(inp);c.appendChild(w);
    });
    $('ex-fnote').textContent=FM==='mkv'?'MKV y WebM: solo se puede borrar todo (editar campo por campo perderia datos).':RW.some(r=>r.ed)?'Dejar un campo vacio lo borra. Los atenuados son de solo lectura.':'Este archivo no tiene metadatos editables. Se pueden agregar abajo.';
  }

  async function EA(tags,all,ok){
    msg('Escribiendo...');
    try{
      const u=await EW(U,NM,tags,all);
      await load(u,NM,MT,true);
      const has=k=>RW.some(r=>r.n===k.split(':').pop());
      const no=Object.keys(tags).filter(k=>tags[k]!==''&&!has(k)),qd=Object.keys(tags).filter(k=>tags[k]===''&&has(k));
      let t=no.length||qd.length?'':ok+' Falta descargar.';
      if(no.length)t='No se pudo escribir: '+no.join(', ')+' (el formato no lo admite). '+t;
      if(qd.length)t='No se pudo borrar: '+qd.join(', ')+'. '+t;
      note(t.trim());
    }catch(e){msg(NM);note('Error Escribir: '+((e&&e.message)||e))}
  }

  function save(){
    const t={};
    RW.forEach(r=>{if(r.mod&&r.ed)t[r.k]=r.v});
    if(!Object.keys(t).length){note('No hay cambios para guardar.');return}
    EA(t,false,'Cambios aplicados.');
  }

  function add(){
    if(FM==='mkv'){note('MKV y WebM: solo se puede borrar todo.');return}
    const k=$('ex-ak').value.trim(),v=$('ex-av').value;
    if(!/^[A-Za-z][A-Za-z0-9_-]*(:[A-Za-z][A-Za-z0-9_-]*)?$/.test(k)){note('Error Campo: nombre invalido');return}
    if(!v){note('Error Campo: falta el valor');return}
    EA({[k]:v},false,'Campo '+k+' agregado.');
  }

  function geo(){
    if(FM==='mkv'){note('MKV y WebM: solo se puede borrar todo.');return}
    const t={};
    RW.forEach(r=>{if(r.ed&&LOC.test(r.n))t[r.k]=''});
    if(!Object.keys(t).length){note('Este archivo no tiene ubicacion.');return}
    EA(t,false,'Ubicacion borrada.');
  }

  function doStrip(){
    EA({},true,'Metadatos borrados.');
  }

  function dl(u=U,nm=NM,mt=MT,suf='-editado'){
    const b=new Blob([u],{type:mt||'application/octet-stream'});
    const x=URL.createObjectURL(b);
    const a=document.createElement('a');
    a.href=x;a.download=nm.replace(/(\.[^.]+)?$/,suf+'$1');
    document.body.appendChild(a);a.click();a.remove();
    setTimeout(()=>URL.revokeObjectURL(x),15000);
  }

  function card(inf,k,v,href){
    const c=document.createElement('div');c.className='EX3';
    const b=document.createElement('b');b.textContent=k;
    const s=document.createElement(href?'a':'span');s.textContent=v;
    if(href){s.href=href;s.target='_blank';s.rel='noopener noreferrer'}
    c.appendChild(b);c.appendChild(s);inf.appendChild(c);
  }

  async function load(u,nm,mt,keep){
    U=u;NM=nm;MT=mt;FM=FMT(U);BK=scan(U,FM);
    if(!keep){SL=-1;note('')}
    if(SL>=BK.length)SL=-1;
    msg(nm);
    $('ex-body').classList.remove('hide');
    const inf=$('ex-info');inf.textContent='';
    for(const d of [['FORMATO',FM.toUpperCase()],['TAMANO',F(U.length)],['TIPO',mt||'desconocido'],['BLOQUES',String(BK.length)]])card(inf,d[0],d[1]);
    tree();hex();
    $('ex-fields').textContent='';
    $('ex-fnote').textContent=ETP?'Leyendo campos...':'Cargando ExifTool (5 MB, solo la primera vez)...';
    try{await readFields();fields()}
    catch(e){RW=[];$('ex-fnote').textContent='Error ExifTool: '+((e&&e.message)||e)}
    const p=GP&&GP.split(',').map(parseFloat);
    if(p&&p.length===2&&isFinite(p[0])&&isFinite(p[1]))card(inf,'UBICACION','📍 '+p[0].toFixed(5)+', '+p[1].toFixed(5),'https://www.openstreetmap.org/?mlat='+p[0]+'&mlon='+p[1]+'#map=16/'+p[0]+'/'+p[1]);
  }

  async function batch(fs){
    if(!confirm('Se van a borrar los metadatos de '+fs.length+' archivos y descargar cada uno limpio. Seguir?'))return;
    let ok=0,er=0;
    for(const f of fs){
      msg('Limpiando '+(ok+er+1)+' de '+fs.length+'...');
      try{dl(await EW(new Uint8Array(await f.arrayBuffer()),f.name,{},true),f.name,f.type,'-limpio');ok++}catch(e){er++}
    }
    msg('Lote listo');
    note('Limpiados '+ok+', con error '+er+'.');
  }

  async function pick(fs){
    if(!fs||!fs.length)return;
    if(fs.length>1){batch([...fs]);return}
    const f=fs[0];
    msg('Leyendo...');
    try{
      const ab=await f.arrayBuffer();
      await load(new Uint8Array(ab),f.name,f.type,false);
    }catch(e){msg('Error Leer');note(String((e&&e.message)||e))}
  }

  const dz=$('ex-drop'),fi=$('ex-in');
  dz.onclick=()=>fi.click();
  fi.onchange=()=>{pick(fi.files);fi.value=''};
  dz.addEventListener('dragover',e=>{e.preventDefault();dz.classList.add('on')});
  dz.addEventListener('dragleave',()=>dz.classList.remove('on'));
  dz.addEventListener('drop',e=>{e.preventDefault();dz.classList.remove('on');pick(e.dataTransfer.files)});

  $('ex-save').onclick=save;
  $('ex-geo').onclick=geo;
  $('ex-strip').onclick=doStrip;
  $('ex-dl').onclick=()=>dl();
  $('ex-ab').onclick=add;
  $('ex-hap').onclick=hap;

  $('ex-dir').onclick=async()=>{
    if(!window.showDirectoryPicker){note('Elegir carpeta solo anda en Chromium de escritorio.');return}
    let d;
    try{d=await window.showDirectoryPicker({mode:'readwrite'})}catch(e){return}
    if(!confirm('Se van a reescribir los archivos de esa carpeta sin copia de respaldo. Seguir?'))return;
    let ok=0,er=0;
    msg('Limpiando carpeta...');
    for await(const en of d.values()){
      if(en.kind!=='file')continue;
      try{
        const f=await en.getFile();
        const r=await EW(new Uint8Array(await f.arrayBuffer()),f.name,{},true);
        const w=await en.createWritable();
        await w.write(r);
        await w.close();
        ok++;
      }catch(e){er++}
    }
    msg('Carpeta lista');
    note('Limpiados '+ok+', con error '+er+'. Se reescribieron en el lugar.');
  };

  const cu=$('content');
  if(cu)cu.addEventListener('contentUnload',()=>{U=null;BK=[];RW=[];if(ETP)ETP.then(E=>E.dispose()).catch(()=>{})},{once:true});
})();
</script>

<br>
<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>
</div>
