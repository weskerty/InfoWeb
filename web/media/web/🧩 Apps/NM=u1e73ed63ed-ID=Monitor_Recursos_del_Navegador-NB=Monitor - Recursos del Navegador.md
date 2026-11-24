 <!-- https://packagemain.tech/p/golang-datastar  -->


<div style="text-align:center;position:relative;padding-top:0;margin-top:0" id="ht-app">
<style>
.HT0{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 18px}
.HT1{display:grid;grid-template-columns:repeat(auto-fit,minmax(142px,1fr));gap:10px;text-align:left}
.HT2{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.09);border-radius:var(--r-sm);padding:10px 12px}
.HT3{font-size:.72rem;color:rgba(255,255,255,.5);letter-spacing:.03em;margin-bottom:3px}
.HT4{font-size:1.2rem;font-weight:600;line-height:1.25;overflow-wrap:break-word}
.HT5{height:5px;border-radius:3px;background:rgba(255,255,255,.1);margin-top:8px;overflow:hidden}
.HT6{height:100%;width:0;border-radius:3px;background:var(--ok);transition:width .4s ease,background .4s ease}
.HT7{color:rgba(255,255,255,.45);font-size:.8em;margin:10px 0 0}
.HT8{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:14px 0 4px}
.HT9{font-size:.9rem}
@media (prefers-reduced-motion:reduce){.HT6{transition:none}}
body.low-perf .HT6{transition:none}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">📊</div>
<div class="HT0" id="ht-st">Monitor de Recursos</div>

<details open>
<summary>🔥 Procesador</summary>
<section>
<div class="HT1">
<div class="HT2"><div class="HT3">PRESION CPU</div><div class="HT4" id="ht-prs">--</div><div class="HT5"><div class="HT6" id="ht-prsb"></div></div></div>
<div class="HT2"><div class="HT3">HILO BLOQUEADO</div><div class="HT4" id="ht-blk">--</div><div class="HT5"><div class="HT6" id="ht-blkb"></div></div></div>
<div class="HT2"><div class="HT3">CUADROS</div><div class="HT4" id="ht-fps">--</div><div class="HT5"><div class="HT6" id="ht-fpsb"></div></div></div>
<div class="HT2"><div class="HT3">NUCLEOS</div><div class="HT4" id="ht-cor">--</div></div>
</div>
<p class="HT7">Presion CPU la reporta el sistema operativo. Bloqueo es cuanto tiempo por segundo el hilo principal quedo trabado en tareas largas.</p>
</section>
</details>

<details open>
<summary>🧠 Memoria</summary>
<section>
<div class="HT1">
<div class="HT2"><div class="HT3">HEAP EN USO</div><div class="HT4" id="ht-hp">--</div><div class="HT5"><div class="HT6" id="ht-hpb"></div></div></div>
<div class="HT2"><div class="HT3">HEAP RESERVADO</div><div class="HT4" id="ht-hpt">--</div></div>
<div class="HT2"><div class="HT3">RAM DEL EQUIPO</div><div class="HT4" id="ht-ram">--</div></div>
<div class="HT2"><div class="HT3">BATERIA</div><div class="HT4" id="ht-bat">--</div><div class="HT5"><div class="HT6" id="ht-batb"></div></div></div>
</div>
<p class="HT7">Solo se ve la memoria de esta pestana, no la del sistema.</p>
</section>
</details>

<details open>
<summary>🌐 Red</summary>
<section>
<div class="HT1">
<div class="HT2"><div class="HT3">VELOCIDAD</div><div class="HT4" id="ht-rat">--</div><div class="HT5"><div class="HT6" id="ht-ratb"></div></div></div>
<div class="HT2"><div class="HT3">TRANSFERIDO</div><div class="HT4" id="ht-tot">--</div></div>
<div class="HT2"><div class="HT3">DESDE CACHE</div><div class="HT4" id="ht-cch">--</div></div>
<div class="HT2"><div class="HT3">CONEXION</div><div class="HT4" id="ht-cnx">--</div></div>
<div class="HT2"><div class="HT3">LATENCIA ESTIMADA</div><div class="HT4" id="ht-rtt">--</div></div>
<div class="HT2"><div class="HT3">AHORRO DE DATOS</div><div class="HT4" id="ht-sav">--</div></div>
</div>
<p class="HT7">U</p>
</section>
</details>

<details open>
<summary>⚡ Velocidad</summary>
<section>
<div class="HT1">
<div class="HT2"><div class="HT3">BAJADA</div><div class="HT4" id="ht-dn">--</div><div class="HT5"><div class="HT6" id="ht-dnb"></div></div></div>
<div class="HT2"><div class="HT3">SUBIDA</div><div class="HT4" id="ht-up">--</div><div class="HT5"><div class="HT6" id="ht-upb"></div></div></div>
<div class="HT2"><div class="HT3">LATENCIA MEDIDA</div><div class="HT4" id="ht-lt">--</div><div class="HT5"><div class="HT6" id="ht-ltb"></div></div></div>
<div class="HT2"><div class="HT3">VARIACION</div><div class="HT4" id="ht-jt">--</div></div>
<div class="HT2"><div class="HT3">IP PUBLICA</div><div class="HT4 HT9" id="ht-ip">--</div></div>
</div>
<div class="HT8"><button id="ht-spb">🔄 Repetir</button><button id="ht-spl">📈 Prueba larga</button></div>
<p class="HT7">Se mide contra speed.cloudflare.com.</p>
</section>
</details>

<details open>
<summary>📈 Recursos mas pesados</summary>
<section>
<table><thead><tr><th>Archivo</th><th>Transferido</th><th>Descomprimido</th><th>Tiempo</th></tr></thead><tbody id="ht-rt"></tbody></table>
<div class="HT8"><button id="ht-rtb">🔄 Actualizar</button></div>
</section>
</details>

<details open>
<summary>💾 Almacenamiento</summary>
<section>
<div class="HT1">
<div class="HT2"><div class="HT3">USADO</div><div class="HT4" id="ht-usg">--</div><div class="HT5"><div class="HT6" id="ht-usgb"></div></div></div>
<div class="HT2"><div class="HT3">CUOTA</div><div class="HT4" id="ht-quo">--</div></div>
</div>
<div class="HT8"><button id="ht-anb">🔍 Analizar</button></div>
<table><thead><tr><th>Origen</th><th>Cantidad</th><th>Peso</th><th></th></tr></thead><tbody id="ht-sb"></tbody></table>
<blockquote><p>Vaciar un cache es inmediato y no se puede deshacer. El sitio lo vuelve a llenar solo al navegar, pero la fuente de emojis y las librerias se bajan de nuevo.</p></blockquote>
</section>
</details>

<details open>
<summary>🖥️ Equipo</summary>
<section>
<div class="HT1">
<div class="HT2"><div class="HT3">GRAFICA</div><div class="HT4 HT9" id="ht-gpu">--</div></div>
<div class="HT2"><div class="HT3">PANTALLA</div><div class="HT4 HT9" id="ht-scr">--</div></div>
<div class="HT2"><div class="HT3">PLATAFORMA</div><div class="HT4 HT9" id="ht-plt">--</div></div>
<div class="HT2"><div class="HT3">SERVICE WORKER</div><div class="HT4 HT9" id="ht-swk">--</div></div>
<div class="HT2"><div class="HT3">MODO RENDIMIENTO</div><div class="HT4 HT9" id="ht-lp">--</div></div>
</div>
<p class="HT7">El sitio mide los cuadros por segundo al arrancar y guarda el resultado. Debajo de 48 activa el modo bajo, que apaga desenfoques y animaciones.</p>
<div class="HT8"><button id="ht-lpl">Forzar bajo</button><button id="ht-lph">Forzar alto</button><button id="ht-lpr">Volver a medir</button></div>
</section>
</details>

<div class="HT8"><button id="ht-cp">📋 Copiar resultados</button></div>

<script>
(function(){
  const $=i=>document.getElementById(i);
  if(!$('ht-fps'))return;
  const F=n=>{if(n==null||!isFinite(n))return '--';const u=['B','KB','MB','GB','TB'];let i=0;n=Math.abs(n);while(n>=1024&&i<u.length-1){n/=1024;i++}return (i?n.toFixed(n<10?2:1):Math.round(n))+' '+u[i]};
  const C=p=>p<60?'var(--ok)':p<85?'var(--warn)':'var(--err)';
  function S(id,v,p,c){const e=$(id);if(e)e.textContent=v;const b=$(id+'b');if(b&&p!=null){b.style.width=Math.max(0,Math.min(100,p))+'%';if(c)b.style.background=c}}

  let fr=0,fps=0,rid=0,blk=0,pblk=0,tot=0,ptot=0,cch=0,peak=1,prs=null,bat=null,po=null,lo=null,ro=null,tick=0;
  let tPrev=performance.now();

  function raf(){fr++;rid=requestAnimationFrame(raf)}
  rid=requestAnimationFrame(raf);

  if(window.PressureObserver){
    try{
      po=new PressureObserver(rs=>{prs=rs[rs.length-1].state});
      const r=po.observe('cpu',{sampleInterval:1000});
      if(r&&r.catch)r.catch(()=>{po=null});
    }catch(e){po=null}
  }
  try{lo=new PerformanceObserver(l=>{for(const e of l.getEntries())blk+=e.duration});lo.observe({type:'longtask',buffered:true})}catch(e){lo=null}
  try{ro=new PerformanceObserver(l=>{for(const e of l.getEntries()){tot+=e.transferSize||0;if(!e.transferSize&&e.decodedBodySize)cch+=e.decodedBodySize}});ro.observe({type:'resource',buffered:true})}catch(e){ro=null}
  for(const e of performance.getEntriesByType('resource')){tot+=e.transferSize||0;if(!e.transferSize&&e.decodedBodySize)cch+=e.decodedBodySize}
  ptot=tot;

  if(navigator.getBattery)navigator.getBattery().then(b=>{bat=b}).catch(()=>{});

  const nc=navigator.connection||navigator.mozConnection||navigator.webkitConnection;
  $('ht-cor').textContent=navigator.hardwareConcurrency?navigator.hardwareConcurrency+' hilos':'n/d';
  $('ht-ram').textContent=navigator.deviceMemory?navigator.deviceMemory+' GB o mas':'n/d';
  $('ht-scr').textContent=screen.width+'x'+screen.height+' @'+(window.devicePixelRatio||1)+'x';
  $('ht-plt').textContent=(navigator.userAgentData&&navigator.userAgentData.platform)||navigator.platform||'n/d';
  try{
    const cv=document.createElement('canvas'),gl=cv.getContext('webgl')||cv.getContext('experimental-webgl');
    const dx=gl&&gl.getExtension('WEBGL_debug_renderer_info');
    $('ht-gpu').textContent=dx?gl.getParameter(dx.UNMASKED_RENDERER_WEBGL):(gl?gl.getParameter(gl.RENDERER):'n/d');
  }catch(e){$('ht-gpu').textContent='n/d'}
  const swc=navigator.serviceWorker&&navigator.serviceWorker.controller;
  $('ht-swk').textContent=swc?'Activo':'Sin controlar';

  const PM={nominal:['Normal',15,'var(--ok)'],fair:['Media',45,'var(--ok)'],serious:['Alta',75,'var(--warn)'],critical:['Critica',100,'var(--err)']};

  function upd(){
    const now=performance.now(),dt=(now-tPrev)/1000||1;tPrev=now;
    fps=Math.round(fr/dt);fr=0;
    S('ht-fps',fps+' fps',fps/60*100,fps>=48?'var(--ok)':fps>=30?'var(--warn)':'var(--err)');

    if(po&&prs&&PM[prs])S('ht-prs',PM[prs][0],PM[prs][1],PM[prs][2]);
    else S('ht-prs',po?'Midiendo':'n/d',0);

    if(lo){const d=(blk-pblk)/dt;pblk=blk;S('ht-blk',Math.round(d)+' ms/s',d/10,C(d/10))}
    else S('ht-blk','n/d',0);

    const m=performance.memory;
    if(m){const p=m.usedJSHeapSize/m.jsHeapSizeLimit*100;S('ht-hp',F(m.usedJSHeapSize),p,C(p));$('ht-hpt').textContent=F(m.totalJSHeapSize)+' de '+F(m.jsHeapSizeLimit)}
    else{S('ht-hp','n/d',0);$('ht-hpt').textContent='n/d'}

    if(bat){const p=bat.level*100;S('ht-bat',Math.round(p)+'%'+(bat.charging?' ⚡':''),p,p>50?'var(--ok)':p>20?'var(--warn)':'var(--err)')}
    else S('ht-bat','n/d',0);

    const rate=(tot-ptot)/dt;ptot=tot;
    if(rate>peak)peak=rate;
    S('ht-rat',F(rate)+'/s',rate/peak*100,'var(--acc)');
    $('ht-tot').textContent=F(tot);
    $('ht-cch').textContent=F(cch);
    if(nc){$('ht-cnx').textContent=(nc.effectiveType||'?')+(nc.downlink?' · '+nc.downlink+' Mb/s':'');$('ht-rtt').textContent=nc.rtt!=null?nc.rtt+' ms':'n/d';$('ht-sav').textContent=nc.saveData?'Activado':'Desactivado'}
    else{$('ht-cnx').textContent='n/d';$('ht-rtt').textContent='n/d';$('ht-sav').textContent='n/d'}

    if(navigator.storage&&navigator.storage.estimate)navigator.storage.estimate().then(e=>{
      const p=e.quota?e.usage/e.quota*100:0;
      S('ht-usg',F(e.usage),p,C(p));$('ht-quo').textContent=F(e.quota);
    }).catch(()=>{});

    if(tick++%5===0)res();
  }

  function res(){
    const tb=$('ht-rt');if(!tb)return;
    const rs=performance.getEntriesByType('resource').slice().sort((a,b)=>(b.transferSize||b.decodedBodySize||0)-(a.transferSize||a.decodedBodySize||0)).slice(0,15);
    tb.textContent='';
    for(const r of rs){
      let n=r.name.split('?')[0].split('/').pop()||r.name;
      try{n=decodeURIComponent(n)}catch(e){}
      row(tb,[n.slice(0,30),F(r.transferSize),F(r.decodedBodySize),Math.round(r.duration)+' ms']);
    }
  }

  function row(tb,vals,btn){
    const tr=document.createElement('tr');
    for(const v of vals){const td=document.createElement('td');td.textContent=v;tr.appendChild(td)}
    if(btn!==undefined){const td=document.createElement('td');if(btn)td.appendChild(btn);tr.appendChild(td)}
    tb.appendChild(tr);
  }

  async function walk(d,p,out,dp){
    if(dp>5)return;
    for await(const en of d.entries()){
      const n=en[0],h=en[1];
      if(h.kind==='file'){try{const f=await h.getFile();out.push([p+n,f.size])}catch(e){}}
      else await walk(h,p+n+'/',out,dp+1);
    }
  }

  async function scan(){
    const tb=$('ht-sb'),bt=$('ht-anb');
    bt.disabled=true;bt.textContent='Analizando...';tb.textContent='';
    try{
      const e=await navigator.storage.estimate();
      if(e.usageDetails)for(const k in e.usageDetails)row(tb,['📐 '+k,'',F(e.usageDetails[k])],null);
    }catch(e){}
    try{
      for(const n of await caches.keys()){
        const c=await caches.open(n),ks=await c.keys();let s=0;
        for(const k of ks){const r=await c.match(k);if(!r)continue;const cl=r.headers.get('content-length');s+=cl?+cl:(await r.blob()).size}
        const b=document.createElement('button');b.textContent='Vaciar';
        b.onclick=async()=>{if(!confirm('Borrar el cache '+n+'?'))return;await caches.delete(n);scan()};
        row(tb,['🗄️ '+n,ks.length+' arch.',F(s)],b);
      }
    }catch(e){}
    try{
      const out=[];await walk(await navigator.storage.getDirectory(),'',out,0);
      let t=0;for(const o of out)t+=o[1];
      row(tb,['🗂️ OPFS',out.length+' arch.',F(t)],null);
      for(const o of out.slice(0,120))row(tb,['  '+o[0],'',F(o[1])],null);
    }catch(e){}
    bt.disabled=false;bt.textContent='🔍 Analizar';
  }

  const SPD='https://speed.cloudflare.com/__down?bytes=',SPU='https://speed.cloudflare.com/__up';
  let spb=false;
  const MB=(b,s)=>b*8/s/1e6;
  const DC=m=>m>25?'var(--ok)':m>5?'var(--warn)':'var(--err)';
  const UC=m=>m>10?'var(--ok)':m>2?'var(--warn)':'var(--err)';

  async function SP1(){
    const t=[];
    for(let k=0;k<6;k++){
      const a=performance.now();
      try{
        const r=await fetch(SPD+'1&r='+Math.random(),{cache:'no-store'});
        const ip=r.headers.get('cf-meta-ip');
        if(ip)$('ht-ip').textContent=ip;
        await r.arrayBuffer();
        t.push(performance.now()-a);
      }catch(e){}
    }
    if(!t.length){S('ht-lt','Error',0);return}
    t.sort((a,b)=>a-b);
    const mn=t[0];
    S('ht-lt',Math.round(mn)+' ms',Math.min(100,mn/3),mn<80?'var(--ok)':mn<200?'var(--warn)':'var(--err)');
    $('ht-jt').textContent=Math.round(t[t.length-1]-mn)+' ms';
  }

  async function SP2(ms,cap){
    try{
      const t0=performance.now();
      const r=await fetch(SPD+cap+'&r='+Math.random(),{cache:'no-store'});
      const rd=r.body.getReader();
      let got=0,tm=0,bm=0,nx=0,el=0;
      for(;;){
        const c=await rd.read();
        if(c.done)break;
        got+=c.value.length;
        el=performance.now()-t0;
        if(!tm&&el>250){tm=el;bm=got}
        if(tm&&el>nx){nx=el+250;const m=MB(got-bm,(el-tm)/1000);if(isFinite(m)&&m>0)S('ht-dn',m.toFixed(1)+' Mb/s',Math.min(100,m),DC(m))}
        if(el>ms){try{await rd.cancel()}catch(e){}break}
      }
      const w=tm?(el-tm)/1000:el/1000,b=tm?got-bm:got,m=MB(b,w);
      S('ht-dn',(w<.3?'~':'')+(isFinite(m)?m.toFixed(1):'--')+' Mb/s',Math.min(100,m),DC(m));
    }catch(e){S('ht-dn','Error',0)}
  }

  async function SP3(n){
    try{
      const bl=new Uint8Array(65536);
      crypto.getRandomValues(bl);
      const k=Math.ceil(n/65536),parts=[];
      for(let i=0;i<k;i++)parts.push(bl);
      const t0=performance.now();
      await fetch(SPU,{method:'POST',body:new Blob(parts),cache:'no-store'});
      const sc=(performance.now()-t0)/1000,m=MB(k*65536,sc);
      S('ht-up',(sc<.3?'~':'')+m.toFixed(1)+' Mb/s',Math.min(100,m),UC(m));
    }catch(e){S('ht-up','Error',0)}
  }

  async function SPR(big){
    if(spb)return;
    spb=true;
    const b1=$('ht-spb'),b2=$('ht-spl');
    b1.disabled=b2.disabled=true;
    S('ht-dn','Midiendo',0);S('ht-up','Midiendo',0);S('ht-lt','Midiendo',0);
    await SP1();
    await SP2(big?8000:1500,big?60e6:5e6);
    await SP3(big?10e6:1e6);
    b1.disabled=b2.disabled=false;
    spb=false;
  }

  function lpu(){
    const v=localStorage.getItem('perf');
    $('ht-lp').textContent=(document.body.classList.contains('low-perf')?'Bajo':'Alto')+(v?' (guardado: '+v+')':' (sin medir)');
  }
  function lps(v){
    if(v)localStorage.setItem('perf',v);else localStorage.removeItem('perf');
    window.__PF1(v);
    lpu();
  }
  lpu();

  $('ht-lpl').onclick=()=>lps('low');
  $('ht-lph').onclick=()=>lps('high');
  $('ht-lpr').onclick=()=>lps(null);
  $('ht-spb').onclick=()=>SPR(false);
  $('ht-spl').onclick=()=>SPR(true);
  $('ht-anb').onclick=scan;
  $('ht-rtb').onclick=res;
  $('ht-cp').onclick=()=>{
    const L=[];
    document.querySelectorAll('#ht-app .HT2').forEach(c=>{
      const a=c.querySelector('.HT3'),b=c.querySelector('.HT4');
      if(a&&b)L.push(a.textContent+': '+b.textContent);
    });
    L.push('UA: '+navigator.userAgent);
    navigator.clipboard.writeText(L.join('\n')).then(()=>{
      const b=$('ht-cp');b.textContent='✅ Copiado';setTimeout(()=>{b.textContent='📋 Copiar resultados'},1500);
    }).catch(()=>{$('ht-cp').textContent='❌ Error Copiar'});
  };

  upd();res();
  const iv=setInterval(upd,1000);
  let spt=0;
  if(nc&&nc.saveData){$('ht-dn').textContent='Ahorro de datos';$('ht-up').textContent='Ahorro de datos'}
  else spt=setTimeout(()=>SPR(false),1500);

  const cu=$('content');
  if(cu)cu.addEventListener('contentUnload',()=>{
    clearInterval(iv);
    clearTimeout(spt);
    cancelAnimationFrame(rid);
    try{if(po)po.disconnect()}catch(e){}
    try{if(lo)lo.disconnect()}catch(e){}
    try{if(ro)ro.disconnect()}catch(e){}
  },{once:true});
})();
</script>

<br>
<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>
</div>
