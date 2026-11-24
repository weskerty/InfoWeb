<!DOCTYPE html>
<html lang="es">
<head><meta charset="UTF-8"></head>
<body>

<style data-content>
@import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap');
:root{
  --e-bg:#080810;
  --e-acc:#c8ff00;
  --e-red:#ff2d4e;
  --e-dim:#ffffff18;
  --e-txt:#e8e8e8;
  --e-spy:#ff9900;
  --e-mono:'Share Tech Mono',monospace;
  --e-head:'Share Tech Mono',monospace;
}
*{box-sizing:border-box;margin:0;padding:0;}
#ES_W{
  width:100%;
  min-height:100vh;
  font-family:var(--e-mono);
  color:var(--e-txt);
  background:transparent;
  display:flex;
  flex-direction:column;
  align-items:center;
  padding:24px 16px 40px;
  user-select:none;
  -webkit-user-select:none;
}
.ES_screen{width:100%;max-width:480px;display:none;flex-direction:column;gap:14px;}
.ES_screen.ES_act{display:flex;}
h1{
  font-family:var(--e-head);
  font-size:3rem;
  letter-spacing:6px;
  color:var(--e-acc);
  text-shadow:0 0 30px #c8ff0055;
  text-align:center;
  line-height:1;
}
h2{
  font-family:var(--e-head);
  font-size:1.6rem;
  letter-spacing:4px;
  color:var(--e-acc);
}
.ES_sub{font-size:.7rem;color:#ffffff44;letter-spacing:2px;text-align:center;}
.ES_btn{
  padding:10px 20px;
  background:transparent;
  border:1px solid var(--e-acc);
  color:var(--e-acc);
  font-family:var(--e-mono);
  font-size:.85rem;
  letter-spacing:2px;
  cursor:pointer;
  text-transform:uppercase;
  transition:background .15s,color .15s,box-shadow .15s;
  width:100%;
}
.ES_btn:hover,.ES_btn:active{background:var(--e-acc);color:#080810;}
.ES_btn.ES_red{border-color:var(--e-red);color:var(--e-red);}
.ES_btn.ES_red:hover{background:var(--e-red);color:#fff;}
.ES_btn.ES_dim{border-color:#ffffff33;color:#ffffff55;}
.ES_btn.ES_dim:hover{background:#ffffff11;color:#fff;}
.ES_btn.ES_sm{padding:6px 12px;font-size:.75rem;width:auto;}
.ES_inp{
  width:100%;
  padding:10px 12px;
  background:transparent;
  border:1px solid #ffffff33;
  color:var(--e-txt);
  font-family:var(--e-mono);
  font-size:.85rem;
  letter-spacing:1px;
  outline:none;
  transition:border-color .2s;
}
.ES_inp:focus{border-color:var(--e-acc);}
.ES_divider{height:1px;background:var(--e-dim);width:100%;}
.ES_label{font-size:.65rem;color:#ffffff44;letter-spacing:2px;text-transform:uppercase;}
.ES_card{
  border:1px solid var(--e-dim);
  padding:14px;
  display:flex;
  flex-direction:column;
  gap:8px;
}
.ES_row{display:flex;align-items:center;gap:8px;}
.ES_row .ES_grow{flex:1;}
#ES_lobbies{display:flex;flex-direction:column;gap:8px;min-height:60px;}
.ES_lobby_item{
  border:1px solid #ffffff22;
  padding:10px 14px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  cursor:pointer;
  transition:border-color .15s,background .15s;
}
.ES_lobby_item:hover{border-color:var(--e-acc);background:#c8ff0008;}
.ES_lobby_name{font-size:.9rem;color:var(--e-acc);}
.ES_lobby_count{font-size:.7rem;color:#ffffff55;}
#ES_players{display:flex;flex-direction:column;gap:6px;}
.ES_player_row{
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:8px 10px;
  border:1px solid var(--e-dim);
  font-size:.8rem;
}
.ES_player_me{border-color:#ffffff33;color:var(--e-acc);}
.ES_player_muted{opacity:.45;}
.ES_mute_btn{
  background:transparent;
  border:1px solid #ffffff33;
  color:#fff;
  font-size:.8rem;
  padding:3px 8px;
  cursor:pointer;
  transition:border-color .15s;
}
.ES_mute_btn:hover{border-color:var(--e-red);color:var(--e-red);}
#ES_word_reveal{
  text-align:center;
  padding:30px 20px;
  border:1px solid var(--e-acc);
  background:#c8ff0006;
  display:flex;
  flex-direction:column;
  gap:10px;
  animation:ES_fadein .6s ease;
}
@keyframes ES_fadein{from{opacity:0;transform:scale(.96)}to{opacity:1;transform:scale(1)}}
#ES_word_big{
  font-family:var(--e-head);
  font-size:3rem;
  color:var(--e-acc);
  letter-spacing:4px;
  text-shadow:0 0 20px #c8ff0066;
  transition:font-size 1s ease;
}
#ES_word_big.ES_shrink{font-size:1.2rem;}
#ES_word_role{font-size:.7rem;letter-spacing:3px;color:#ffffff55;}
#ES_turn_bar{
  border:1px solid var(--e-dim);
  padding:12px 14px;
  display:flex;
  flex-direction:column;
  gap:6px;
}
#ES_turn_name{font-size:1rem;color:var(--e-acc);letter-spacing:2px;}
#ES_turn_timer{
  font-size:2rem;
  font-family:var(--e-head);
  color:var(--e-acc);
  letter-spacing:4px;
}
#ES_turn_timer.ES_urgent{color:var(--e-red);animation:ES_blink .5s infinite;}
@keyframes ES_blink{0%,100%{opacity:1}50%{opacity:.3}}
#ES_vote_list{display:flex;flex-direction:column;gap:6px;}
.ES_vote_item{
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:10px 14px;
  border:1px solid var(--e-dim);
  cursor:pointer;
  transition:border-color .15s,background .15s;
}
.ES_vote_item:hover:not(.ES_voted_for){border-color:var(--e-acc);background:#c8ff0008;}
.ES_vote_item.ES_voted_for{border-color:var(--e-acc);background:#c8ff0015;}
.ES_vote_count{font-size:.7rem;color:#ffffff55;}
#ES_result_box{
  text-align:center;
  padding:24px;
  border:1px solid var(--e-dim);
  display:flex;
  flex-direction:column;
  gap:12px;
}
#ES_result_title{font-family:var(--e-head);font-size:2.5rem;letter-spacing:4px;}
#ES_result_title.ES_win{color:var(--e-acc);}
#ES_result_title.ES_lose{color:var(--e-red);}
#ES_result_detail{font-size:.8rem;color:#ffffff77;line-height:1.6;}
.ES_notice{font-size:.75rem;color:#ffffff44;text-align:center;letter-spacing:1px;}
#ES_status{font-size:.7rem;color:#ffffff33;text-align:right;letter-spacing:1px;}
</style>

<div id="ES_W">

  <div id="ES_s_lobby" class="ES_screen ES_act">
    <h1>ESPÍA</h1>
    <div class="ES_sub">AMIGO ESPÍA — P2P</div>
    <div class="ES_divider"></div>
    <div class="ES_label">Salas activas</div>
    <div id="ES_lobbies"><div class="ES_notice">Buscando salas...</div></div>
    <div class="ES_divider"></div>
    <div class="ES_label">Crear sala</div>
    <input id="ES_room_name" class="ES_inp" placeholder="Nombre de sala..." maxlength="24">
    <button id="ES_create_btn" class="ES_btn">Crear sala</button>
    <div id="ES_status"></div>
  </div>

  <div id="ES_s_room" class="ES_screen">
    <div class="ES_row">
      <h2 id="ES_room_title" class="ES_grow">SALA</h2>
      <button id="ES_leave_btn" class="ES_btn ES_red ES_sm">Salir</button>
    </div>
    <div class="ES_row">
      <button id="ES_my_mute_btn" class="ES_btn ES_dim ES_sm">🎤 Mic</button>
      <div id="ES_room_status" class="ES_grow ES_notice"></div>
    </div>
    <div class="ES_label">Jugadores</div>
    <div id="ES_players"></div>
    <div class="ES_divider"></div>
    <button id="ES_start_btn" class="ES_btn" style="display:none">Iniciar partida</button>
    <div id="ES_wait_msg" class="ES_notice">Esperando al host...</div>
  </div>

  <div id="ES_s_word" class="ES_screen">
    <div class="ES_label">Tu palabra</div>
    <div id="ES_word_reveal">
      <div id="ES_word_role"></div>
      <div id="ES_word_big"></div>
      <div class="ES_notice" id="ES_word_hint"></div>
    </div>
    <div class="ES_notice">La palabra se reducira en 10 segundos</div>
  </div>

  <div id="ES_s_game" class="ES_screen">
    <div id="ES_word_mini" style="font-size:.8rem;color:#ffffff44;letter-spacing:1px;"></div>
    <div id="ES_turn_bar">
      <div class="ES_label">Turno</div>
      <div id="ES_turn_name">—</div>
      <div id="ES_turn_timer">1:00</div>
    </div>
    <div id="ES_players_game"></div>
    <button id="ES_pass_btn" class="ES_btn" style="display:none">Pasar turno ▶</button>
    <button id="ES_my_mute_game" class="ES_btn ES_dim ES_sm">🎤 Mic</button>
  </div>

  <div id="ES_s_vote" class="ES_screen">
    <h2>VOTACION</h2>
    <div class="ES_notice" id="ES_vote_timer_txt"></div>
    <div class="ES_label">Vota al sospechoso</div>
    <div id="ES_vote_list"></div>
    <div class="ES_notice" id="ES_vote_status"></div>
  </div>

  <div id="ES_s_result" class="ES_screen">
    <div id="ES_result_box">
      <div id="ES_result_title"></div>
      <div id="ES_result_detail"></div>
    </div>
    <button id="ES_back_lobby_btn" class="ES_btn">Volver a sala</button>
  </div>

</div>

<script>
(function(){

const BASE='web/adjuntos/Espia_Descubre_quien_es_el_Espia/';
const LOBBY_ROOM='CheAgana-Espia-Lobby';
const APP_ID={appId:'cheagana-espia-v1'};
const MAX_PLAYERS=15;
const TURN_SECS=60;
const VOTE_SECS=60;
const WORD_SHRINK_MS=10000;

let MY_ID=Math.random().toString(36).slice(2,8).toUpperCase();
const ES_U1='https://cdn.jsdelivr.net/npm/trystero@0.26.0/+esm';
const ES_A1=(r,n)=>{const a=r.makeAction(n);return[(d,t)=>a.send(d,t?{target:t}:undefined).catch(()=>{}),f=>{a.onMessage=(d,{peerId})=>f(d||{},peerId);}];};
const ES_N1=id=>String(id).slice(0,6).toUpperCase();
const ES_E1=(t,c,x)=>{const e=document.createElement(t);if(c)e.className=c;e.textContent=x;return e;};

const $=id=>document.getElementById(id);

const EL={
  lobbies:$('ES_lobbies'),
  roomName:$('ES_room_name'),
  createBtn:$('ES_create_btn'),
  status:$('ES_status'),
  roomTitle:$('ES_room_title'),
  leaveBtn:$('ES_leave_btn'),
  myMuteBtn:$('ES_my_mute_btn'),
  myMuteGame:$('ES_my_mute_game'),
  roomStatus:$('ES_room_status'),
  players:$('ES_players'),
  startBtn:$('ES_start_btn'),
  waitMsg:$('ES_wait_msg'),
  wordRole:$('ES_word_role'),
  wordBig:$('ES_word_big'),
  wordHint:$('ES_word_hint'),
  wordMini:$('ES_word_mini'),
  turnName:$('ES_turn_name'),
  turnTimer:$('ES_turn_timer'),
  playersGame:$('ES_players_game'),
  passBtn:$('ES_pass_btn'),
  voteTimerTxt:$('ES_vote_timer_txt'),
  voteList:$('ES_vote_list'),
  voteStatus:$('ES_vote_status'),
  resultTitle:$('ES_result_title'),
  resultDetail:$('ES_result_detail'),
  backLobbyBtn:$('ES_back_lobby_btn'),
};

const screens={
  lobby:$('ES_s_lobby'),
  room:$('ES_s_room'),
  word:$('ES_s_word'),
  game:$('ES_s_game'),
  vote:$('ES_s_vote'),
  result:$('ES_s_result'),
};

function showScreen(name){
  Object.values(screens).forEach(s=>s.classList.remove('ES_act'));
  screens[name].classList.add('ES_act');
}

let words=[];
async function loadWords(){
  try{
    const r=await fetch(BASE+'palabras.txt');
    const txt=await r.text();
    words=txt.trim().split('\n').map(l=>{
      const[w,h]=l.split(':');
      return{word:w.trim(),hint:h?h.trim():w.trim()};
    }).filter(l=>l.word);
  }catch(e){words=[{word:'CAFE',hint:'Bebida caliente'},{word:'PLAYA',hint:'Lugar con arena'},{word:'AVION',hint:'Transporte'},{word:'CASTILLO',hint:'Edificio antiguo'},{word:'HOSPITAL',hint:'Lugar de salud'}];}
}

let lobbyRoom=null,gameRoom=null;
let lobbyPeers={};
let knownRooms={};
let _sendAnn=null,_sendBye=null;

let roomId=null,roomName=null,isHost=false;
let gamePlayers={};
let myStream=null,peerStreams={},mutedPeers={},myMuted=false;
let spyId=null,chosenWord=null,chosenHint=null;
let turnOrder=[],turnIdx=0,turnTimer=null,voteTimer=null;
let myVote=null,votes={};
let gameActive=false;

async function initLobby(){
  EL.status.textContent='Conectando...';
  try{
    const{joinRoom,selfId}=await import(ES_U1);
    MY_ID=selfId;
    lobbyRoom=joinRoom(APP_ID,LOBBY_ROOM);

    let[sendAnn,getAnn]=ES_A1(lobbyRoom,'ann');
    let[sendBye,getBye]=ES_A1(lobbyRoom,'bye');
    _sendAnn=sendAnn;_sendBye=sendBye;

    lobbyRoom.onPeerJoin=id=>{
      lobbyPeers[id]=true;
      if(roomId&&isHost)_sendAnn({roomId,roomName,count:Object.keys(gamePlayers).length});
    };
    lobbyRoom.onPeerLeave=id=>delete lobbyPeers[id];
    getAnn(({roomId:rid,roomName:rn,count},from)=>{
      if(typeof rid!=='string')return;
      knownRooms[rid]={name:rn,count,host:from,ts:Date.now()};
      renderLobbies();
    });
    getBye(({roomId:rid})=>{
      delete knownRooms[rid];
      renderLobbies();
    });

    EL.status.textContent='';
    setInterval(()=>{
      const now=Date.now();
      Object.keys(knownRooms).forEach(k=>{if(now-knownRooms[k].ts>15000)delete knownRooms[k];});
      renderLobbies();
    },5000);
    setInterval(()=>{
      if(roomId&&isHost&&_sendAnn)_sendAnn({roomId,roomName,count:Object.keys(gamePlayers).length});
    },8000);

    loadWords();
  }catch(e){EL.status.textContent='Error red';}
}

function renderLobbies(){
  const entries=Object.entries(knownRooms);
  if(!entries.length){EL.lobbies.innerHTML='<div class="ES_notice">Sin salas activas</div>';return;}
  EL.lobbies.innerHTML='';
  entries.forEach(([rid,info])=>{
    const d=document.createElement('div');
    d.className='ES_lobby_item';
    d.append(ES_E1('span','ES_lobby_name',String(info.name)),ES_E1('span','ES_lobby_count',(+info.count||0)+'/'+MAX_PLAYERS));
    d.onclick=()=>joinRoom(rid,info.name);
    EL.lobbies.appendChild(d);
  });
}

async function createRoom(){
  const name=(EL.roomName.value.trim()||'Sala '+MY_ID.slice(0,3));
  roomId='room-'+Math.random().toString(36).slice(2,8);
  roomName=name;
  isHost=true;
  gamePlayers[MY_ID]={id:MY_ID,host:true};
  await joinGameRoom();
  showScreen('room');
  EL.roomTitle.textContent=roomName;
  EL.startBtn.style.display='';
  EL.waitMsg.style.display='none';
  renderRoomPlayers();
  if(_sendAnn)_sendAnn({roomId,roomName,count:1});
}

async function joinRoom(rid,rname){
  roomId=rid;
  roomName=rname;
  isHost=false;
  gamePlayers[MY_ID]={id:MY_ID,host:false};
  await joinGameRoom();
  showScreen('room');
  EL.roomTitle.textContent=roomName;
  EL.startBtn.style.display='none';
  EL.waitMsg.style.display='';
  renderRoomPlayers();
}

async function joinGameRoom(){
  const voicePromise=initVoice();
  try{
    const{joinRoom:jr}=await import(ES_U1);
    gameRoom=jr(APP_ID,roomId);

    let[sendJoin,getJoin]=ES_A1(gameRoom,'join');
    let[sendStart,getStart]=ES_A1(gameRoom,'start');
    let[sendTurnNext,getTurnNext]=ES_A1(gameRoom,'turn');
    let[sendVote,getVote]=ES_A1(gameRoom,'vote');
    let[sendMute,getMute]=ES_A1(gameRoom,'mute');

    gameRoom.onPeerJoin=id=>{
      gamePlayers[id]={id,host:false};
      const allKnown=Object.values(gamePlayers).map(p=>({id:p.id,host:p.host}));
      sendJoin({id:MY_ID,host:isHost,all:allKnown});
      renderRoomPlayers();
      if(isHost&&_sendAnn)_sendAnn({roomId,roomName,count:Object.keys(gamePlayers).length});
      voicePromise.then(()=>{if(myStream&&gameRoom)gameRoom.addStream(myStream,{target:id});});
    };

    gameRoom.onPeerLeave=id=>{
      delete gamePlayers[id];
      delete peerStreams[id];
      const el=document.getElementById('ES_audio_'+id);
      if(el){el.pause();el.remove();}
      renderRoomPlayers();
      if(gameActive){
        const wasIdx=turnOrder.indexOf(id);
        turnOrder=turnOrder.filter(x=>x!==id);
        if(wasIdx>=0&&wasIdx<=turnIdx&&turnIdx>0)turnIdx--;
        if(turnOrder[turnIdx]===id||!turnOrder[turnIdx])advanceTurn();
      }
    };

    getJoin(({id,host,all},from)=>{
      if(all&&Array.isArray(all)){
        all.forEach(p=>{if(p&&typeof p.id==='string'&&!gamePlayers[p.id])gamePlayers[p.id]={id:p.id,host:p.host};});
      }else{
        gamePlayers[from]={id:from,host};
      }
      renderRoomPlayers();
    });

    getStart(({order,spyIdx,word,hint},from)=>{
      if(!isHost&&Array.isArray(order)){
        turnOrder=order.map(String);
        spyId=order[spyIdx];
        chosenWord=word;
        chosenHint=hint;
        startWordReveal();
      }
    });

    getTurnNext(({idx,from:sender},peerId)=>{
      if(sender===turnOrder[turnIdx-1]||peerId===turnOrder[turnIdx-1]){
        turnIdx=idx;
        renderTurn();
      }
    });

    getVote(({voter,target},from)=>{
      votes[from]=target;
      renderVoteStatus();
    });

    getMute(({muted},from)=>{
      mutedPeers[from]=muted;
      renderRoomPlayers();
    });

    gameRoom.onPeerStream=(stream,id)=>{
      peerStreams[id]=stream;
      playStream(id,stream);
    };

    window._ES_sendTurnNext=(data)=>sendTurnNext({...data,from:MY_ID});
    window._ES_sendVote=sendVote;
    window._ES_sendMute=sendMute;
    window._ES_sendStart=sendStart;

    await voicePromise;
    if(myStream)gameRoom.addStream(myStream);
  }catch(e){}
}

async function initVoice(){
  try{
    myStream=await navigator.mediaDevices.getUserMedia({audio:{echoCancellation:1,noiseSuppression:1},video:false});
    if(gameRoom)gameRoom.addStream(myStream);
  }catch(e){myStream=null;}
}

function playStream(id,stream){
  let el=document.getElementById('ES_audio_'+id);
  if(!el){el=document.createElement('audio');el.id='ES_audio_'+id;el.autoplay=1;el.playsInline=1;document.body.appendChild(el);}
  el.srcObject=stream;
  el.volume=mutedPeers[id]?0:0.8;
}

function muteAll(){
  Object.keys(peerStreams).forEach(id=>{
    const el=document.getElementById('ES_audio_'+id);
    if(el)el.volume=0;
  });
}

function unmuteActive(activeId){
  Object.keys(peerStreams).forEach(id=>{
    const el=document.getElementById('ES_audio_'+id);
    if(el)el.volume=(id===activeId&&!mutedPeers[id])?0.8:0;
  });
  if(activeId===MY_ID&&myStream){
    myStream.getAudioTracks().forEach(t=>t.enabled=true);
  }else if(myStream){
    myStream.getAudioTracks().forEach(t=>t.enabled=false);
  }
}

function renderRoomPlayers(){
  EL.players.innerHTML='';
  const all=Object.values(gamePlayers);
  all.forEach(p=>{
    const d=document.createElement('div');
    const isMe=p.id===MY_ID;
    d.className='ES_player_row'+(isMe?' ES_player_me':'');
    d.append(ES_E1('span','',ES_N1(p.id)+(isMe?' (yo)':'')+(p.host?' ★':'')));
    if(!isMe){const b=ES_E1('button','ES_mute_btn',mutedPeers[p.id]?'🔇':'🔊');b.dataset.id=p.id;d.append(b);}
    EL.players.appendChild(d);
  });
  EL.players.querySelectorAll('.ES_mute_btn').forEach(btn=>{
    btn.onclick=()=>{
      const id=btn.dataset.id;
      mutedPeers[id]=!mutedPeers[id];
      const el=document.getElementById('ES_audio_'+id);
      if(el)el.volume=mutedPeers[id]?0:0.8;
      renderRoomPlayers();
    };
  });
}

function hostStart(){
  if(!isHost||words.length===0)return;
  const all=Object.keys(gamePlayers);
  if(all.length<2)return;
  const order=[...all].sort(()=>Math.random()-.5);
  const spyIdx=Math.floor(Math.random()*order.length);
  const w=words[Math.floor(Math.random()*words.length)];
  spyId=order[spyIdx];
  chosenWord=w.word;
  chosenHint=w.hint;
  turnOrder=order;
  turnIdx=0;
  window._ES_sendStart({order,spyIdx,word:w.word,hint:w.hint});
  startWordReveal();
}

function startWordReveal(){
  gameActive=true;
  const isSpy=MY_ID===spyId;
  EL.wordRole.textContent=isSpy?'ERES EL ESPÍA':'JUGADOR';
  EL.wordBig.textContent=isSpy?chosenHint:chosenWord;
  EL.wordBig.classList.remove('ES_shrink');
  EL.wordHint.textContent=isSpy?'Tu pista — actua normal':'Recuerdala bien';
  showScreen('word');
  setTimeout(()=>{
    EL.wordBig.classList.add('ES_shrink');
    setTimeout(()=>startGamePhase(),1000);
  },WORD_SHRINK_MS);
}

function startGamePhase(){
  turnIdx=0;
  EL.wordMini.textContent='Palabra: '+(MY_ID===spyId?chosenHint:chosenWord);
  showScreen('game');
  muteAll();
  renderTurn();
  renderGamePlayers();
}

function renderGamePlayers(){
  EL.playersGame.innerHTML='';
  turnOrder.forEach((id,i)=>{
    const d=document.createElement('div');
    d.className='ES_player_row';
    d.id='ES_gp_'+id;
    const n=ES_E1('span','','#'+(i+1));n.style.cssText='font-size:.7rem;color:#ffffff33';
    d.append(ES_E1('span','',ES_N1(id)+(id===MY_ID?' (yo)':'')),n);
    EL.playersGame.appendChild(d);
  });
}

function renderTurn(){
  const activeId=turnOrder[turnIdx];
  if(!activeId){startVote();return;}
  EL.turnName.textContent=ES_N1(activeId)+(activeId===MY_ID?' (TU TURNO)':'');
  EL.passBtn.style.display=(activeId===MY_ID)?'':'none';
  document.querySelectorAll('.ES_player_row[id^="ES_gp_"]').forEach(el=>{
    el.style.borderColor=el.id==='ES_gp_'+activeId?'var(--e-acc)':'';
  });
  unmuteActive(activeId);
  startTurnTimer();
}

let turnSecs=TURN_SECS;
function startTurnTimer(){
  clearInterval(turnTimer);
  turnSecs=TURN_SECS;
  renderTurnTimer();
  turnTimer=setInterval(()=>{
    turnSecs--;
    renderTurnTimer();
    if(turnSecs<=0){clearInterval(turnTimer);advanceTurn();}
  },1000);
}

function renderTurnTimer(){
  const m=Math.floor(turnSecs/60),s=turnSecs%60;
  EL.turnTimer.textContent=m+':'+(s<10?'0':'')+s;
  EL.turnTimer.classList.toggle('ES_urgent',turnSecs<=10);
}

function advanceTurn(){
  clearInterval(turnTimer);
  const wasActive=turnOrder[turnIdx];
  turnIdx++;
  if(turnIdx>=turnOrder.length){
    if(wasActive===MY_ID||isHost)startVote();
    return;
  }
  if(wasActive===MY_ID){
    if(window._ES_sendTurnNext)window._ES_sendTurnNext({idx:turnIdx});
  }
  renderTurn();
}

function startVote(){
  muteAll();
  if(myStream)myStream.getAudioTracks().forEach(t=>t.enabled=false);
  myVote=null;
  votes={};
  showScreen('vote');
  renderVoteList();
  let vsecs=VOTE_SECS;
  EL.voteTimerTxt.textContent='Tiempo: '+vsecs+'s';
  voteTimer=setInterval(()=>{
    vsecs--;
    EL.voteTimerTxt.textContent='Tiempo: '+vsecs+'s';
    if(vsecs<=0){clearInterval(voteTimer);resolveVote();}
  },1000);
}

function renderVoteList(){
  EL.voteList.innerHTML='';
  turnOrder.forEach(id=>{
    if(id===MY_ID)return;
    const d=document.createElement('div');
    d.className='ES_vote_item'+(myVote===id?' ES_voted_for':'');
    const c=ES_E1('span','ES_vote_count','0 votos');c.id='ES_vc_'+id;
    d.append(ES_E1('span','',ES_N1(id)),c);
    d.onclick=()=>{
      if(myVote)return;
      myVote=id;
      votes[MY_ID]=id;
      if(window._ES_sendVote)window._ES_sendVote({voter:MY_ID,target:id});
      renderVoteList();
      renderVoteStatus();
    };
    EL.voteList.appendChild(d);
  });
}

function renderVoteStatus(){
  const counts={};
  Object.values(votes).forEach(t=>{counts[t]=(counts[t]||0)+1;});
  Object.entries(counts).forEach(([id,c])=>{
    const el=document.getElementById('ES_vc_'+id);
    if(el)el.textContent=c+' voto'+(c!==1?'s':'');
  });
  const total=Object.keys(gamePlayers).length;
  const cast=Object.keys(votes).length;
  EL.voteStatus.textContent=cast+'/'+total+' votos emitidos';
  if(cast>=total){clearInterval(voteTimer);resolveVote();}
}

function resolveVote(){
  const counts={};
  Object.values(votes).forEach(t=>{counts[t]=(counts[t]||0)+1;});
  let maxId=null,maxC=0;
  Object.entries(counts).forEach(([id,c])=>{if(c>maxC){maxC=c;maxId=id;}});
  const isSpy=maxId===spyId;
  const majority=maxC>Object.keys(gamePlayers).length/2;
  EL.resultTitle.textContent=isSpy?(majority?'ESPIA ATRAPADO':'EMPATE'):('INOCENTE VOTADO');
  EL.resultTitle.className='ES_result_title '+(isSpy&&majority?'ES_win':'ES_lose');
  EL.resultDetail.textContent=
    'Mas votado: '+ES_N1(maxId)+'\n'+
    'El espia era: '+ES_N1(spyId)+'\n'+
    'La palabra era: '+chosenWord+'\n'+
    (isSpy&&majority?'Los jugadores ganaron!':isSpy?'Empate — el espia sobrevive':'El espia gana — votaron a un inocente');
  gameActive=false;
  showScreen('result');
}

function leaveRoom(){
  clearInterval(turnTimer);
  clearInterval(voteTimer);
  if(gameRoom){
    if(isHost&&_sendBye)_sendBye({roomId});
    try{gameRoom.leave();}catch(e){}
    gameRoom=null;
  }
  document.querySelectorAll('audio[id^="ES_audio_"]').forEach(el=>{el.pause();el.remove();});
  gamePlayers={};
  peerStreams={};
  mutedPeers={};
  roomId=null;roomName=null;isHost=false;
  spyId=null;chosenWord=null;chosenHint=null;
  turnOrder=[];turnIdx=0;myVote=null;votes={};gameActive=false;
  showScreen('lobby');
  renderLobbies();
}

EL.createBtn.onclick=createRoom;
EL.leaveBtn.onclick=leaveRoom;
EL.backLobbyBtn.onclick=leaveRoom;
EL.startBtn.onclick=hostStart;
EL.passBtn.onclick=advanceTurn;

function toggleMyMute(){
  myMuted=!myMuted;
  if(myStream)myStream.getAudioTracks().forEach(t=>t.enabled=!myMuted);
  const label=myMuted?'🔇 Mic':'🎤 Mic';
  EL.myMuteBtn.textContent=label;
  EL.myMuteGame.textContent=label;
  if(window._ES_sendMute)window._ES_sendMute({muted:myMuted});
}
EL.myMuteBtn.onclick=toggleMyMute;
EL.myMuteGame.onclick=toggleMyMute;

const content=document.getElementById('content');
if(content){
  content.addEventListener('contentUnload',()=>{
    leaveRoom();
    if(lobbyRoom){try{lobbyRoom.leave();}catch(e){}lobbyRoom=null;}
    if(myStream){myStream.getTracks().forEach(t=>t.stop());myStream=null;}
  },{once:true});
}

initLobby();

})();
</script>

</body>
</html>