<style>
.nv-top{padding:16px 4px;display:flex;align-items:center;gap:12px;border-bottom:1px solid rgba(255,255,255,.13);margin-bottom:16px}
.nv-top h3{margin:0}
.nv-top>div{flex:1;min-width:0}
.nv-top span{font-size:.78em;color:rgba(255,255,255,.5);display:block;margin-top:2px}
.nv-sec{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.09);border-radius:var(--r-md);padding:16px;margin-bottom:14px}
.nv-sec h4{margin:0 0 10px;font-size:.78em;color:rgba(255,255,255,.5);text-transform:uppercase;letter-spacing:.08em;border:none;padding:0}
.nv-fg{margin-bottom:0}
.nv-fg input{width:100%}
#nv-list .BMD1{cursor:pointer}
.NV_I1{width:58px;height:58px;display:flex;align-items:center;justify-content:center;font-size:1.7em;flex-shrink:0}
.NV_F1{position:absolute;width:1px;height:1px;opacity:0;overflow:hidden;border:0;padding:0}
.nv-empty{text-align:center;color:rgba(255,255,255,.5);padding:30px 10px;font-size:.9em}
.nv-nr{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
.nv-nr .nv-fg{flex:1;min-width:120px}
.nv-recbar{display:flex;gap:6px;flex-shrink:0}
.nv-recst{text-align:center;font-size:.8em;color:rgba(255,255,255,.5);margin-top:6px;min-height:1.2em}
.nv-recst.on{color:#f87171}
.BS2-CN{width:40px;height:40px;padding:0;margin:0;border-radius:var(--r-sm)}
.BS2-CN .BS4{font-size:1.3em}
.nv-savest{text-align:center;font-size:.72em;color:rgba(255,255,255,.4);margin-top:6px}
.nv-msg{position:fixed;bottom:26px;left:50%;transform:translateX(-50%);background:rgba(20,20,25,.92);border:1px solid rgba(255,255,255,.15);border-radius:30px;padding:9px 18px;font-size:.82em;color:#fff;z-index:9999;pointer-events:none;white-space:nowrap;max-width:88vw;overflow:hidden;text-overflow:ellipsis}
.nv-msg.err{border-color:rgba(248,113,113,.5);color:#fca5a5}
.nv-msg.warn{border-color:rgba(251,191,36,.5);color:#fbbf24}
.nv-read{padding:0 2px}
.nv-read img{border-radius:var(--r-sm);display:block;margin:8px 0}
.nv-read audio,.nv-read video{width:100%;display:block;margin:10px 0}
#nv-mde{margin-bottom:14px}
#nv-mde .EasyMDEContainer{background:transparent!important;border-radius:10px;overflow:hidden}
#nv-mde .CodeMirror{background:rgba(255,255,255,.04)!important;color:#fff!important;height:auto!important;min-height:160px;border-radius:0 0 10px 10px!important;border:1px solid rgba(255,255,255,.15)!important;border-top:none!important}
#nv-mde .CodeMirror-scroll{overflow:visible!important;height:auto!important}
#nv-mde .CodeMirror-cursor{border-color:#fff!important}
#nv-mde .editor-toolbar{background:rgba(255,255,255,.04)!important;border:1px solid rgba(255,255,255,.15)!important;border-bottom:none!important;border-radius:10px 10px 0 0!important}
#nv-mde .editor-toolbar button{color:rgba(255,255,255,.6)!important;background:transparent!important}
#nv-mde .editor-toolbar button:hover,#nv-mde .editor-toolbar button.active{background:rgba(255,255,255,.1)!important}
</style>

<div id="nv-scr-list">
  <div class="nv-top">
    <div><h3>Notas de Voz</h3><span>Tu bitacora Personal.</span></div>
  </div>
  <div class="BS1" style="margin-bottom:16px">
    <div class="BS2" id="nv-add"><div class="BS3"><span class="BS4">➕</span><p class="BS5">Añadir</p></div></div>
  </div>
  <div id="nv-list"><div class="nv-empty">Cargando...</div></div>
</div>

<div id="nv-scr-read" style="display:none">
  <div class="nv-top">
    <button class="back-button" id="nvr-back">←</button>
    <div style="flex:1"><h3 id="nvr-name">Nota</h3><span id="nvr-date"></span></div>
    <div class="BS1" style="margin:0"><div class="BS2" id="nvr-edit" style="width:44px;height:44px"><div class="BS3"><span class="BS4" style="font-size:1.5em">✏️</span></div></div></div>
  </div>
  <div class="nv-read" id="nvr-body"></div>
</div>

<div id="nv-scr-edit" style="display:none">
  <div class="nv-top">
    <button class="back-button" id="nv-back">←</button>
    <div><h3>Editar Entrada</h3><span>Expresate</span></div>
  </div>

  <div class="nv-sec">
    <div class="nv-nr">
      <div class="nv-fg" id="ne-namewrap"><input id="ne-name" type="text" placeholder="Nombre de la Nota" maxlength="80"></div>
      <div class="nv-recbar">
        <div class="BS2 BS2-CN" id="ne-battach" title="Adjuntar imagen o video"><div class="BS3"><span class="BS4">📎</span></div></div>
        <div class="BS2 BS2-CN" id="ne-brec" title="Grabar"><div class="BS3"><span class="BS4">⏺️</span></div></div>
        <div class="BS2 BS2-CN" id="ne-bpause" title="Pausar" style="display:none"><div class="BS3"><span class="BS4">⏸️</span></div></div>
        <div class="BS2 BS2-CN" id="ne-bresume" title="Reanudar" style="display:none"><div class="BS3"><span class="BS4">▶️</span></div></div>
        <div class="BS2 BS2-CN" id="ne-bstop" title="Detener y guardar" style="display:none"><div class="BS3"><span class="BS4">⏹️</span></div></div>
      </div>
    </div>
    <div class="nv-recst" id="ne-recst"></div>
  </div>

  <div id="nv-mde">
    <input type="file" id="ne-filein" class="NV_F1" accept="image/*,video/*,audio/*" multiple>
    <textarea id="ne-mdtxt"></textarea>
    <div class="nv-savest" id="ne-savest"></div>
  </div>

  <div class="BS1">
    <div class="BS2" id="ne-save"><div class="BS3"><span class="BS4">💾</span><p class="BS5">Guardar</p></div></div>
    <div class="BS2" id="ne-del"><div class="BS3"><span class="BS4">🗑️</span><p class="BS5">Borrar</p></div></div>
  </div>
</div>

<div class="nv-msg" id="nv-toast" style="display:none"></div>

<script>
(function(){
  const _self=document.currentScript;
  const SAVE_DEBOUNCE=1000;
  const MAX_SIZE=10*1024*1024;
  const LIB_DP={k:'js',local:'web/js/lib/DOMPurify/purify.min.js',cdn:'https://cdn.jsdelivr.net/npm/dompurify@3/dist/purify.min.js',check:()=>window.DOMPurify};
  const LIBS=[
    {k:'css',local:'web/js/lib/EasyMDE/easymde.min.css',cdn:'https://cdn.jsdelivr.net/npm/easymde@2/dist/easymde.min.css'},
    {k:'js',local:'web/js/lib/EasyMDE/easymde.min.js',cdn:'https://cdn.jsdelivr.net/npm/easymde@2/dist/easymde.min.js',check:()=>window.EasyMDE},
    LIB_DP
  ];
  function loadLib(l){
    return new Promise(res=>{
      if(l.check&&l.check())return res();
      if(l.k==='css'){
        if(document.querySelector('link[data-nvlib="'+l.local+'"]'))return res();
        const e=document.createElement('link');
        e.rel='stylesheet';e.dataset.nvlib=l.local;e.href=l.local;
        e.onload=res;
        e.onerror=()=>{e.onerror=null;e.onload=res;e.href=l.cdn;};
        document.head.appendChild(e);
      }else{
        const e=document.createElement('script');
        e.src=l.local;
        e.onload=res;
        e.onerror=()=>{
          e.onerror=res;e.onload=res;
          const c=document.createElement('script');
          c.src=l.cdn;c.onload=res;c.onerror=res;
          document.head.appendChild(c);
        };
        document.head.appendChild(e);
      }
    });
  }
  const libsReady=Promise.all(LIBS.map(loadLib));

  const scrList=document.getElementById('nv-scr-list'),scrEdit=document.getElementById('nv-scr-edit'),scrRead=document.getElementById('nv-scr-read');
  let dirH=null,mde=null,mediaRec=null,mediaStream=null,curId=null,saveTO=null,readBlobs=[];
  let mdReader=null;
  const tEl=document.getElementById('nv-toast');
  let _tt;

  function toast(t,tp,d){
    tp=tp||'ok';d=d||2500;
    tEl.className='nv-msg'+(tp!=='ok'?' '+tp:'');
    tEl.textContent=t;tEl.style.display='block';
    clearTimeout(_tt);
    _tt=setTimeout(()=>{tEl.style.display='none';},d);
  }

  const _hasOPFS=typeof navigator.storage?.getDirectory==='function'
    &&typeof FileSystemFileHandle!=='undefined'
    &&typeof FileSystemFileHandle.prototype.createWritable==='function';

  async function NV_W1(dir,name,data){
    const fh=await dir.getFileHandle(name,{create:true});
    const w=await fh.createWritable();
    await w.write(data);
    await w.close();
  }
  function NV_E1(q,e){
    toast('Error '+q+': '+((e&&e.message)||e),'err',4500);
  }
  const _hasRec=typeof MediaRecorder!=='undefined'&&!!(navigator.mediaDevices&&navigator.mediaDevices.getUserMedia);

  async function getNVRoot(){
    const root=await navigator.storage.getDirectory();
    const apps=await root.getDirectoryHandle('Apps',{create:true});
    return await apps.getDirectoryHandle('NotasVoz',{create:true});
  }

  function fmtDate(ts){
    const d=new Date(ts);
    return d.toLocaleDateString('es-PY',{day:'2-digit',month:'short',year:'numeric'})+' '+d.toLocaleTimeString('es-PY',{hour:'2-digit',minute:'2-digit'});
  }

  function showScreen(s){
    scrList.style.display=s==='list'?'block':'none';
    scrEdit.style.display=s==='edit'?'block':'none';
    scrRead.style.display=s==='read'?'block':'none';
  }

  async function loadList(){
    const listEl=document.getElementById('nv-list');
    if(!_hasOPFS){listEl.innerHTML='<div class="nv-empty">Tu navegador no es compatible con el Sistema de Archivos Privado o no concediste permisos.</div>';return;}
    listEl.innerHTML='<div class="nv-empty">Cargando...</div>';
    try{
      const nv=await getNVRoot();
      const items=[];
      for await(const[name,handle]of nv.entries()){
        if(handle.kind!=='directory')continue;
        let nombre=name,fecha=0,naudios=0;
        try{
          const f=await handle.getFileHandle('info.json');
          const j=JSON.parse(await (await f.getFile()).text());
          nombre=j.nombre||name;fecha=j.fecha||0;
        }catch(e){}
        for await(const[n2,h2]of handle.entries()){
          if(h2.kind==='file'&&/^audio-\d+\./.test(n2))naudios++;
        }
        items.push({id:name,nombre:nombre,fecha:fecha,naudios:naudios});
      }
      items.sort((a,b)=>b.fecha-a.fecha||b.id.localeCompare(a.id));
      if(!items.length){listEl.innerHTML='<div class="nv-empty">Sin notas.<br>Toca "Añadir" para crear la primera.</div>';return;}
      listEl.innerHTML='';
      items.forEach(it=>{
        const div=document.createElement('div');div.className='BMD1';
        div.innerHTML='<span class="NV_I1">🎙️</span><div class="BMD1-CN"><h3></h3><p></p></div>';
        div.querySelector('h3').textContent=it.nombre;
        div.querySelector('p').textContent=(it.fecha?fmtDate(it.fecha):'')+(it.naudios?' · '+it.naudios+' audio'+(it.naudios>1?'s':''):' · sin audio');
        div.onclick=()=>openReader(it.id);
        listEl.appendChild(div);
      });
    }catch(e){
      listEl.innerHTML='<div class="nv-empty">Error: '+e.message+'</div>';
    }
  }

  document.getElementById('nv-add').onclick=async()=>{
    if(!_hasOPFS){toast('Tu navegador no soporta esta funcion','err',3500);return;}
    const id=Date.now().toString(36);
    try{
      const nv=await getNVRoot();
      await nv.getDirectoryHandle(id,{create:true});
      openEditor(id);
    }catch(e){toast('Error al crear: '+e.message,'err');}
  };

  async function resolveMedia(root,dh){
    if(!root||!dh)return[];
    const urls=[];
    const els=root.querySelectorAll('img[src],audio[src],video[src]');
    for(const el of els){
      const src=el.getAttribute('src');
      if(!src||/^(https?:|data:|blob:)/i.test(src))continue;
      try{
        const fh=await dh.getFileHandle(src);
        const file=await fh.getFile();
        const url=URL.createObjectURL(file);
        el.src=url;
        urls.push(url);
      }catch(e){}
    }
    return urls;
  }

  function extFromMime(m){
    if(m.indexOf('webm')>-1)return 'webm';
    if(m.indexOf('ogg')>-1)return 'ogg';
    if(m.indexOf('mp4')>-1)return 'mp4';
    return 'webm';
  }

  async function loadInfo(){
    try{
      const f=await dirH.getFileHandle('info.json');
      const j=JSON.parse(await (await f.getFile()).text());
      document.getElementById('ne-name').value=j.nombre||'';
      return j;
    }catch(e){return{fecha:Date.now()};}
  }

  async function saveInfo(patch){
    let cur={};
    try{
      const f=await dirH.getFileHandle('info.json');
      cur=JSON.parse(await (await f.getFile()).text());
    }catch(e){}
    const j=Object.assign({fecha:Date.now()},cur,patch);
    await NV_W1(dirH,'info.json',JSON.stringify(j));
  }

  function bindSeqPlay(root){
    const auds=[...root.querySelectorAll('audio')];
    auds.forEach((a,idx)=>{
      a.onended=()=>{
        const next=auds[idx+1];
        if(next)next.play().catch(()=>{});
      };
    });
  }

  const attachBtn=document.getElementById('ne-battach');
  const recBtn=document.getElementById('ne-brec'),pauseBtn=document.getElementById('ne-bpause');
  const resumeBtn=document.getElementById('ne-bresume'),stopBtn=document.getElementById('ne-bstop');
  const recSt=document.getElementById('ne-recst');

  function setRecUI(state){
    const busy=state==='recording'||state==='paused';
    recBtn.style.display=state==='idle'?'flex':'none';
    pauseBtn.style.display=state==='recording'?'flex':'none';
    resumeBtn.style.display=state==='paused'?'flex':'none';
    stopBtn.style.display=busy?'flex':'none';
    recSt.classList.toggle('on',state==='recording');
    recSt.textContent=state==='recording'?'Grabando...':state==='paused'?'En pausa':'';
  }

  if(!_hasRec){
    recBtn.style.display='none';
    recSt.textContent='Grabar audio no esta disponible en este navegador';
  }

  function queueSave(){
    clearTimeout(saveTO);
    document.getElementById('ne-savest').textContent='Guardando...';
    saveTO=setTimeout(saveMD,SAVE_DEBOUNCE);
  }

  let recBookmark=null;

  recBtn.onclick=async()=>{
    try{
      mediaStream=await navigator.mediaDevices.getUserMedia({audio:true});
      mediaRec=new MediaRecorder(mediaStream);
      const noteDir=dirH;
      recBookmark=mde?mde.codemirror.setBookmark(mde.codemirror.getCursor()):null;
      const chunks=[];
      mediaRec.ondataavailable=e=>{if(e.data.size)chunks.push(e.data);};
      mediaRec.onstop=async()=>{
        mediaStream.getTracks().forEach(t=>t.stop());
        const bm=recBookmark;recBookmark=null;
        if(!chunks.length){setRecUI('idle');if(bm)bm.clear();return;}
        const blob=new Blob(chunks,{type:mediaRec.mimeType||'audio/webm'});
        if(blob.size>MAX_SIZE){toast('Audio supera 10MB, descartado','warn',3500);setRecUI('idle');if(bm)bm.clear();return;}
        const ext=extFromMime(blob.type);
        const fname='audio-'+Date.now()+Math.floor(Math.random()*1000)+'.'+ext;
        try{
          await NV_W1(noteDir,fname,blob);
        }catch(err){
          NV_E1('Audio',err);
          setRecUI('idle');
          if(bm)bm.clear();
          return;
        }
        if(mde){
          const cm=mde.codemirror;
          const pos=bm&&bm.find()?bm.find():cm.getCursor();
          cm.replaceRange('\n<audio controls src="'+fname+'"></audio>\n',pos);
        }
        if(bm)bm.clear();
        setRecUI('idle');
        toast('Audio agregado');
        queueSave();
      };
      mediaRec.start();
      setRecUI('recording');
    }catch(e){toast('No se pudo iniciar la grabacion: '+e.message,'err',4000);}
  };
  pauseBtn.onclick=()=>{if(mediaRec&&mediaRec.state==='recording'){mediaRec.pause();setRecUI('paused');}};
  resumeBtn.onclick=()=>{if(mediaRec&&mediaRec.state==='paused'){mediaRec.resume();setRecUI('recording');}};
  stopBtn.onclick=()=>{if(mediaRec&&mediaRec.state!=='inactive')mediaRec.stop();};

  attachBtn.onclick=()=>document.getElementById('ne-filein').click();

  document.getElementById('ne-filein').onchange=async function(e){
    const files=[].slice.call(e.target.files);
    this.value='';
    const noteDir=dirH;
    const bm=mde?mde.codemirror.setBookmark(mde.codemirror.getCursor()):null;
    let n=0;
    for(const f of files){
      if(f.size>MAX_SIZE){toast(f.name+' supera 10MB, omitido','warn',3500);continue;}
      const extm=f.name.match(/\.(\w+)$/);
      const ext=extm?extm[1]:(f.type.split('/')[1]||'bin');
      const fname='media-'+Date.now()+Math.floor(Math.random()*1000)+'.'+ext;
      try{
        await NV_W1(noteDir,fname,f);
      }catch(err){
        NV_E1('Adjuntar',err);
        break;
      }
      n++;
      if(mde){
        const cm=mde.codemirror;
        const pos=bm&&bm.find()?bm.find():cm.getCursor();
        cm.replaceRange(NV_T1(f.type,fname),pos);
      }
    }
    if(bm)bm.clear();
    if(n){toast(n>1?n+' archivos agregados':'Archivo agregado');queueSave();}
  };

  function NV_T1(mime,fname){
    if(mime.indexOf('video/')===0)return '\n<video controls preload="none" src="'+fname+'"></video>\n';
    if(mime.indexOf('audio/')===0)return '\n<audio controls src="'+fname+'"></audio>\n';
    return '![]('+fname+')\n';
  }

  const MD_ALLOWED_TAGS=['b','i','em','strong','a','code','pre','br','p','ul','ol','li','h1','h2','h3','blockquote','img','audio','video','source'];
  const MD_ALLOWED_ATTR=['href','src','alt','controls','preload','type'];
  const NV_DC1={
    ALLOWED_TAGS:MD_ALLOWED_TAGS,
    ALLOWED_ATTR:MD_ALLOWED_ATTR,
    FORBID_TAGS:['script','style','iframe','object','embed','svg','form'],
    FORBID_ATTR:['style','on*']
  };

  async function sanitizeMD(raw){
    if(!/[<>]/.test(raw))return raw;
    if(!window.DOMPurify)await loadLib(LIB_DP);
    if(!window.DOMPurify){
      toast('Guardado sin filtro: falta libreria','warn',4500);
      return raw.replace(/</g,'&lt;').replace(/>/g,'&gt;');
    }
    return window.DOMPurify.sanitize(raw,NV_DC1);
  }

  function renderReadHTML(txt){
    if(!mdReader)mdReader=window.markdownit({html:!0,breaks:!0,linkify:!0,typographer:!0});
    const raw=mdReader.render(txt);
    if(!window.DOMPurify)return'<p style="opacity:.5">No se pudo mostrar: falta libreria de seguridad.</p>';
    return window.DOMPurify.sanitize(raw,NV_DC1);
  }

  function initMDE(){
    if(mde){mde.toTextArea();mde=null;}
    mde=new EasyMDE({
      element:document.getElementById('ne-mdtxt'),
      spellChecker:false,autofocus:false,status:false,
      scrollbarStyle:'null',
      toolbar:['bold','italic','heading','|','quote','unordered-list','ordered-list','|','link','guide']
    });
    mde.codemirror.on('change',queueSave);
  }

  async function loadMD(){
    try{
      const fh=await dirH.getFileHandle('nota.md');
      const txt=await (await fh.getFile()).text();
      mde.value(txt);
    }catch(e){mde.value('');}
  }

  async function saveMD(){
    if(!mde)return true;
    try{
      await NV_W1(dirH,'nota.md',await sanitizeMD(mde.value()));
    }catch(e){
      document.getElementById('ne-savest').textContent='No guardado';
      NV_E1('Guardar',e);
      return false;
    }
    document.getElementById('ne-savest').textContent='Guardado '+new Date().toLocaleTimeString('es-PY',{hour:'2-digit',minute:'2-digit'});
    return true;
  }

  async function flushSave(){
    if(!saveTO)return true;
    clearTimeout(saveTO);saveTO=null;
    return await saveMD();
  }

  document.getElementById('ne-save').onclick=async()=>{
    try{
      if(!await flushSave())return;
      await saveInfo({nombre:document.getElementById('ne-name').value.trim()});
    }catch(e){
      NV_E1('Guardar',e);
      return;
    }
    stopRecordingIfActive();
    backToList();
    toast('Nota guardada');
  };

  document.getElementById('ne-name').onchange=async function(){
    try{
      await saveInfo({nombre:this.value.trim()});
    }catch(e){NV_E1('Nombre',e);}
  };

  document.getElementById('ne-del').onclick=async e=>{
    e.preventDefault();
    if(!confirm('Borrar esta nota de voz completa? Esto no se puede deshacer.'))return;
    clearTimeout(saveTO);saveTO=null;
    stopRecordingIfActive();
    try{
      const nv=await getNVRoot();
      await nv.removeEntry(curId,{recursive:true});
      backToList();
      toast('Entrada borrada');
    }catch(e){toast('Error al borrar: '+e.message,'err');}
  };

  function stopRecordingIfActive(){
    if(mediaRec&&mediaRec.state!=='inactive')mediaRec.stop();
  }

  document.getElementById('nv-back').onclick=async()=>{
    stopRecordingIfActive();
    await flushSave();
    backToList();
  };

  document.getElementById('nvr-back').onclick=()=>{
    backToList();
  };

  function clearReadBlobs(){
    readBlobs.forEach(u=>URL.revokeObjectURL(u));
    readBlobs=[];
  }

  function backToList(){
    curId=null;dirH=null;
    clearReadBlobs();
    showScreen('list');
    loadList();
  }

  async function openReader(id){
    curId=id;
    const nv=await getNVRoot();
    dirH=await nv.getDirectoryHandle(id,{create:true});
    const info=await loadInfo();
    document.getElementById('nvr-name').textContent=info.nombre||'Nota';
    document.getElementById('nvr-date').textContent=info.fecha?fmtDate(info.fecha):'';
    let txt='';
    try{
      const fh=await dirH.getFileHandle('nota.md');
      txt=await (await fh.getFile()).text();
    }catch(e){}
    const body=document.getElementById('nvr-body');
    try{
      await libsReady;
      body.innerHTML=txt?renderReadHTML(txt):'<p style="opacity:.5">Sin contenido de texto.</p>';
    }catch(e){
      body.innerHTML='<p style="opacity:.5">Error mostrando la nota.</p>';
    }
    clearReadBlobs();
    readBlobs=await resolveMedia(body,dirH);
    bindSeqPlay(body);
    showScreen('read');
  }

  async function enterEditMode(){
    document.getElementById('ne-name').value='';
    await loadInfo();
    setRecUI('idle');
    showScreen('edit');
    try{
      await libsReady;
      initMDE();
      await loadMD();
    }catch(e){
      toast('Error cargando editor de texto','err',4000);
    }
  }

  async function openEditor(id){
    curId=id;
    const nv=await getNVRoot();
    dirH=await nv.getDirectoryHandle(id,{create:true});
    await enterEditMode();
  }

  document.getElementById('nvr-edit').onclick=()=>{
    clearReadBlobs();
    enterEditMode();
  };

  const _el=document.getElementById('content');
  if(_el){
    _el.addEventListener('contentUnload',function _cleanup(){
      stopRecordingIfActive();
      if(saveTO){clearTimeout(saveTO);saveTO=null;saveMD();}
      if(mde){mde.toTextArea();mde=null;}
      clearReadBlobs();
      _el.removeEventListener('contentUnload',_cleanup);
      if(_self&&_self.parentNode)_self.parentNode.removeChild(_self);
    },{once:true});
  }


  loadList();
})();
</script>
