<style>
#rc-cats,#rc-mats{display:flex;flex-wrap:wrap;justify-content:center;gap:6px;margin-bottom:10px}
#rc-mats:not(.on){display:none}
#rc-map{height:340px;border-radius:14px;overflow:hidden;border:1px solid rgba(255,255,255,.1)}
#rc-map.leaflet-container{background:#1a1f2e}
#rc-map .leaflet-control-attribution{background:rgba(10,12,20,.75)!important;color:rgba(255,255,255,.45)!important;font-size:.6em!important}
#rc-map .leaflet-control-attribution a{color:rgba(255,255,255,.55)!important}
.rc-pn{position:relative;font:20px/1 var(--font);text-align:center;white-space:nowrap;transition:font-size .15s}
.rc-pn b{position:absolute;top:-6px;right:-8px;min-width:16px;padding:0 3px;border-radius:8px;background:#4ade80;color:#000;font:700 11px/16px sans-serif}
.rc-pn.on{font-size:30px;filter:drop-shadow(0 0 6px rgba(74,222,128,.9))}
#rc-panel{margin-top:12px;padding:14px;border-radius:14px;background:rgba(255,255,255,.03);border:1px solid rgba(255,255,255,.07)}
.rc-e{margin:12px 0;text-align:center;color:rgba(255,255,255,.4)}
.rc-tags{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:8px}
.rc-tag{padding:2px 10px;border-radius:12px;font-size:.72em;font-weight:700;background:rgba(74,222,128,.15);color:#86efac;border:1px solid rgba(74,222,128,.3)}
.rc-nm{margin:0 0 6px;font-size:1.05em}
.rc-row{font-size:.82em;color:rgba(255,255,255,.65);margin-bottom:4px}
.rc-acts{clear:both;display:flex;flex-wrap:wrap;gap:6px;margin-top:12px;padding-top:12px;border-top:1px solid rgba(255,255,255,.07)}
.lk-mp{border-color:rgba(234,67,53,.35);color:#ff7b6e;--LK_I:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M12 2a7 7 0 0 0-7 7c0 5.25 7 13 7 13s7-7.75 7-13a7 7 0 0 0-7-7zm0 9.5a2.5 2.5 0 1 1 0-5 2.5 2.5 0 0 1 0 5z'/%3E%3C/svg%3E")}
.lk-tl{--LK_I:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M6.62 10.79a15.05 15.05 0 0 0 6.59 6.59l2.2-2.2a1 1 0 0 1 1.02-.24 11.4 11.4 0 0 0 3.57.57 1 1 0 0 1 1 1V20a1 1 0 0 1-1 1A17 17 0 0 1 3 4a1 1 0 0 1 1-1h3.5a1 1 0 0 1 1 1c0 1.25.2 2.45.57 3.57a1 1 0 0 1-.25 1.02z'/%3E%3C/svg%3E")}
.lk-sm{--LK_I:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M20 2H4a2 2 0 0 0-2 2v18l4-4h14a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2zM9 11H7V9h2zm4 0h-2V9h2zm4 0h-2V9h2z'/%3E%3C/svg%3E")}
.lk-os{--LK_I:url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M3 17.25V21h3.75L17.81 9.94l-3.75-3.75zM20.71 7.04a1 1 0 0 0 0-1.41l-2.34-2.34a1 1 0 0 0-1.41 0l-1.83 1.83 3.75 3.75z'/%3E%3C/svg%3E")}
</style>

<h1>📍 Localizador</h1>

<div id="rc-cats"></div>
<div id="rc-mats"></div>

<div id="rc-map"></div>

<div id="rc-panel"><p class="rc-e">📍 Selecciona un punto en el mapa</p></div>

<script>
(function(){
const JSON_URL='web/Publico/localizador/data.json';
const CAT_EMOJI={banos:'🚻',agua:'💧','carga-electrica':'🔌','carga-celular':'📱',lavanderia:'👕',reciclaje:'♻️'};
const CAT_LABEL={banos:'Baños',agua:'Agua','carga-electrica':'Carga Autos','carga-celular':'Carga Celular',lavanderia:'Lavanderia',reciclaje:'Reciclaje'};
const MAT_EMOJI={electronico:'🔌',plastico:'🧴',papel:'📄',vidrio:'🍶',metal:'🔩',pilas:'🔋',organico:'🌿',aceite:'🛢️',ropa:'👚'};
const MAT_LABEL={electronico:'Electronicos',plastico:'Plastico',papel:'Papel',vidrio:'Vidrio',metal:'Metal',pilas:'Pilas',organico:'Organico',aceite:'Aceite',ropa:'Ropa'};
const PNL=document.getElementById('rc-panel'),AN=window.__AN1;

let GR=[],map=null,MKS=[],CG=null,SEL=null,_filter='',_matFilter='',_myPos=null,myMarker=null;

function X(t,c,s){const e=document.createElement(t);if(c)e.className=c;if(s!=null)e.textContent=s;return e;}
function em(p){return p.c==='reciclaje'&&_matFilter?MAT_EMOJI[_matFilter]:CAT_EMOJI[p.c];}
function lbl(p){return p.c==='reciclaje'&&p.m?p.m.map(k=>`${MAT_EMOJI[k]} ${MAT_LABEL[k]}`):[`${CAT_EMOJI[p.c]} ${CAT_LABEL[p.c]}`];}
function match(p){return(!_filter||p.c===_filter)&&(_filter!=='reciclaje'||!_matFilter||(p.m||[]).includes(_matFilter));}
function vis(g){return g.its.some(match);}

function mkIcon(gs,sel,n){
  const e=[...new Set(gs.flatMap(g=>g.its.filter(match).map(em)))].slice(0,3);
  const w=(sel?30:20)*e.length+4;
  return L.divIcon({html:`<div class="rc-pn${sel?' on':''}">${e.join('')}${n?`<b>${n}</b>`:''}</div>`,className:'',iconSize:[w,sel?32:24],iconAnchor:[w/2,sel?16:12]});
}

function showDetail(g){
  PNL.textContent='';
  const tg=X('div','rc-tags');
  [...new Set(g.its.flatMap(lbl))].forEach(t=>tg.append(X('span','rc-tag',t)));
  const nm=[...new Set(g.its.map(q=>q.n||CAT_LABEL[q.c]))].join(' / ');
  PNL.append(tg,X('h3','rc-nm',nm));
  [...new Set(g.its.map(q=>q.h).filter(Boolean))].forEach(h=>PNL.append(X('div','rc-row','🕐 '+h)));
  const f=g.its.find(q=>q.f!=null),w=g.its.find(q=>q.p||q.w||q.g)||{};
  if(f)PNL.append(X('div','rc-row',f.f?'💲 Pago':'💲 Gratis'));
  if(w.p)PNL.append(X('div','rc-row','📞 +'+w.p));
  const ac=X('div','rc-acts'),M=k=>GeoUtils.MU1(k,g.lat,g.lng,nm),MN={a:'Abrir en app','':'Google Maps',p:'Apple Maps',w:'Waze',o:'OpenStreetMap'};
  const A=(c,h,t,b)=>{const a=X('a','lk '+c,t);a.href=h;if(b){a.target='_blank';a.rel='noopener noreferrer';}ac.append(a);};
  let mk='';try{mk=localStorage.getItem('MA1')||''}catch{}
  (mk?[mk]:['a','','p']).forEach(k=>A('lk-mp',M(k),MN[k],k!=='a'));
  if(w.w){A('lk-wa',`https://wa.me/${w.w}`,'WhatsApp',1);A('lk-sm',`sms:+${w.w}`,'SMS');}
  if(w.p)A('lk-tl',`tel:+${w.p}`,'Llamar');
  if(w.g)A('lk-tg',`https://t.me/${w.g}`,'Telegram',1);
  A('lk-os',`https://www.openstreetmap.org/${g.its[0].i}`,'Corregir en OSM',1);
  PNL.append(ac);
}

function emptyPanel(t){PNL.textContent='';PNL.append(X('p','rc-e',t));}

function selectPin(g){
  const prev=MKS.find(m=>m.g===SEL);
  if(prev)prev.m.setIcon(mkIcon([prev.g],false));
  SEL=g;
  const cur=MKS.find(m=>m.g===g);
  if(cur)cur.m.setIcon(mkIcon([g],true));
  showDetail(g);
  PNL.scrollIntoView({behavior:'smooth',block:'nearest'});
}

function applyFilter(){
  SEL=null;
  emptyPanel('📍 Selecciona un punto en el mapa');
  CG.clearLayers();
  const v=MKS.filter(({g})=>vis(g));
  v.forEach(({g,m})=>m.setIcon(mkIcon([g],false)));
  CG.addLayers(v.map(x=>x.m));
  if(v.length)map.fitBounds(v.map(({g})=>[g.lat,g.lng]),{padding:[32,32],maxZoom:13});
  else emptyPanel('Sin lugares de este tipo aun');
}

function mkMyIcon(){
  return L.divIcon({html:'<div class="rc-pn">📍</div>',className:'',iconSize:[28,28],iconAnchor:[14,26]});
}
function addMyMarker(){
  if(!map||!_myPos||myMarker)return;
  myMarker=L.marker([_myPos.lat,_myPos.lng],{icon:mkMyIcon(),zIndexOffset:1000}).addTo(map);
  myMarker.bindTooltip('Tu ubicacion');
}
function geoLocate(){
  if(!navigator.geolocation)return;
  navigator.geolocation.getCurrentPosition(
    p=>{
      _myPos={lat:p.coords.latitude,lng:p.coords.longitude};
      try{localStorage.setItem('UBI','1');}catch{}
      addMyMarker();
    },
    ()=>{},
    {timeout:10000,maximumAge:60000}
  );
}

function initMap(){
  if(map)return;
  if(!GR.length){emptyPanel('Sin lugares publicados aun');return;}
  map=L.map('rc-map',{scrollWheelZoom:false});
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{
    attribution:'© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
    maxZoom:19
  }).addTo(map);
  CG=L.markerClusterGroup({showCoverageOnHover:false,iconCreateFunction:c=>mkIcon(c.getAllChildMarkers().map(m=>m.options.g),false,c.getChildCount())}).addTo(map);
  GR.forEach(g=>MKS.push({g,m:L.marker([g.lat,g.lng],{icon:mkIcon([g],false),g}).on('click',()=>selectPin(g))}));
  CG.addLayers(MKS.map(x=>x.m));
  addMyMarker();
  const AD=document.getElementById('rc-add');
  map.on('moveend',()=>{const c=map.getCenter();AD.href=`https://www.openstreetmap.org/note/new#map=${map.getZoom()}/${c.lat.toFixed(5)}/${c.lng.toFixed(5)}`;});
  const pts=GR.map(g=>[g.lat,g.lng]);
  if(_myPos)pts.push([_myPos.lat,_myPos.lng]);
  map.fitBounds(pts,{padding:[32,32],maxZoom:13});
}

const LF_L='web/js/lib/Leaflet/',LF_C='https://cdn.jsdelivr.net/npm/leaflet@1/dist/',MC_C='https://cdn.jsdelivr.net/npm/leaflet.markercluster@1/dist/';
function loadLeaflet(cb){
  if(window.L?.MarkerClusterGroup){cb();return;}
  const css=(f,c)=>{const l=document.createElement('link');l.rel='stylesheet';l.href=LF_L+f;l.onerror=()=>{l.href=c+f};document.head.appendChild(l);};
  const add=(f,c,ok,fb)=>{
    const s=document.createElement('script');
    s.src=(fb?c:LF_L)+f;s.onload=ok;
    s.onerror=fb?()=>emptyPanel('Error Mapa'):()=>add(f,c,ok,1);
    document.head.appendChild(s);
  };
  const mc=()=>{css('MarkerCluster.css',MC_C);add('leaflet.markercluster.js',MC_C,cb);};
  if(window.L)return mc();
  css('leaflet.css',LF_C);
  add('leaflet.js',LF_C,mc);
}

function selectCat(cat){
  _filter=cat;_matFilter='';
  document.querySelectorAll('#rc-cats button').forEach(b=>b.setAttribute('aria-pressed',b.dataset.cat===cat));
  document.querySelectorAll('#rc-mats button').forEach(b=>b.setAttribute('aria-pressed',b.dataset.mat===''));
  document.getElementById('rc-mats').classList.toggle('on',cat==='reciclaje');
  if(map)applyFilter();
}

function LZ_B1(L){
  const B=(id,d,k,t)=>{const b=X('button',null,t);b.dataset[d]=k;b.setAttribute('aria-pressed',k==='');document.getElementById(id).append(b);return b;};
  B('rc-cats','cat','','🗺️ Todos');
  Object.keys(CAT_EMOJI).filter(k=>L.some(p=>p.c===k)).forEach(k=>B('rc-cats','cat',k,`${CAT_EMOJI[k]} ${CAT_LABEL[k]}`));
  const ms=Object.keys(MAT_EMOJI).filter(k=>L.some(p=>p.m&&p.m.includes(k)));
  if(ms.length)['',...ms].forEach(k=>B('rc-mats','mat',k,k?`${MAT_EMOJI[k]} ${MAT_LABEL[k]}`:'Todos'));
  document.querySelectorAll('#rc-cats button').forEach(b=>{b.onclick=()=>selectCat(b.dataset.cat);});
  document.querySelectorAll('#rc-mats button').forEach(b=>{
    b.onclick=()=>{
      _matFilter=b.dataset.mat;
      document.querySelectorAll('#rc-mats button').forEach(x=>x.setAttribute('aria-pressed',x===b));
      if(map)applyFilter();
    };
  });
}

document.addEventListener('contentUnload',function(){
  if(map){map.remove();map=null;MKS=[];CG=null;}
  myMarker=null;_myPos=null;
},{once:true});

geoLocate();

Promise.all([fetch(JSON_URL).then(r=>r.json()),window.GeoUtils||new Promise((ok,ko)=>{const s=document.createElement('script');s.src='web/js/lib/GeoUtils.js';s.onload=ok;s.onerror=ko;document.head.appendChild(s)})])
  .then(([L])=>{
    const G={};
    L.forEach(p=>{(G[p.la+','+p.lo]??={lat:p.la,lng:p.lo,its:[]}).its.push(p);});
    GR=Object.values(G);
    LZ_B1(L);
    if(AN&&Object.hasOwn(CAT_EMOJI,AN))selectCat(AN);
    loadLeaflet(()=>{initMap();if(_filter&&map)applyFilter();});
  })
  .catch(()=>emptyPanel('Error Lugares'));
})();
</script>

<h2>Faltan lugares?</h2>

<p>Datos de <a href="https://www.openstreetmap.org/copyright" target="_blank" rel="noopener noreferrer">OpenStreetMap</a>, el mapa libre que cualquiera puede completar.</p>

<a id="rc-add" href="https://www.openstreetmap.org/note/new#map=7/-23.44/-58.44" target="_blank" rel="noopener noreferrer" class="view-all-button">➕ Agregar en OpenStreetMap</a>

<h2>Otras fuentes</h2>

<p>♻️ EcoPuntos: <a href="https://www.google.com/maps/d/viewer?mid=10n2AB-80yf5Shlu4p2kxqeeQ0J_H2UI" target="_blank" rel="noopener noreferrer">mapa de Soluciones Ecologicas</a></p>

<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones</a>
</div>
