<div style="text-align:center;position:relative;padding-top:0;margin-top:0">
<style>
.pw-st{color:rgba(255,255,255,.75);font-size:1.3em;font-weight:600;margin:10px 0 22px;min-height:1.6em;transition:color .2s}
.pw-st.act{color:rgba(56,189,248,.9)}
.pw-st.ok{color:rgba(37,211,102,.9)}
.pw-st.er{color:rgba(239,68,68,.9)}
.pw-wrap{padding:0 12px;max-width:100%}
.pw-bar{display:flex;align-items:center;gap:8px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.13);border-radius:24px;padding:10px 16px;margin-bottom:14px;position:relative;overflow:hidden;transition:border-color .2s,box-shadow .2s;max-width:420px;margin-left:auto;margin-right:auto}
.pw-bar:focus-within{border-color:rgba(56,189,248,.4);box-shadow:0 0 0 3px rgba(56,189,248,.08)}
.pw-bar input{flex:1;background:none;border:none;outline:none;color:white;font-size:.9em;min-width:0;font-family:inherit}
.pw-bar input::placeholder{color:rgba(255,255,255,.4)}
.pw-ib{background:none;border:none;color:white;cursor:pointer;font-size:1.1rem;flex-shrink:0;padding:0 2px;opacity:.7;transition:opacity .2s,transform .2s;line-height:1;font-family:inherit}
.pw-ib:hover{opacity:1;transform:scale(1.1)}
.pw-ib:disabled{opacity:.3;cursor:not-allowed;transform:none}
.pw-note{color:rgba(255,255,255,.38);font-size:.76em;max-width:380px;margin:0 auto 16px;line-height:1.5}
.pw-card{border-radius:14px;padding:14px 16px;margin:8px auto;max-width:420px;text-align:left;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.06)}
.pw-card.g{border-color:rgba(37,211,102,.4);background:rgba(37,211,102,.08)}
.pw-card.r{border-color:rgba(239,68,68,.4);background:rgba(239,68,68,.08)}
.pw-ch{font-weight:700;font-size:1em;margin-bottom:6px;display:flex;align-items:center;gap:8px;color:#fff}
.pw-cd{font-size:.82em;color:rgba(255,255,255,.6);line-height:1.55}
.pw-gen-row{display:flex;align-items:center;gap:10px;justify-content:center;margin-bottom:10px;flex-wrap:wrap}
.pw-gen-row label{color:rgba(255,255,255,.7);font-size:.85em}
.pw-gen-row input[type=number]{width:64px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.13);border-radius:10px;color:#fff;padding:6px 8px;font-family:inherit;text-align:center}
.pw-ck{display:flex;align-items:center;gap:6px;flex-wrap:wrap;justify-content:center;margin-bottom:14px}
.pw-ck label{display:flex;align-items:center;gap:5px;color:rgba(255,255,255,.7);font-size:.82em;background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:16px;padding:5px 12px;cursor:pointer}
.pw-out{font-family:monospace;font-size:1.05em;word-break:break-all;color:#fff;background:rgba(0,0,0,.25);border-radius:10px;padding:10px 12px;margin-top:8px;min-height:1.4em;user-select:all}
</style>

<div style="font-size:2.8rem;margin:0 auto 4px;line-height:1.2">🔐</div>
<div class="pw-st" id="pw-st">Pwned Checker</div>

<div class="pw-wrap">
  <div class="pw-bar" id="pw-pb-bar">
    <input type="text" id="pw-pi" placeholder="Contraseña a verificar..." autocomplete="new-password" autocorrect="off" autocapitalize="off" spellcheck="false" name="q-3f7a">
    <button class="pw-ib" id="pw-pb" title="Verificar">🔍</button>
  </div>
  <div class="pw-note">🔒 Solo los primeros 5 chars del hash SHA-1 se envian. La contraseña nunca sale del dispositivo.</div>
  <div id="pw-pr"></div>
</div>

<div style="font-size:2.8rem;margin:36px auto 4px;line-height:1.2">🎲</div>
<div class="pw-st" id="gp-st">Crear Contraseña Segura</div>

<div class="pw-wrap">
  <div class="pw-gen-row">
    <label for="gp-len">Longitud</label>
    <input type="number" id="gp-len" value="20" min="12">
  </div>
  <div class="pw-ck">
    <label><input type="checkbox" id="gp-rare">Simbolos raros</label>
    <label><input type="checkbox" id="gp-emoji">Emojis</label>
    <label><input type="checkbox" id="gp-glyph">Otros alfabetos y jeroglificos</label>
  </div>
  <div class="pw-note">⚠️ Emojis y otros alfabetos no son aceptados por todas las plataformas (ej. Google).</div>
  <button id="gp-btn">Generar</button>
  <div class="pw-out" id="gp-out"></div>
</div>

<div class="pw-tk" id="pw-tk"></div>

<script>
(function(){
  const $=id=>document.getElementById(id);
  const st=$('pw-st'),tk=$('pw-tk'),pi=$('pw-pi'),r=$('pw-pr');
  let _btt=null,_deb=null;

  function PW_T(msg){
    clearTimeout(_btt);
    tk.textContent=msg;tk.classList.add('show');
    _btt=setTimeout(()=>tk.classList.remove('show'),2800);
  }

  function PW_ST(txt,cls){
    st.textContent=txt;st.className='pw-st'+(cls?' '+cls:'');
  }

  function PW_FN(n){
    return n>=1e9?(n/1e9).toFixed(1)+'B':n>=1e6?(n/1e6).toFixed(1)+'M':n>=1e3?Math.round(n/1e3)+'K':String(n);
  }

  async function PW_HP(pass){
    const buf=await crypto.subtle.digest('SHA-1',new TextEncoder().encode(pass));
    const hex=[...new Uint8Array(buf)].map(b=>b.toString(16).padStart(2,'0')).join('').toUpperCase();
    const pre=hex.slice(0,5),suf=hex.slice(5);
    const res=await fetch('https://api.pwnedpasswords.com/range/'+pre,{headers:{'Add-Padding':'true'}});
    const txt=await res.text();
    const found=txt.split('\n').find(l=>l.startsWith(suf));
    return found?parseInt(found.split(':')[1].trim()):0;
  }

  const ZX_CDN=[
    'https://cdn.jsdelivr.net/npm/@zxcvbn-ts/language-common@4.1.3/dist/zxcvbn-ts.js',
    'https://cdn.jsdelivr.net/npm/@zxcvbn-ts/language-es-es@4.1.2/dist/zxcvbn-ts.js',
    'https://cdn.jsdelivr.net/npm/@zxcvbn-ts/core@4.1.2/dist/zxcvbn-ts.js'
  ];
  let zxInst=null,zxLoadP=null;

  function ZX_LOAD(){
    if(zxInst)return Promise.resolve(zxInst);
    if(zxLoadP)return zxLoadP;
    zxLoadP=new Promise((res,rej)=>{
      let i=0;
      const loadNext=()=>{
        if(i>=ZX_CDN.length){
          const ns=window.zxcvbnts;
          const common=ns['language-common'],es=ns['language-es-es'],core=ns.core;
          const opts={
            translations:es.translations,
            graphs:common.adjacencyGraphs,
            dictionary:{...common.dictionary,...es.dictionary}
          };
          zxInst=new core.ZxcvbnFactory(opts);
          res(zxInst);
          return;
        }
        const s=document.createElement('script');
        s.src=ZX_CDN[i];
        s.onload=()=>{i++;loadNext();};
        s.onerror=()=>rej(new Error('ZX load fail '+ZX_CDN[i]));
        document.head.appendChild(s);
      };
      loadNext();
    });
    return zxLoadP;
  }

  const ZX_SC=['Muy debil','Debil','Regular','Fuerte','Muy fuerte'];

  function ZX_CARD(r){
    const ct=r.crackTimes;
    return`<div class="pw-card r">
<div class="pw-ch">🧩 Analisis de patron: ${ZX_SC[r.score]}</div>
<div class="pw-cd">
${r.feedback.warning?r.feedback.warning+'<br>':''}
Tiempo estimado para descifrarla:<br>
• Ataque online con limite (100/hora): ${ct.onlineThrottlingXPerHour.display}<br>
• Ataque online sin limite (10/seg): ${ct.onlineNoThrottlingXPerSecond.display}<br>
• Ataque offline, hash lento: ${ct.offlineSlowHashingXPerSecond.display}<br>
• Ataque offline, hash rapido (super computadora): ${ct.offlineFastHashingXPerSecond.display}
</div>
</div>`;
  }

  async function PW_CHK(){
    const pass=pi.value;
    if(!pass){r.innerHTML='';PW_ST('Pwned Checker');return;}
    const btn=$('pw-pb');btn.disabled=true;
    PW_ST('Verificando...','act');
    r.innerHTML='';
    try{
      const n=await PW_HP(pass);
      if(n===0){
        r.innerHTML=`<div class="pw-card g"><div class="pw-ch">✅ Sin filtraciones conocidas</div><div class="pw-cd">Esta contraseña no aparece en ninguna base de datos filtrada. No garantiza que sea segura, pero es buena señal.</div></div>`;
        PW_ST('Sin filtraciones','ok');
      } else {
        r.innerHTML=`<div class="pw-card r"><div class="pw-ch">⚠️ Encontrada ${PW_FN(n)} ${n===1?'vez':'veces'}</div><div class="pw-cd">Esta contraseña aparece en filtraciones de datos. Cambiala en todos los servicios donde la uses.</div></div>`;
        PW_ST('Contraseña comprometida','er');
        try{
          const zx=await ZX_LOAD();
          r.insertAdjacentHTML('beforeend',ZX_CARD(zx.check(pass)));
        }catch(e){
          r.insertAdjacentHTML('beforeend','<div class="pw-note">No se pudo cargar el analisis de patron.</div>');
        }
      }
    }catch{
      PW_T('Error al verificar');PW_ST('Pwned Checker');
    }
    btn.disabled=false;
  }

  pi.addEventListener('input',()=>{
    clearTimeout(_deb);
    _deb=setTimeout(PW_CHK,5000);
  });
  pi.addEventListener('keydown',e=>{if(e.key==='Enter'){clearTimeout(_deb);PW_CHK();}});
  $('pw-pb').onclick=()=>{clearTimeout(_deb);PW_CHK();};

  const GP_LOW='abcdefghijklmnopqrstuvwxyz';
  const GP_UP='ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  const GP_NUM='0123456789';
  const GP_SYM='!@#$%^&*()-_=+[]{}';
  const GP_RARE='~`<>|\\/:;"\',.?';
  const GP_EMOJI_RANGES=[[0x1F300,0x1F5FF],[0x1F600,0x1F64F],[0x1F680,0x1F6FF],[0x1F900,0x1F9FF],[0x1FA70,0x1FAFF],[0x2700,0x27BF],[0x1F650,0x1F67F],[0x2600,0x26FF]];
  const GP_GLYPH_RANGES=[[0x0600,0x06FF],[0x0590,0x05FF],[0x0370,0x03FF],[0x0400,0x04FF],[0x0900,0x097F],[0x0E00,0x0E7F],[0xAC00,0xD7A3],[0x4E00,0x9FFF],[0x3040,0x309F],[0x30A0,0x30FF],[0x13000,0x1342E],[0x12000,0x123FF],[0x16A0,0x16FF],[0x2200,0x22FF]];

  function GP_RI(max){
    const buf=new Uint32Array(1);
    crypto.getRandomValues(buf);
    return buf[0]%max;
  }

  function GP_RC(pool){
    return pool[GP_RI(pool.length)];
  }

  function GP_RE(ranges){
    const [a,b]=ranges[GP_RI(ranges.length)];
    const cp=a+GP_RI(b-a+1);
    return String.fromCodePoint(cp);
  }

  function GP_GEN(len,useRare,useEmoji,useGlyph){
    let pool=GP_LOW+GP_UP+GP_NUM+GP_SYM;
    if(useRare)pool+=GP_RARE;
    const extraGens=[];
    if(useEmoji)extraGens.push(()=>GP_RE(GP_EMOJI_RANGES));
    if(useGlyph)extraGens.push(()=>GP_RE(GP_GLYPH_RANGES));
    const out=[];
    for(let i=0;i<len;i++){
      if(extraGens.length&&GP_RI(4)===0){
        out.push(extraGens[GP_RI(extraGens.length)]());
      }else{
        out.push(GP_RC(pool));
      }
    }
    return out.join('');
  }

  function GP_OK(p,useRare,useEmoji,useGlyph){
    const cs=[...p],cp=cs.map(c=>c.codePointAt(0)),inR=r=>cp.some(x=>r.some(([a,b])=>x>=a&&x<=b));
    return [GP_LOW,GP_UP,GP_NUM,GP_SYM].concat(useRare?[GP_RARE]:[]).every(t=>cs.some(c=>t.includes(c)))&&(!useEmoji||inR(GP_EMOJI_RANGES))&&(!useGlyph||inR(GP_GLYPH_RANGES));
  }

  $('gp-btn').onclick=()=>{
    const len=Math.max(12,parseInt($('gp-len').value)||20),r=$('gp-rare').checked,e=$('gp-emoji').checked,g=$('gp-glyph').checked;
    let pass;
    do pass=GP_GEN(len,r,e,g);while(!GP_OK(pass,r,e,g));
    $('gp-out').textContent=pass;
    if(navigator.clipboard)navigator.clipboard.writeText(pass).then(()=>PW_T('Copiada al portapapeles')).catch(()=>{});
  };
})();
</script>

</div>


<div style="text-align:center;">
  <a href="web/paginas/apps.html" class="back-button">← Volver al Inicio</a>
</div>