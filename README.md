<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>K-Hearts World</title>

<style>
body{
  margin:0;
  font-family: "Comic Sans MS", cursive;
  background: linear-gradient(#ffd6ec,#ffc0e6);
  text-align:center;
}
h1{color:#ff1493;}

button{
  background:#ff69b4;
  border:none;
  padding:10px 18px;
  border-radius:20px;
  margin:5px;
  color:white;
  cursor:pointer;
}
button:hover{background:#ff1493;}

.section{display:none;padding:20px;}
.active{display:block;}

.pet-area{
  font-size:80px;
  position:relative;
  height:160px;
}
.layer{
  position:absolute;
  left:50%;
  transform:translateX(-50%);
}
#hat{top:0;font-size:40px;}
#collar{top:75px;font-size:30px;}
#toy{top:100px;font-size:40px;}

.chat-box{
  height:200px;
  overflow:auto;
  border:2px solid pink;
  background:white;
  padding:10px;
  text-align:left;
}

input{
  padding:8px;
  border-radius:10px;
  border:1px solid pink;
}

.card{
  background:white;
  border-radius:15px;
  padding:10px;
  margin:10px auto;
  width:300px;
}
</style>
</head>

<body>

<h1>💖 K-HEARTS WORLD 💖</h1>

<div id="login">
  <h3>Enter your Kaes name:</h3>
  <input id="nameInput">
  <button onclick="start()">Enter</button>
</div>

<div id="main" style="display:none;">

<p>Fandom: 💖 Kaes 💖</p>
<p>Coins: <span id="coins">100</span> 💰</p>
<p>Pet Happiness: <span id="happy">70</span> 💕</p>
<p>Pet Health: <span id="health">100</span> ❤️</p>
<button onclick="feed()">Feed (-5 coins)</button>

<button onclick="show('home')">Home</button>
<button onclick="show('members')">Members</button>
<button onclick="show('pets')">Pets</button>
<button onclick="show('games')">Games</button>
<button onclick="show('chat')">AI Chat</button>
<button onclick="show('leaderboard')">Leaderboard</button>
<button onclick="show('lyrics')">Lyrics</button>

<!-- HOME -->
<div id="home" class="section active">
  <h2>Welcome <span id="player"></span> 💕</h2>
  <p>Future global queens 👑</p>
</div>

<!-- MEMBERS -->
<div id="members" class="section">
<h2>Members</h2>

<div class="card"><b>Karlyn</b><br>Leader, Main Rapper, Lead Dancer</div>
<div class="card"><b>Trixie</b><br>Centre, Main Dancer</div>
<div class="card"><b>Hayley</b><br>Lead Vocalist, Maknae</div>
<div class="card"><b>Alyssa</b><br>Main Vocalist, Visual</div>

</div>

<!-- PETS -->
<div id="pets" class="section">
<h2>Your Pet</h2>

<button onclick="choosePet('🐶')">Dog</button>
<button onclick="choosePet('🐱')">Cat</button>
<button onclick="choosePet('🐧')">Penguin</button>

<div class="pet-area">
  <div id="pet">🐶</div>
  <div id="hat" class="layer"></div>
  <div id="collar" class="layer"></div>
  <div id="toy" class="layer"></div>
</div>

<h3>Shop</h3>
<button onclick="buy('hat','🎀',20)">Bow (20)</button>
<button onclick="buy('hat','👑',30)">Crown (30)</button>
<button onclick="buy('hat','🧢',20)">Cap (20)</button>
<button onclick="buy('collar','💎',15)">Diamond (15)</button>
<button onclick="buy('collar','🌸',15)">Flower (15)</button>
<button onclick="buy('toy','⚽',10)">Ball (10)</button>
<button onclick="buy('toy','🧸',15)">Teddy (15)</button>
<button onclick="buy('toy','🦴',10)">Bone (10)</button>

<br>
<button onclick="play()">Play (+5 coins)</button>
<button onclick="bathe()">Bathe 🛁</button>

</div>

<!-- GAMES -->
<div id="games" class="section">
<h2>Games</h2>
<button onclick="tap()">Tap (+5)</button>
<button onclick="spin()">Spin</button>
<button onclick="math()">Multiply Quiz</button>
<button onclick="addition()">Addition Quiz</button>
<button onclick="spelling()">Spelling Quiz</button>
<button onclick="logic()">Logic Quiz</button>
<button onclick="science()">Science Quiz</button>
<p id="gameMsg"></p>
</div>

<!-- CHAT -->
<div id="chat" class="section">
<h2>K-Hearts AI</h2>
<div class="chat-box" id="chatBox"></div>
<input id="chatInput">
<button onclick="send()">Send</button>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="section">
<h2>Leaderboard</h2>
<div id="board"></div>
</div>

<!-- LYRICS -->
<No limits
No pressure
No ceiling
We go up

Walk in like a headline, cameras all flash
Step so sharp, make the whole world crash
Different languages, same ambition
Born to win — that’s the only mission

Mirror mirror, we don’t compete
We break the glass in designer feet
No permission, we elevate
Watch how legends are made

We don’t bend, we don’t break
Pressure turns to diamonds in our wake
Every scar is a shining mark
Strike a match — ignite the dark

We go higher, higher
Touch the sky, no ceiling
Fearless fire, fire
Got the whole world feeling

No doubts, no fear
We came too far to disappear
Global girls, we redefine
Step aside — the crown is mine

Runway rebel, spotlight glow
Soft but savage, let them know
From every city we ignite
Day one queens, built for the fight

Whispers turning into cheers
We turned pain into premiere
Every stage, every scene
We don’t follow — we lead

Too real, too bold
Too young, too gold
They said slow down — we said watch this
Turn small talk into a hit list

Confidence loud, no apologies
Breaking rules is our policy
Future written in neon light
We don’t knock — we own the night

If they doubt us, let them talk
We don’t walk — we skywalk
Every fall just fuels the flame
Say our names — remember the game

We go higher, higher
World on our shoulders shining
Fearless fire, fire
Perfect timing

No glass left to break
No crown left to take
We don’t stop, we redefine
No ceiling — we climb.>

</div>

<script>

let coins=100;
let happiness=70;
let health=100;
let username="";
let responses=[
let generalResponses = [
"That’s interesting — tell me more.",
"Let’s break that down step by step.",
"I like how you’re thinking.",
"Can you show me what you’ve tried so far?",
"That’s a good start.",
"Let’s reason through it logically.",
"What subject is this for?",
"Try identifying the key information first.",
"You’re closer than you think.",
"Let’s simplify the problem.",
"What’s the main concept being tested?",
"Think about the formula you might need.",
"Explain your reasoning to me.",
"Let’s tackle this together.",
"You’ve got this 💖",
"That’s creative!",
"Pause — what is the question REALLY asking?",
"Look for patterns.",
"Check your units.",
"What do you already know?"
];
  

function start(){
 username=document.getElementById("nameInput").value;
 if(username==="") return;
 document.getElementById("player").innerText=username;
 document.getElementById("login").style.display="none";
 document.getElementById("main").style.display="block";
 updateStats();
 setInterval(dropHealth,30000);
}

function show(id){
 document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
 document.getElementById(id).classList.add("active");
}

function updateStats(){
 document.getElementById("coins").innerText=coins;
 document.getElementById("happy").innerText=happiness;
 document.getElementById("health").innerText=health;
 document.getElementById("board").innerHTML=username+" — "+coins+" coins";
}

function choosePet(p){document.getElementById("pet").innerText=p;}

function buy(type,emoji,price){
 if(coins>=price){
  coins-=price;
  document.getElementById(type).innerText=emoji;
  updateStats();
 }
}

function play(){coins+=5; happiness+=5; updateStats();}
function bathe(){happiness+=10; health+=5; if(health>100)health=100; updateStats();}
function feed(){if(coins>=5){coins-=5; health+=15; if(health>100)health=100;} updateStats();}
function dropHealth(){health-=5; if(health<0)health=0; updateStats();}

function tap(){coins+=5; updateStats();}
function spin(){let w=Math.floor(Math.random()*30)+1; coins+=w; updateStats();}

function math(){let a=6,b=8; let ans=prompt("6 x 8 = ?"); if(ans=="48"){coins+=20;} updateStats();}
function addition(){let ans=prompt("45 + 37 = ?"); if(ans=="82"){coins+=15;} updateStats();}
function spelling(){let ans=prompt("Spell: ambition"); if(ans&&ans.toLowerCase()=="ambition"){coins+=20;} updateStats();}
function logic(){let ans=prompt("3 apples, take 2. How many do YOU have?"); if(ans=="2"){coins+=25;} updateStats();}
function science(){let ans=prompt("Planet we live on?"); if(ans&&ans.toLowerCase()=="earth"){coins+=20;} updateStats();}

function send(){
 function send(){
 let input=document.getElementById("chatInput").value;
 if(input==="") return;

 let box=document.getElementById("chatBox");
 box.innerHTML+="<p><b>"+username+":</b> "+input+"</p>";

 let reply="";
 let text=input.toLowerCase();

 // MATH HELP
 if(text.includes("math") || text.includes("x") || text.includes("+") || text.includes("-") || text.includes("÷")){
   reply="Okay let’s solve this step by step. What numbers are we working with?";
 }

 // SCIENCE HELP
 else if(text.includes("science") || text.includes("planet") || text.includes("energy")){
   reply="Science question detected 🧪 What topic specifically?";
 }

 // ENGLISH HELP
 else if(text.includes("essay") || text.includes("composition") || text.includes("write")){
   reply="Let’s plan your structure first: introduction, 3 points, conclusion. What’s your topic?";
 }

 // FEELINGS
 else if(text.includes("sad") || text.includes("tired") || text.includes("stress")){
   reply="I’m here for you 💕 What’s going on?";
 }

 // MOTIVATION
 else if(text.includes("give up") || text.includes("hard")){
   reply="Hard doesn’t mean impossible. You’ve handled tougher things before.";
 }

 // QUESTIONS
 else if(text.includes("?")){
   reply="Great question. Let’s think about it logically.";
 }

 // DEFAULT RANDOM
 else{
   reply = generalResponses[Math.floor(Math.random()*generalResponses.length)];
 }

 box.innerHTML+="<p><b>K-Hearts AI:</b> "+reply+"</p>";
 box.scrollTop=box.scrollHeight;
 document.getElementById("chatInput").value="";
}
}

</script>

</body>
</html>
