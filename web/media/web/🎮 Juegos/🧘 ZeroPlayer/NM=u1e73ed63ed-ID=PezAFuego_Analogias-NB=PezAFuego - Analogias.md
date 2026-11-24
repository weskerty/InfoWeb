<style data-content>
#AN_wrap{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:16px;padding:24px;max-width:600px;margin:0 auto}
#AN_barra{width:100%;text-align:center;font-size:.9em;opacity:.8}
#AN_timer{width:100%;height:6px;background:rgba(255,255,255,.15);border-radius:3px;overflow:hidden}
#AN_timerBar{height:100%;width:100%;background:currentColor;transition:width 1s linear}
#AN_pregunta{font-size:1.3em;font-weight:600;text-align:center}
#AN_explica{font-size:.9em;opacity:.85;text-align:center;max-width:500px;line-height:1.5}
#AN_explica a{color:inherit}
#AN_inicio{display:flex;flex-direction:column;align-items:center;gap:16px;text-align:center}
#AN_iniciarBtn{padding:12px 24px;border-radius:10px;border:1px solid rgba(255,255,255,.3);background:rgba(255,255,255,.08);cursor:pointer;font-size:1em}
#AN_opciones{display:flex;flex-direction:column;gap:10px;width:100%}
.AN_op{padding:14px;border-radius:12px;border:1px solid rgba(255,255,255,.2);background:rgba(255,255,255,.05);color:inherit;font:inherit;cursor:pointer;text-align:center;transition:background .2s}
.AN_op:hover{background:rgba(255,255,255,.12)}
#AN_final{text-align:center;display:flex;flex-direction:column;gap:12px}
#AN_estrellas{font-size:2em}
#AN_reintentar{padding:10px 20px;border-radius:10px;border:1px solid rgba(255,255,255,.3);background:rgba(255,255,255,.08);cursor:pointer}
</style>

<div id="AN_wrap">
<div id="AN_inicio">
<div id="AN_explica">Una analogia es una comparacion entre dos cosas diferentes. Ejemplo: "A es a B como C es a D". Sirve para explicar ideas nuevas usando cosas que ya conocemos. Ver mas info en <a href="https://es.wikipedia.org/wiki/Analog%C3%ADa" target="_blank" rel="noopener">Wikipedia ↗️</a></div>
<button id="AN_iniciarBtn" disabled>Iniciar Juego</button>
</div>
<div id="AN_barra" style="display:none"><span id="AN_contador"></span></div>
<div id="AN_timer" style="display:none"><div id="AN_timerBar"></div></div>
<div id="AN_pregunta" style="display:none"></div>
<div id="AN_opciones"></div>
</div>

<script>
(function(){
var AN_base="web/adjuntos/PezAFuego_Analogias/";
var AN_TOTAL=20;
var AN_TIME=15;
var AN_data=[],AN_orden=[],AN_idx=0,AN_ok=0,AN_int=null,AN_seg=0,AN_activo=false;

function AN_shuffle(a){
  for(var i=a.length-1;i>0;i--){
    var j=Math.floor(Math.random()*(i+1));
    var t=a[i];a[i]=a[j];a[j]=t;
  }
  return a;
}

function AN_limpiar(){
  clearInterval(AN_int);
  AN_int=null;
  AN_activo=false;
}

function AN_render(){
  var q=AN_data[AN_orden[AN_idx]];
  document.getElementById("AN_contador").textContent=(AN_idx+1)+"/"+AN_orden.length;
  document.getElementById("AN_pregunta").textContent=q.pregunta+" como:";
  var idxOp=AN_shuffle(q.opciones.map(function(_,i){return i}));
  var correctaPos=idxOp.indexOf(q.correct);
  var cont=document.getElementById("AN_opciones");
  cont.innerHTML="";
  idxOp.forEach(function(origI,pos){
    var d=document.createElement("button");
    d.className="AN_op";
    d.textContent=q.opciones[origI];
    d.addEventListener("click",function(){AN_responder(pos,correctaPos)});
    cont.appendChild(d);
  });
  AN_seg=AN_TIME;
  var bar=document.getElementById("AN_timerBar");
  bar.style.transition="none";
  bar.style.width="100%";
  void bar.offsetWidth;
  bar.style.transition="width 1s linear";
  AN_activo=true;
  clearInterval(AN_int);
  AN_int=setInterval(function(){
    AN_seg--;
    bar.style.width=Math.max(0,(AN_seg/AN_TIME)*100)+"%";
    if(AN_seg<=0){
      clearInterval(AN_int);
      AN_responder(-1,correctaPos);
    }
  },1000);
}

function AN_responder(i,correctaPos){
  if(!AN_activo)return;
  AN_activo=false;
  clearInterval(AN_int);
  if(i===correctaPos)AN_ok++;
  AN_idx++;
  if(AN_idx>=AN_orden.length)AN_final();
  else AN_render();
}

function AN_final(){
  AN_limpiar();
  document.getElementById("AN_timer").style.display="none";
  document.getElementById("AN_pregunta").style.display="none";
  document.getElementById("AN_contador").textContent="";
  var cont=document.getElementById("AN_opciones");
  cont.innerHTML="";
  var porEstrella=AN_orden.length/5;
  var estrellas=Math.max(1,Math.round(AN_ok/porEstrella));
  var f=document.createElement("div");
  f.id="AN_final";
  f.innerHTML="<div>Tu puntuacion es:</div><div id=\"AN_estrellas\">"+"\u2b50".repeat(estrellas)+"</div>";
  var btn=document.createElement("button");
  btn.id="AN_reintentar";
  btn.textContent="Jugar de nuevo";
  btn.addEventListener("click",AN_iniciar);
  f.appendChild(btn);
  cont.appendChild(f);
}

function AN_iniciar(){
  document.getElementById("AN_inicio").style.display="none";
  document.getElementById("AN_barra").style.display="";
  document.getElementById("AN_timer").style.display="";
  document.getElementById("AN_pregunta").style.display="";
  AN_ok=0;AN_idx=0;
  var ids=AN_data.map(function(_,i){return i});
  AN_orden=AN_shuffle(ids).slice(0,Math.min(AN_TOTAL,AN_data.length));
  AN_render();
}

fetch(AN_base+"analogias.json")
  .then(function(r){return r.json()})
  .then(function(data){
    AN_data=data;
    document.getElementById("AN_iniciarBtn").disabled=false;
  })
  .catch(function(){
    document.getElementById("AN_explica").textContent="Error Juego 1";
  });

document.getElementById("AN_iniciarBtn").addEventListener("click",AN_iniciar);

document.getElementById("AN_wrap").closest("#content")?.addEventListener("contentUnload",AN_limpiar,{once:true});
})();
</script>
<br>

<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones </a>