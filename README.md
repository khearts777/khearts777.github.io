<!DOCTYPE html>
<html>
<head>
<title>K-HEARTS Official Fan Hub</title>
<style>
/* ===== GENERAL ===== */
body{margin:0;font-family:Georgia, serif;background:linear-gradient(to bottom,#fff0f5,#ffe4ec);color:#b03060;overflow-x:hidden;}
h1,h2{color:#ff69b4;text-shadow:0 0 25px #ffb6c1;}
h1{font-size:60px;margin-top:50px;animation:fadeIn 2s;}
h2{font-size:45px;margin-top:50px;}
button{padding:12px 30px;border:none;border-radius:25px;background:hotpink;color:white;cursor:pointer;margin:20px;transition:0.3s;}
button:hover{background:#ff1493;transform:scale(1.05);}
nav{position:fixed; top:0; width:100%; background:rgba(255,255,255,0.85); display:flex; justify-content:center; gap:20px; padding:15px; z-index:1000; box-shadow:0 5px 15px rgba(255,182,193,0.4);}
nav a{text-decoration:none;color:hotpink;font-weight:bold;font-size:18px;cursor:pointer;transition:0.3s;}
nav a:hover{color:#ff1493; letter-spacing:2px; text-shadow:0 0 10px #ff69b4; animation:wiggle 0.5s;}
@keyframes wiggle{0%{transform:rotate(0deg);}25%{transform:rotate(5deg);}50%{transform:rotate(-5deg);}75%{transform:rotate(3deg);}100%{transform:rotate(0deg);}}
.page{display:none;width:100%;min-height:100vh;padding-top:80px;text-align:center;}
.page.active{display:block;}
.members{display:flex;justify-content:center;gap:40px;padding:60px;flex-wrap:wrap;}
.card{background:white;width:250px;padding:25px;border-radius:25px;box-shadow:0 15px 30px rgba(255,182,193,0.4);cursor:pointer;transition:0.4s;text-align:center;}
.card:hover{transform:translateY(-10px) scale(1.05);box-shadow:0 0 25px #ff69b4;}
.popup{display:none;position:fixed;top:50%;left:50%;transform:translate(-50%,-50%);background:white;padding:30px;border-radius:20px;box-shadow:0 20px 40px rgba(255,105,180,0.6);z-index:10000;}
.popup button{margin-top:15px;padding:8px 20px;border:none;background:hotpink;color:white;border-radius:20px;cursor:pointer;}
#fandom{font-size:40px;margin-top:20px;opacity:0;display:inline-block;animation: fandomGlow 1s infinite alternate; color:#ff69b4; text-shadow:0 0 25px #ffb6c1;}
@keyframes fandomGlow{0%{text-shadow:0 0 15px #ff69b4;}100%{text-shadow:0 0 35px #ff1493;}}
#countdown{font-size:35px;margin:30px 0;color:#ff1493;text-shadow:0 0 15px #ffb6c1;position:relative;}
.lightstick{width:80px;height:200px;margin:20px auto;background:linear-gradient(to top,#ff69b4,#ffe4ec);border-radius:20px;box-shadow:0 0 25px #ff69b4;position:relative;animation:lightstickPop 1s ease-out;}
.lightstick::after{content:'💖';position:absolute;top:-30px;left:50%;transform:translateX(-50%);font-size:40px;animation:glowPulse 1.5s infinite alternate;}
@keyframes glowPulse{0%{text-shadow:0 0 10px #ff69b4;}100%{text-shadow:0 0 25px #ff1493;}}
@keyframes lightstickPop{0%{transform:scale(0);}100%{transform:scale(1);}}
#song-container{width:90%;margin:0 auto 60px auto;background: linear-gradient(to bottom, #fff0f5, #ffe4ec);padding:20px;border-radius:25px;box-shadow:0 10px 20px rgba(255,182,193,0.4);position:relative;height:300px;overflow:hidden;}
.lyrics-line{font-size:22px;color:#ff1493;text-shadow:0 0 10px #ff69b4;margin:10px 0;opacity:0;animation:lyricsFade 1s forwards;}
@keyframes lyricsFade{0%{opacity:0; transform:translateY(20px);}100%{opacity:1; transform:translateY(0);}}
.swirl,.heart{position:fixed;width:50px;height:50px;border-radius:50%;opacity:0.5;animation:floatMove 15s linear infinite;}
.swirl{border:2px solid #ff69b4;}
.heart::after{content:"💖";font-size:50px;}
@keyframes floatMove{0%{transform:translateY(0) rotate(0deg);}50%{transform:translateY(-600px) rotate(180deg);}100%{transform:translateY(0) rotate(360deg);}}
@keyframes fadeIn{0%{opacity:0;}100%{opacity:1;}}
.glitter-burst{position:absolute;width:15px;height:15px;border-radius:50%;background:hotpink;animation:burstMove 1.5s ease-out forwards;pointer-events:none;}
@keyframes burstMove{0%{transform:translate(0,0) scale(0.5);opacity:1;}100%{transform:translate(var(--x),var(--y)) scale(1.5);opacity:0;}}
.quiz-section{margin:20px auto;max-width:600px;background:white;padding:20px;border-radius:20px;box-shadow:0 10px 20px rgba(255,182,193,0.4);}
.quiz-section h3{color:#ff69b4;}
.badge{font-size:30px;margin-top:10px;opacity:0;transition:1s;}
.badge.show{opacity:1; animation: badgePop 1s;}
@keyframes badgePop{0%{transform:scale(0.5);opacity:0;}100%{transform:scale(1.2);opacity:1;}}
.merch-item{display:inline-block;margin:20px;padding:15px;background:white;border-radius:20px;box-shadow:0 10px 20px rgba(255,182,193,0.4);cursor:pointer;transition:0.3s;}
.merch-item:hover{transform:scale(1.1);box-shadow:0 0 25px #ff69b4;}
.collection-item{display:inline-block;margin:10px;font-size:30px;}
#coinDisplay{position:fixed;top:15px;right:20px;font-size:25px;color:#ff1493;text-shadow:0 0 10px #ff69b4;z-index:1001;}
</style>
</head>
<body>

<div id="coinDisplay">Coins: 0</div>

<nav>
<a onclick="showPage('pageName')">Enter Name</a>
<a onclick="showPage('page1')">Home</a>
<a onclick="showPage('page2')">Fandom</a>
<a onclick="showPage('page3')">Members</a>
<a onclick="showPage('page4')">Countdown</a>
<a onclick="showPage('page5')">No Limits</a>
<a onclick="showPage('page6')">Quizzes</a>
<a onclick="showPage('page7')">Fanboard</a>
<a onclick="showPage('page8')">Games</a>
<a onclick="showPage('page9')">Merch</a>
<a onclick="showPage('page10')">Leaderboard</a>
</nav>

<!-- PAGE 0: Name Entry -->
<div class="page" id="pageName">
<h2>Enter Your Name</h2>
<input type="text" id="playerName" placeholder="Your fan nickname"><br>
<button onclick="registerName()">Submit</button>
<p id="nameConfirm"></p>
</div>

<!-- PAGE 1: Home -->
<div class="page active" id="page1">
<h1>K-HEARTS</h1>
<p>Three Hearts. One Spark.</p>
<div class="lightstick"></div>
</div>

<!-- PAGE 2: Fandom -->
<div class="page" id="page2">
<h2>Fandom Reveal</h2>
<button onclick="revealFandom()">Click to Reveal KAES</button>
<div id="fandom">✨KAES✨</div>
</div>

<!-- PAGE 3: Members -->
<div class="page" id="page3">
<h2>Meet K-HEARTS</h2>
<section class="members">
<div class="card" onclick="openPopup('Karlyn: Leader, Main Rapper, Lead Dancer, Sub Vocalist')">Karlyn</div>
<div class="card" onclick="openPopup('Alyssa: Visual, Main Vocalist, Sub Rapper')">Alyssa</div>
<div class="card" onclick="openPopup('Trixie: Main Dancer, Lead Rapper, Sub Vocalist')">Trixie</div>
</section>
</div>

<!-- PAGE 4: Countdown -->
<div class="page" id="page4">
<h2>Debut Countdown</h2>
<div id="countdown"></div>
</div>

<!-- PAGE 5: No Limits -->
<div class="page" id="page5">
<h2>First Song: No Limits</h2>
<div id="song-container"></div>
</div>

<!-- PAGE 6: Quizzes -->
<div class="page" id="page6">
<h2>K-HEARTS Member Quiz</h2>
<!-- Quizzes same as before -->
</div>

<!-- PAGE 7: Fanboard -->
<div class="page" id="page7">
<h2>Fanboard</h2>
<form id="fanForm">
<label>Leave a message: </label><br>
<input type="text" id="fanMessage" placeholder="always stay strong! khearts coming soon!"><br>
<button type="button" onclick="submitFanMessage()">Submit</button>
</form>
<div id="fanMessages" style="margin-top:20px;"></div>
</div>

<!-- PAGE 8: Games -->
<div class="page" id="page8">
<h2>Mini Games</h2>
<p>Catch the flying hearts! Click to earn coins.</p>
<div id="gameArea" style="position:relative;height:300px;background:linear-gradient(to top,#ffe4ec,#fff0f5);border-radius:20px;overflow:hidden;"></div>
<p>Score: <span id="gameScore">0</span></p>
<button onclick="changeLightstick()">Change Lightstick Color 💖</button>
<div class="lightstick" id="gameLightstick"></div>
</div>

<!-- PAGE 9: Merch -->
<div class="page" id="page9">
<h2>Virtual Merch Store</h2>
<div id="merchStore">
<div class="merch-item" onclick="buyMerch('☁️',10)">Karlyn Badge ☁️ - 10 coins</div>
<div class="merch-item" onclick="buyMerch('🎀',10)">Alyssa Ribbon 🎀 - 10 coins</div>
<div class="merch-item" onclick="buyMerch('🥟',10)">Trixie Dumpling 🥟 - 10 coins</div>
<div class="merch-item" onclick="buyMerch('💿✨',20)">Animated CD 💿✨ - 20 coins</div>
</div>
<h3>My Collection:</h3>
<div id="collection"></div>
</div>

<!-- PAGE 10: Leaderboard -->
<div class="page" id="page10">
<h2>Top KAES Fans</h2>
<div id="leaderboard"></div>
</div>

<!-- FLOATING HEARTS & SWIRLS -->
<div class="swirl" style="left:10%; animation-delay:0s;"></div>
<div class="swirl" style="left:30%; animation-delay:2s;"></div>
<div class="swirl" style="left:50%; animation-delay:4s;"></div>
<div class="heart" style="left:20%; animation-delay:1s;"></div>
<div class="heart" style="left:75%; animation-delay:3s;"></div>

<script>
/* ===== VARIABLES ===== */
let coins=0;
let playerName="";
let leaderboard=[];

/* ===== PAGE NAVIGATION ===== */
function showPage(id){
  const pages=document.querySelectorAll('.page');
  pages.forEach(p=>p.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

/* ===== REGISTER NAME ===== */
function registerName(){
  const nameInput=document.getElementById("playerName").value.trim();
  if(nameInput){
    playerName=nameInput;
    document.getElementById("nameConfirm").innerText="Welcome, "+playerName+"!";
    if(!leaderboard.some(l=>l.name===playerName)) leaderboard.push({name:playerName,coins:coins,collection:[]});
    document.getElementById("coinDisplay").innerText="Coins: "+coins;
  }
}

/* ===== UPDATE LEADERBOARD ===== */
function updateLeaderboard(){
  leaderboard.sort((a,b)=>b.coins-a.coins);
  const lb=document.getElementById("leaderboard");
  lb.innerHTML="";
  leaderboard.forEach((p,i)=>{
    let div=document.createElement("div");
    div.innerText=`${i+1}. ${p.name} - ${p.coins} coins - ${p.collection.join(" ")}`;
    lb.appendChild(div);
  });
}

/* ===== COINS + COLLECTION ===== */
function addCoins(n){
  if(playerName==="") return alert("Enter your name first!");
  coins+=n;
  document.getElementById("coinDisplay").innerText="Coins: "+coins;
  leaderboard.find(l=>l.name===playerName).coins=coins;
  updateLeaderboard();
}

function buyMerch(item,cost){
  if(playerName==="") return alert("Enter your name first!");
  if(coins>=cost){
    coins-=cost;
    document.getElementById("coinDisplay").innerText="Coins: "+coins;
    const player=leaderboard.find(l=>l.name===playerName);
    player.coins=coins;
    player.collection.push(item);
    const colDiv=document.getElementById("collection");
    const span=document.createElement("span");
    span.className="collection-item";
    span.innerText=item;
    colDiv.appendChild(span);
    updateLeaderboard();
    alert("You got "+item+"!");
  }else{
    alert("Not enough coins!");
  }
}

/* ===== MINI GAMES ===== */
let gameScore=0;
function spawnHeart(){
  const heart=document.createElement("div");
  heart.className="heart";
  heart.style.left=Math.random()*280+"px";
  heart.style.top="300px";
  heart.style.fontSize=(20+Math.random()*30)+"px";
  heart.onclick=function(){
    gameScore+=1;
    addCoins(1);
    document.getElementById("gameScore").innerText=gameScore;
    heart.remove();
  }
  document.getElementById("gameArea").appendChild(heart);
  setTimeout(()=>heart.remove(),4000);
}
setInterval(spawnHeart,1000);

function changeLightstick(){
  const colors=["#ff69b4","#ff1493","#ffb6c1","#ff8da1"];
  const stick=document.getElementById("gameLightstick");
  stick.style.background=colors[Math.floor(Math.random()*colors.length)];
}

/* ===== FANBOARD ===== */
function submitFanMessage(){
  const msg=document.getElementById("fanMessage").value;
  if(msg){
    const div=document.createElement("div");
    div.innerText=msg;
    div.style.margin="10px";
    div.style.padding="10px";
    div.style.background="linear-gradient(to right,#ffe4ec,#fff0f5)";
    div.style.borderRadius="15px";
    div.style.boxShadow="0 5px 15px rgba(255,182,193,0.4)";
    document.getElementById("fanMessages").appendChild(div);
    document.getElementById("fanMessage").value="";
  }
}

/* ===== FANDOM REVEAL ===== */
function revealFandom(){
  const fandom=document.getElementById("fandom");
  fandom.style.opacity="1";
  for(let i=0;i<25;i++){
    const glitter=document.createElement("div");
    glitter.className="glitter-burst";
    glitter.style.setProperty('--x',(Math.random()*600-300)+'px');
    glitter.style.setProperty('--y',(Math.random()*600-300)+'px');
    glitter.style.left=(fandom.offsetLeft+fandom.offsetWidth/2)+'px';
    glitter.style.top=(fandom.offsetTop+fandom.offsetHeight/2)+'px';
    document.body.appendChild(glitter);
    setTimeout(()=>glitter.remove(),1500);
  }
}

/* ===== POPUP ===== */
function openPopup(text){
  document.getElementById("popupText").innerText=text;
  document.getElementById("popup").style.display="block";
}
function closePopup(){document.getElementById("popup").style.display="none";}

/* ===== COUNTDOWN ===== */
var countDownDate=new Date();
countDownDate.setDate(countDownDate.getDate()+30);
setInterval(function(){
  var now=new Date().getTime();
  var distance=countDownDate-now;
  var days=Math.floor(distance/(1000*60*60*24));
  var hours=Math.floor((distance%(1000*60*60*24))/(1000*60*60));
  var minutes=Math.floor((distance%(1000*60*60))/(1000*60));
  var seconds=Math.floor((distance%(1000
