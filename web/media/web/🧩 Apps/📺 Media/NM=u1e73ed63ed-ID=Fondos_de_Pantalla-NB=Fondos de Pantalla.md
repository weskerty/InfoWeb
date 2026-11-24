<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
._ic{display:block;margin:0 auto 8px}
.sk-wrap{padding:12px;max-width:100%}
.sk-bar{display:flex;align-items:center;gap:8px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.13);border-radius:24px;padding:10px 16px;margin-bottom:14px;position:relative;overflow:hidden;transition:border-color .2s,box-shadow .2s}
.sk-bar:focus-within{border-color:rgba(56,189,248,.4);box-shadow:0 0 0 3px rgba(56,189,248,.08),0 8px 32px rgba(0,0,0,.25)}
.sk-bar input[type=text]{flex:1;background:none;border:none;outline:none;color:white;font-size:.9em;min-width:0;font-family:inherit;position:relative;z-index:1}
.sk-bar input[type=text]::placeholder{color:rgba(255,255,255,.45)}
.sk-home{font-size:1.3rem;text-decoration:none;flex-shrink:0;line-height:1;opacity:.8;transition:opacity .2s,transform .2s;position:relative;z-index:1}
.sk-home:hover{opacity:1;transform:scale(1.15)}
.sk-ib{background:none;border:none;color:white;cursor:pointer;font-size:1.15rem;flex-shrink:0;padding:0 2px;opacity:.7;transition:opacity .2s,transform .2s;line-height:1;position:relative;z-index:1;min-width:1.6em;text-align:center;font-family:inherit}
.sk-ib:hover{opacity:1;transform:scale(1.1)}
.sk-ib:disabled{opacity:.3;cursor:not-allowed;transform:none}
.sk-bar.sk-cd::after{content:'';position:absolute;left:0;top:0;height:100%;width:var(--sk-cd-p,0%);background:rgba(56,189,248,.13);transition:width .1s linear;pointer-events:none;z-index:0}
.sk-msg{text-align:center;color:rgba(255,255,255,.55);font-size:.9em;padding:20px 0;margin:0}
.sk-searching{display:flex;flex-direction:column;align-items:center;justify-content:center;padding:32px 0;gap:8px;width:100%;grid-column:1/-1}
.sk-searching img{width:56px;height:56px}
.sk-searching span{color:rgba(255,255,255,.6);font-size:.95em}
.sk-toast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(20px);background:rgba(30,30,30,.97);border:1px solid rgba(255,255,255,.15);color:white;padding:10px 22px;border-radius:12px;font-size:.88em;opacity:0;pointer-events:none;transition:opacity .25s,transform .25s;z-index:999;white-space:nowrap}
.sk-toast.show{opacity:1;transform:translateX(-50%) translateY(0)}
.wp-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(max(160px,calc((100% - 16px)/3)),1fr));gap:8px;margin-bottom:8px;min-height:40px}
.wp-grid.wp-v{grid-template-columns:repeat(auto-fill,minmax(max(100px,calc((100% - 24px)/4)),1fr))}
.wp-it{aspect-ratio:16/9;border-radius:12px;overflow:hidden;cursor:pointer;position:relative;background:rgba(255,255,255,.08);border:2px solid rgba(255,255,255,.15);box-sizing:border-box;transition:transform .15s,border-color .15s}
.wp-grid.wp-v .wp-it{aspect-ratio:9/16}
.wp-it img.wp-th{width:100%;height:100%;object-fit:cover;display:block;pointer-events:none}
@media(hover:hover){.wp-it:hover{transform:scale(1.03);border-color:rgba(56,189,248,.4)}}
.wp-attr{position:absolute;bottom:0;left:0;right:0;padding:3px 7px;background:rgba(0,0,0,.62);font-size:.6em;color:rgba(255,255,255,.85);text-align:left}
.wp-dl{position:absolute;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,.55);backdrop-filter:blur(3px);-webkit-backdrop-filter:blur(3px);z-index:2}
body.low-perf .wp-dl{backdrop-filter:none}
.wp-dl.on{display:flex}
.wp-dl img{width:48px;height:48px}
.wp-mode{display:flex;justify-content:center;align-items:center;gap:8px;margin-bottom:10px}
.wp-ml{color:rgba(255,255,255,.5);font-size:.82em}
.wp-mo{background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.18);border-radius:10px;color:white;padding:5px 14px;cursor:pointer;font-size:.95rem;transition:background .2s}
.wp-mo:hover{background:rgba(255,255,255,.18)}
.wp-mo.wp-ma{background:rgba(56,189,248,.22);border-color:rgba(56,189,248,.45)}
.wp-cats{display:flex;flex-wrap:wrap;justify-content:center;gap:6px;margin-bottom:12px}
.wp-cat{background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.18);border-radius:20px;color:white;padding:5px 13px;cursor:pointer;font-size:.82em;transition:background .2s}
.wp-cat:hover{background:rgba(255,255,255,.18)}
.wp-cat.wp-ca{background:rgba(56,189,248,.22);border-color:rgba(56,189,248,.45)}
</style>


<div class="sk-wrap" id="wp-wrap">
  <div class="sk-bar" id="wp-bar">
    <a class="sk-home" href="web/es.html">🏠</a>
    <input id="wp-q" type="text" placeholder="Buscar wallpapers...">
    <button class="sk-ib" id="wp-btn">🔍</button>
  </div>
  <div class="wp-mode">
    <span class="wp-ml">Formato:</span>
    <button class="wp-mo wp-ma" id="wp-mh">🖥️</button>
    <button class="wp-mo" id="wp-mv">📱</button>
  </div>
  <div class="wp-cats">
    <button class="wp-cat" data-q="naturaleza">🌿 Naturaleza</button>
    <button class="wp-cat" data-q="oscuro">🌑 Oscuro</button>
    <button class="wp-cat" data-q="arte digital">🎨 Arte digital</button>
    <button class="wp-cat" data-q="autos">🚗 Autos</button>
    <button class="wp-cat" data-q="galaxia">🌌 Galaxia</button>
  </div>
  <div id="wp-grid" class="wp-grid"></div>
  <div id="wp-pg" class="PG1"></div>
  <p id="wp-st" class="sk-msg"></p>
</div>

<div class="sk-toast" id="wp-toast"></div>

<script>
(function(){
  const CD=10000;
  let WA='';
  let R=[],TP=1,pg=1,CQ='',cdEnd=0,cdRaf=null,_sac=null;
  let WM=window.innerHeight>window.innerWidth?'v':'h';
  const _busy=new WeakSet();

  const gEl=document.getElementById('wp-grid');
  const pgEl=document.getElementById('wp-pg');
  let SW=null,gfP=null;
  const GF1=()=>window.GridFit?Promise.resolve(window.GridFit):gfP||(gfP=new Promise(r=>{const s=document.createElement('script');s.src='web/js/lib/GridFit.js';s.onload=s.onerror=()=>r(window.GridFit);document.head.appendChild(s)}));
  const stEl=document.getElementById('wp-st');
  const qEl=document.getElementById('wp-q');
  const tEl=document.getElementById('wp-toast');
  const wrap=document.getElementById('wp-wrap');
  const mhEl=document.getElementById('wp-mh');
  const mvEl=document.getElementById('wp-mv');
  let _tt;

  if(window.__CFG){WA=window.__CFG.waitAnim||'';}else{fetch('web/js/plugins/config.json').then(r=>r.ok?r.json():{}).then(c=>{WA=c.waitAnim||'';}).catch(()=>{});}

  function toast(m){tEl.textContent=m;tEl.classList.add('show');clearTimeout(_tt);_tt=setTimeout(()=>tEl.classList.remove('show'),2500);}
  function ST(m){if(stEl)stEl.textContent=m;}

  function setMode(m){
    WM=m;
    gEl.classList.toggle('wp-v',m==='v');
    mhEl.classList.toggle('wp-ma',m==='h');
    mvEl.classList.toggle('wp-ma',m==='v');
    if(CQ){cdEnd=0;doSearch(CQ,pg);}
  }

  function startCD(){
    cdEnd=Date.now()+CD;
    qEl.readOnly=true;qEl.blur();
    const btn=document.getElementById('wp-btn'),bar=document.getElementById('wp-bar');
    btn.disabled=true;bar.classList.add('sk-cd');
    function tick(){
      const rem=cdEnd-Date.now();
      if(rem<=0){btn.disabled=false;bar.classList.remove('sk-cd');bar.style.removeProperty('--sk-cd-p');btn.textContent='🔍';qEl.readOnly=false;cdRaf=null;return;}
      bar.style.setProperty('--sk-cd-p',((1-rem/CD)*100).toFixed(1)+'%');
      btn.textContent=Math.ceil(rem/1000)+'s';
      cdRaf=requestAnimationFrame(tick);
    }
    cdRaf=requestAnimationFrame(tick);
  }

  function renderPG(){
    if(!window.GridFit){GF1().then(g=>{if(g)renderPG()});return}
    if(!SW)SW=GridFit.SW1(gEl,{n:()=>TP,p:()=>pg-1,go:i=>doSearch(CQ,i+1)});
    GridFit.PN1(pgEl,pg-1,TP,i=>doSearch(CQ,i+1));
  }

  function render(items){
    gEl.innerHTML='';ST('');
    if(!items.length){ST('Sin resultados');return;}
    items.forEach(item=>{
      const d=document.createElement('div');d.className='wp-it';
      const img=document.createElement('img');
      img.className='wp-th';
      img.src=item.thumb;img.alt=item.alt;img.loading='lazy';
      const at=document.createElement('div');at.className='wp-attr';
      const lk=document.createElement('a');
      lk.href=item.userUrl;lk.target='_blank';lk.rel='noopener noreferrer';
      lk.textContent='📷 '+item.user+' · '+(item.src||'');
      lk.style.cssText='color:inherit;text-decoration:none';
      lk.onclick=e=>e.stopPropagation();
      at.appendChild(lk);
      const dl=document.createElement('div');dl.className='wp-dl';
      dl.innerHTML=WA?`<img src="${WA}">`:'';
      d.append(img,at,dl);
      d.onclick=()=>dlImg(item,dl);
      gEl.appendChild(d);
    });
    renderPG();
    wrap.scrollIntoView({behavior:'smooth',block:'start'});
  }

  async function doSearch(q,p){
    if(_sac){_sac.abort();_sac=null;}
    _sac=new AbortController();
    pg=p;CQ=q;ST('');
    gEl.innerHTML=`<div class="sk-searching">${WA?`<img src="${WA}">`:''}<span>Buscando...</span></div>`;
    pgEl.innerHTML='';
    try{
      const r=await fetch('/api/wallpaper?q='+encodeURIComponent(q)+'&page='+p+'&ori='+WM,{signal:_sac.signal});
      const d=await r.json().catch(()=>({}));
      if(!r.ok&&!d.fb)throw new Error(r.status);
      R=d.results||[];TP=d.fb?1:d.total_pages||1;
      render(R);
      if(d.fb)(R.length?toast:ST)('Limite de busquedas, proba en unos minutos');
    }catch(e){
      if(e.name==='AbortError')return;
      gEl.innerHTML='';ST('Error: '+e.message);
    }
  }

  async function dlImg(item,dl){
    if(_busy.has(dl))return;
    _busy.add(dl);
    dl.classList.add('on');
    if(item.dl)fetch('/api/wallpaper?track='+encodeURIComponent(item.dl)).catch(()=>{});
    try{
      const r=await fetch(item.full);
      if(!r.ok)throw new Error(r.status);
      const blob=await r.blob();
      const fname='wallpaper-'+item.id+'.jpg';
      const url=URL.createObjectURL(blob);
      const a=document.createElement('a');
      a.href=url;a.download=fname;a.click();
      setTimeout(()=>URL.revokeObjectURL(url),15000);
      const file=new File([blob],fname,{type:blob.type||'image/jpeg'});
      if(navigator.canShare&&navigator.canShare({files:[file]})){
        navigator.share({files:[file],title:'Wallpaper'}).catch(()=>{});
      }
    }catch{
      toast('Error descarga');
    }
    dl.classList.remove('on');
    _busy.delete(dl);
  }

  function search(){
    if(Date.now()<cdEnd)return;
    const q=qEl.value.trim();if(!q)return;
    document.querySelectorAll('.wp-cat').forEach(b=>b.classList.remove('wp-ca'));
    startCD();doSearch(q,1);
  }

  mhEl.onclick=()=>setMode('h');
  mvEl.onclick=()=>setMode('v');
  document.getElementById('wp-btn').onclick=search;
  qEl.addEventListener('keydown',e=>{if(e.key==='Enter')search();});
  qEl.addEventListener('input',()=>document.querySelectorAll('.wp-cat').forEach(b=>b.classList.remove('wp-ca')));

  document.querySelectorAll('.wp-cat').forEach(btn=>{
    btn.onclick=()=>{
      document.querySelectorAll('.wp-cat').forEach(b=>b.classList.remove('wp-ca'));
      btn.classList.add('wp-ca');
      qEl.value=btn.dataset.q;
      cdEnd=0;startCD();doSearch(btn.dataset.q,1);
    };
  });

  const _ori=window.matchMedia('(orientation: portrait)'),OR1=e=>setMode(e.matches?'v':'h');
  _ori.addEventListener('change',OR1);

  const _el=document.getElementById('content');
  if(_el)_el.addEventListener('contentUnload',()=>{
    if(_sac){_sac.abort();_sac=null;}
    if(cdRaf){cancelAnimationFrame(cdRaf);cdRaf=null;}
    _ori.removeEventListener('change',OR1);
  },{once:true});

  setMode(WM);
  doSearch('naturaleza',1);
})();
</script>

<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>
</div>