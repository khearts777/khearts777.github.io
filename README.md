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
  height:150px;
}

.accessory{
  position:absolute;
  left:50%;
  transform:translateX(-50%);
}

#hat{top:0;font-size:40px;}
#collar{top:70px;font-size:30px;}
#toy{top:90px;font-size:40px;}

.chat-box{
  height:200px;
  overflow:auto;
  border:2px solid pink;
  background:white;
  padding:10px;
}

input{
  padding:8px;
  border-radius:10px;
  border:1px solid pink;
}

.leaderboard{
  background:white;
  border-radius:15px;
  padding:10px;
  width:200px;
  margin:auto;
}
</style>
</head>

<body>

<h1>💖 K-HEARTS WORLD 💖</h1>

<div id="nameSection">
  <h3>Enter your name:</h3>
  <input id="usernameInput">
  <button onclick="startGame()">Enter</button>
</div>

<div id="main" style="display:none;">

<p>Coins: <span id="coins">100</span> 💰</p>

<button onclick="showSection('home')">Home</button>
<button onclick="showSection('members')">Members</button>
<button onclick="showSection('pets')">Pets</button>
<button onclick="showSection('games')">Games</button>
<button onclick="showSection('chat')">AI Chat</button>
<button onclick="showSection('leaderboard')">Leaderboard</button>
<button onclick="showSection('lyrics')">Lyrics</button>

<!-- HOME -->
<div id="home" class="section active">
  <h2>Welcome <span id="playerName"></span> 💕</h2>
  <p>Fandom Name: 💎 Starhearts 💎</p>
  <p>Complete games, dress pets, and chat with idols!</p>
</div>

<!-- MEMBERS -->
<div id="members" class="section">
<h2>Members</h2>
<p><b>Karlyn</b> – Leader, Main Rapper, Lead Dancer, Sub Vocalist</p>
<p><b>Trixie</b> – Centre, Sub Rapper, Main Dancer, Sub Vocalist</p>
<p><b>Hayley</b> – Lead Dancer, Lead Vocalist, Maknae (Likes black + Stray Kids)</p>
<p><b>Alyssa</b> – Main Vocalist, Visual, Sub Rapper, Sub Dancer</p>
</div>

<!-- PETS -->
<div id="pets" class="section">
<h2>Choose Pet</h2>
<button onclick="setPet('🐶')">Dog</button>
<button onclick="setPet('🐱')">Cat</button>
<button onclick="setPet('🐧')">Penguin</button>

<div class="pet-area">
  <div id="pet">🐶</div>
  <div id="hat" class="accessory"></div>
  <div id="collar" class="accessory"></div>
  <div id="toy" class="accessory"></div>
</div>

<h3>Shop</h3>
<button onclick="buyItem('hat','🎀',20)">Buy Bow Hat (20)</button>
<button onclick="buyItem('collar','💎',15)">Buy Diamond Collar (15)</button>
<button onclick="buyItem('toy','⚽',10)">Buy Ball (10)</button>

<button onclick="playToy()">Play With Toy</button>
</div>

<!-- GAMES -->
<div id="games" class="section">
<h2>Games</h2>
<button onclick="tapGame()">Tap Heart</button>
<button onclick="spinWheel()">Spin Wheel</button>
<button onclick="mathGame()">Homework Game</button>
<p id="gameResult"></p>
</div>

<!-- CHAT -->
<div id="chat" class="section">
<h2>K-Hearts AI</h2>
<div class="chat-box" id="chatBox"></div>
<input id="chatInput">
<button onclick="sendChat()">Send</button>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="section">
<h2>Leaderboard</h2>
<div class="leaderboard">
<p id="leaderboardList"></p>
</div>
</div>

<!-- LYRICS -->
<div id="lyrics" class="section">
<h2>No Limits</h2>
<p>We rise up higher, no limits in sight,<br>
Shining together, we light up the night,<br>
Step by step, we own this stage,<br>
K-Hearts power, we’re setting the page 💖</p>
</div>

</div>

<script>

let coins=100;
let username="";
let responses=[
"Hey queen 💖",
"You got this!",
"Need homework help?",
"That’s iconic.",
"I’m proud of you.",
"Slayyy.",
"Let’s win coins!"
];

function startGame(){
 username=document.getElementById("usernameInput").value;
 if(username==="") return;
 document.getElementById("playerName").innerText=username;
 document.getElementById("nameSection").style.display="none";
 document.getElementById("main").style.display="block";
 updateLeaderboard();
}

function showSection(id){
 document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
 document.getElementById(id).classList.add("active");
}

function updateCoins(){
 document.getElementById("coins").innerText=coins;
 updateLeaderboard();
}

function setPet(p){
 document.getElementById("pet").innerText=p;
}

function buyItem(type,emoji,price){
 if(coins>=price){
   coins-=price;
   document.getElementById(type).innerText=emoji;
   updateCoins();
 }
}

function playToy(){
 let toy=document.getElementById("toy");
 if(toy.innerText!==""){
   toy.style.top="70px";
   setTimeout(()=>toy.style.top="90px",300);
 }
}

function tapGame(){
 coins+=5;
 document.getElementById("gameResult").innerText="You earned 5 coins!";
 updateCoins();
}

function spinWheel(){
 let win=Math.floor(Math.random()*20)+1;
 coins+=win;
 document.getElementById("gameResult").innerText="You won "+win+" coins!";
 updateCoins();
}

function mathGame(){
 let answer=prompt("What is 6 x 7?");
 if(answer=="42"){
   coins+=20;
   alert("Correct! +20 coins");
   updateCoins();
 }
}

function sendChat(){
 let input=document.getElementById("chatInput").value;
 if(input==="") return;
 let box=document.getElementById("chatBox");
 box.innerHTML+="<p><b>"+username+":</b> "+input+"</p>";
 let reply=responses[Math.floor(Math.random()*responses.length)];
 box.innerHTML+="<p><b>K-Hearts:</b> "+reply+"</p>";
 box.scrollTop=box.scrollHeight;
 document.getElementById("chatInput").value="";
}

function updateLeaderboard(){
 document.getElementById("leaderboardList").innerHTML=
 username+" — "+coins+" coins";
}

</script>

</body>
</html>
