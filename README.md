<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>K-Hearts Official</title>

<style>
body{
margin:0;
font-family:Arial;
background:black;
color:white;
text-align:center;
overflow-x:hidden;
}

nav{
background:#111;
padding:15px;
position:sticky;
top:0;
}

nav button{
margin:5px;
padding:8px 15px;
background:pink;
color:black;
border:none;
border-radius:20px;
cursor:pointer;
}

.page{display:none;padding:20px;}
.active{display:block;}

h1{
font-size:40px;
background:linear-gradient(45deg,pink,white);
-webkit-background-clip:text;
color:transparent;
}

button{
padding:10px 18px;
margin:5px;
border-radius:20px;
border:none;
cursor:pointer;
background:pink;
color:black;
}

.choiceBtn{
background:white;
color:black;
}

.shop-box{
background:#222;
margin:10px auto;
padding:15px;
width:300px;
border-radius:20px;
}

.avatar{
font-size:80px;
margin:20px;
}

.heart{
position:absolute;
font-size:25px;
animation:float 5s linear infinite;
}

@keyframes float{
from{transform:translateY(100vh);}
to{transform:translateY(-10vh);}
}

.levelBarOuter{
width:80%;
height:20px;
background:#222;
margin:10px auto;
border-radius:20px;
}

.levelBarInner{
height:100%;
width:0%;
background:pink;
border-radius:20px;
transition:0.5s;
}
</style>
</head>

<body>

<nav>
<button onclick="showPage('home')">Home</button>
<button onclick="showPage('games')">Games</button>
<button onclick="showPage('avatar')">Avatar</button>
<button onclick="showPage('shop')">Shop</button>
<button onclick="showPage('members')">Members</button>
<button onclick="showPage('fandom')">Fandom</button>
<button onclick="showPage('leaderboard')">Leaderboard</button>
</nav>

<div id="coinsDisplay">Coins: 0</div>
<div id="levelDisplay">Level 1 — Rookie</div>

<div class="levelBarOuter">
<div id="levelBar" class="levelBarInner"></div>
</div>

<!-- HOME -->
<div id="home" class="page active">
<h1>K-HEARTS</h1>
<p>Always stay strong! K-Hearts coming soon!</p>
</div>

<!-- GAMES -->
<div id="games" class="page">

<h2>💖 Click Heart Game</h2>
<button onclick="startHearts()">Start</button>
<div id="gameArea"></div>

<h2>☁️ Karlyn Quiz</h2>
<div id="quiz1"></div>

<h2>🎀 Alyssa Quiz</h2>
<div id="quiz2"></div>

<h2>🥟 Trixie Quiz</h2>
<div id="quiz3"></div>

</div>

<!-- AVATAR -->
<div id="avatar" class="page">
<h2>Fan Avatar</h2>
<div class="avatar">🙂</div>
<p>Outfit: <span id="outfitDisplay">Basic</span></p>
<div id="lightstickDisplay" style="font-size:60px;"></div>
</div>

<!-- SHOP -->
<div id="shop" class="page">
<h2>Avatar Outfit Shop</h2>

<div class="shop-box">
<p>Pink Bow Outfit 🎀 (30 coins)</p>
<button onclick="buyOutfit('🎀 Coquette',30)">Buy</button>
</div>

<div class="shop-box">
<p>Penguin Hoodie 🐧 (40 coins)</p>
<button onclick="buyOutfit('🐧 Penguin',40)">Buy</button>
</div>

<div class="shop-box">
<p>Stage Queen Fit 👑 (60 coins)</p>
<button onclick="buyOutfit('👑 Queen',60)">Buy</button>
</div>

<div class="shop-box">
<p>Official Pink Lightstick 💗 (Level 5)</p>
<button onclick="unlockLightstick()">Unlock</button>
</div>

</div>

<!-- MEMBERS -->
<div id="members" class="page">
<h2>K-Hearts Members</h2>

<h3>Karlyn</h3>
<p>Leader • Main Rapper • Vision Queen ☁️</p>

<h3>Alyssa</h3>
<p>Main Vocal • Visual • Coquette Princess 🎀</p>

<h3>Trixie</h3>
<p>Main Dancer • Performance Queen • Variety Star 🥟</p>
</div>

<!-- FANDOM -->
<div id="fandom" class="page">
<h2>Fandom Name Reveal</h2>
<button onclick="revealFandom()">Reveal</button>
<h1 id="fandomName" style="display:none;color:pink;"></h1>
<p id="fandomDesc"></p>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="page">
<input id="username" placeholder="Your Name">
<button onclick="saveName()">Submit</button>
<div id="leaderboardList"></div>
</div>

<script>

let coins=0;
let avatarOutfit="Basic";
let leaderboard=[];
let hasLightstick=false;

let titles=[
"Rookie",
"Trainee",
"Rising Star",
"Performer",
"Stage Slayer",
"Icon",
"Global Glow",
"Elite KAES",
"Legend",
"Ultimate KAES"
];

function updateCoins(){
document.getElementById("coinsDisplay").innerText="Coins: "+coins;
updateLevel();
}

function updateLevel(){
let level=Math.floor(coins/50)+1;
if(level>10) level=10;

let progress=(coins%50)*2;
if(level==10) progress=100;

document.getElementById("levelDisplay").innerText=
"Level "+level+" — "+titles[level-1];

document.getElementById("levelBar").style.width=progress+"%";

if(level==10 && hasLightstick){
document.getElementById("lightstickDisplay").innerHTML=
"<span style='color:hotpink;text-shadow:0 0 30px pink,0 0 60px hotpink;'>🔆💗🔆</span>";
}
}

function showPage(id){
document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
document.getElementById(id).classList.add("active");
}

function startHearts(){
let area=document.getElementById("gameArea");
area.innerHTML="";
for(let i=0;i<10;i++){
let heart=document.createElement("div");
heart.innerText="💖";
heart.className="heart";
heart.style.left=Math.random()*90+"%";
heart.onclick=function(){
coins+=5;
updateCoins();
heart.remove();
}
area.appendChild(heart);
}
}

function createQuiz(container,question,answers,correct,badge){
let div=document.getElementById(container);
div.innerHTML="<p>"+question+"</p>";
answers.forEach((ans,i)=>{
let btn=document.createElement("button");
btn.innerText=ans;
btn.className="choiceBtn";
btn.onclick=function(){
if(i===correct){
coins+=20;
updateCoins();
div.innerHTML="Correct! Badge Unlocked "+badge;
}else{
div.innerHTML="Wrong! Try again!";
}
}
div.appendChild(btn);
});
}

createQuiz("quiz1",
"What is Karlyn's fav group?",
["Katseye","Blackpink","IVE"],
0,"☁️");

createQuiz("quiz2",
"What colour does Alyssa love?",
["Blue","Pink","Purple"],
1,"🎀");

createQuiz("quiz3",
"What does Trixie love wearing?",
["Wushu pants","Jeans","Skirts"],
0,"🥟");

function buyOutfit(name,cost){
if(coins>=cost){
coins-=cost;
avatarOutfit=name;
document.getElementById("outfitDisplay").innerText=name;
updateCoins();
}else{
alert("Not enough coins!");
}
}

function unlockLightstick(){
let level=Math.floor(coins/50)+1;
if(level>=5){
hasLightstick=true;
document.getElementById("lightstickDisplay").innerHTML=
"<span style='color:pink;text-shadow:0 0 20px hotpink,0 0 40px pink;'>🔆💗🔆</span>";
alert("Official Pink Lightstick Unlocked!");
}else{
alert("Reach Level 5 to unlock!");
}
}

function revealFandom(){
document.getElementById("fandomName").style.display="block";
document.getElementById("fandomName").innerText="KAES";
document.getElementById("fandomDesc").innerText=
"KAES stands for K-Hearts Angels & Energy Squad. You are our power, our light, our forever.";
}

function saveName(){
let name=document.getElementById("username").value;
let level=Math.floor(coins/50)+1;
if(level>10) level=10;

leaderboard.push({
name:name,
score:coins,
title:titles[level-1]
});

leaderboard.sort((a,b)=>b.score-a.score);

let list=document.getElementById("leaderboardList");
list.innerHTML="";
leaderboard.forEach(p=>{
let div=document.createElement("div");
div.innerText=
p.name+" — "+p.score+" coins — "+p.title;
list.appendChild(div);
});
}

updateCoins();

</script>

</body>
</html>
