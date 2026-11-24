<style data-content>
#FL_wrap{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:16px;padding:24px;max-width:600px;margin:0 auto}
#FL_barra{width:100%;text-align:center;font-size:.9em;opacity:.8}
#FL_timer{width:100%;height:6px;background:rgba(255,255,255,.15);border-radius:3px;overflow:hidden}
#FL_timerBar{height:100%;width:100%;background:currentColor;transition:width 1s linear}
#FL_pregunta{font-size:1.2em;font-weight:600;text-align:center;line-height:1.4}
#FL_explica{font-size:.9em;opacity:.85;text-align:center;max-width:500px;line-height:1.5}
#FL_explica a{color:inherit}
#FL_inicio{display:flex;flex-direction:column;align-items:center;gap:16px;text-align:center}
#FL_iniciarBtn{padding:12px 24px;border-radius:10px;border:1px solid rgba(255,255,255,.3);background:rgba(255,255,255,.08);cursor:pointer;font-size:1em}
#FL_opciones{display:flex;gap:12px;width:100%}
.FL_op{flex:1;padding:14px;border-radius:12px;border:1px solid rgba(255,255,255,.2);background:rgba(255,255,255,.05);color:inherit;font:inherit;cursor:pointer;text-align:center;transition:background .2s}
.FL_op:hover{background:rgba(255,255,255,.12)}
#FL_final{flex:1;text-align:center;display:flex;flex-direction:column;gap:12px}
#FL_estrellas{font-size:2em}
#FL_reintentar{padding:10px 20px;border-radius:10px;border:1px solid rgba(255,255,255,.3);background:rgba(255,255,255,.08);cursor:pointer}
</style>

<div id="FL_wrap">
<div id="FL_inicio">
<div id="FL_explica">Una falacia es un razonamiento que parece valido pero no lo es. Vas a leer un argumento y decidir si tiene un razonamiento correcto (Verdad) o si es una falacia (Mentira). Ver mas info en <a href="http://www.objetos.unam.mx/logica/falacias/index.html" target="_blank" rel="noopener">Tipos de Falacia ↗️</a></div>
<button id="FL_iniciarBtn" disabled>Iniciar Juego</button>
</div>
<div id="FL_barra" style="display:none"><span id="FL_contador"></span></div>
<div id="FL_timer" style="display:none"><div id="FL_timerBar"></div></div>
<div id="FL_pregunta" style="display:none"></div>
<div id="FL_opciones"></div>
</div>

<script>
(function(){
var FL_base="web/adjuntos/Falacioso_Detector_de_Mentiras/";
var FL_TOTAL=20;
var FL_TIME=15;
var FL_data=[],FL_orden=[],FL_idx=0,FL_ok=0,FL_int=null,FL_seg=0,FL_activo=false;

function FL_shuffle(a){
  for(var i=a.length-1;i>0;i--){
    var j=Math.floor(Math.random()*(i+1));
    var t=a[i];a[i]=a[j];a[j]=t;
  }
  return a;
}

function FL_limpiar(){
  clearInterval(FL_int);
  FL_int=null;
  FL_activo=false;
}

function FL_render(){
  var q=FL_data[FL_orden[FL_idx]];
  document.getElementById("FL_contador").textContent=(FL_idx+1)+"/"+FL_orden.length;
  document.getElementById("FL_pregunta").textContent=q.pregunta;
  var cont=document.getElementById("FL_opciones");
  cont.innerHTML="";
  [["Verdad",true],["Mentira",false]].forEach(function(op){
    var d=document.createElement("button");
    d.className="FL_op";
    d.textContent=op[0];
    d.addEventListener("click",function(){FL_responder(op[1],q.correct)});
    cont.appendChild(d);
  });
  FL_seg=FL_TIME;
  var bar=document.getElementById("FL_timerBar");
  bar.style.transition="none";
  bar.style.width="100%";
  void bar.offsetWidth;
  bar.style.transition="width 1s linear";
  FL_activo=true;
  clearInterval(FL_int);
  FL_int=setInterval(function(){
    FL_seg--;
    bar.style.width=Math.max(0,(FL_seg/FL_TIME)*100)+"%";
    if(FL_seg<=0){
      clearInterval(FL_int);
      FL_responder(null,q.correct);
    }
  },1000);
}

function FL_responder(resp,correcta){
  if(!FL_activo)return;
  FL_activo=false;
  clearInterval(FL_int);
  if(resp===correcta)FL_ok++;
  FL_idx++;
  if(FL_idx>=FL_orden.length)FL_final();
  else FL_render();
}

function FL_final(){
  FL_limpiar();
  document.getElementById("FL_timer").style.display="none";
  document.getElementById("FL_pregunta").style.display="none";
  document.getElementById("FL_contador").textContent="";
  var cont=document.getElementById("FL_opciones");
  cont.innerHTML="";
  var porEstrella=FL_orden.length/5;
  var estrellas=Math.max(1,Math.round(FL_ok/porEstrella));
  var f=document.createElement("div");
  f.id="FL_final";
  f.innerHTML="<div>Tu puntuacion es:</div><div id=\"FL_estrellas\">"+"\u2b50".repeat(estrellas)+"</div>";
  var btn=document.createElement("button");
  btn.id="FL_reintentar";
  btn.textContent="Jugar de nuevo";
  btn.addEventListener("click",FL_iniciar);
  f.appendChild(btn);
  cont.appendChild(f);
}

function FL_iniciar(){
  document.getElementById("FL_inicio").style.display="none";
  document.getElementById("FL_barra").style.display="";
  document.getElementById("FL_timer").style.display="";
  document.getElementById("FL_pregunta").style.display="";
  FL_ok=0;FL_idx=0;
  var ids=FL_data.map(function(_,i){return i});
  FL_orden=FL_shuffle(ids).slice(0,Math.min(FL_TOTAL,FL_data.length));
  FL_render();
}

fetch(FL_base+"falacias.json")
  .then(function(r){return r.json()})
  .then(function(data){
    FL_data=data;
    document.getElementById("FL_iniciarBtn").disabled=false;
  })
  .catch(function(){
    document.getElementById("FL_explica").textContent="Error Juego 1";
  });

document.getElementById("FL_iniciarBtn").addEventListener("click",FL_iniciar);

document.getElementById("FL_wrap").closest("#content")?.addEventListener("contentUnload",FL_limpiar,{once:true});
})();
</script>

<br>

<a href="web/paginas/apps.html" class="back-button">← Volver a Aplicaciones </a>