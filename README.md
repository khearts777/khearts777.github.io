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
background:white;
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
animation:glow 2s infinite alternate;
}

@keyframes glow{
from{text-shadow:0 0 10px pink;}
to{text-shadow:0 0 25px white;}
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

button.big{
padding:15px 25px;
font-size:18px;
border-radius:25px;
background:pink;
color:black;
border:none;
cursor:pointer;
margin:10px;
}

input{
padding:8px;
border-radius:15px;
border:none;
text-align:center;
}

.badge{
font-size:40px;
margin:10px;
}

.shop-item{
background:#222;
margin:10px;
padding:15px;
border-radius:15px;
}

.leaderboard-box{
background:#111;
margin:10px auto;
padding:15px;
width:300px;
border-radius:20px;
}
</style>
</head>

<body>

<nav>
<button onclick="showPage('home')">Home</button>
<button onclick="showPage('games')">Games</button>
<button onclick="showPage('shop')">Merch</button>
<button onclick="showPage('collection')">Collection</button>
<button onclick="showPage('leaderboard')">Leaderboard</button>
<button onclick="showPage('lyrics')">No Limits</button>
<button onclick="showPage('fanboard')">Fanboard</button>
</nav>

<div id="coinsDisplay">Coins: 0</div>

<!-- HOME -->
<div id="home" class="page active">
<h1>K-HEARTS</h1>
<p>Always stay strong! K-Hearts coming soon!</p>
<h2 id="countdown"></h2>
</div>

<!-- GAMES -->
<div id="games" class="page">
<h2>Click The Hearts!</h2>
<button class="big" onclick="startGame()">Start Game</button>
<div id="gameArea"></div>

<h2>Member Quiz</h2>
<button onclick="quizKarlyn()">Karlyn Quiz</button>
<button onclick="quizAlyssa()">Alyssa Quiz</button>
<button onclick="quizTrixie()">Trixie Quiz</button>
<div id="quizResult"></div>
</div>

<!-- SHOP -->
<div id="shop" class="page">
<h2>Merch Exchange</h2>

<div class="shop-item">
<p>K-Hearts Emoji Pack ☁️🎀🥟</p>
<button onclick="buyItem('Emoji Pack',50)">50 Coins</button>
</div>

<div class="shop-item">
<p>Animated CD 💿</p>
<button onclick="buyItem('Animated CD',80)">80 Coins</button>
</div>

<div class="shop-item">
<p>Digital Lightstick ✨</p>
<button onclick="buyItem('Lightstick',100)">100 Coins</button>
</div>

</div>

<!-- COLLECTION -->
<div id="collection" class="page">
<h2>My Collection</h2>
<div id="myCollection"></div>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="page">
<h2>Enter Your Name</h2>
<input id="username" placeholder="Your name">
<button onclick="saveName()">Submit</button>

<div class="leaderboard-box">
<h3>Top Fans</h3>
<div id="leaderboardList"></div>
</div>
</div>

<!-- LYRICS -->
<div id="lyrics" class="page">
<h2>No Limits</h2>
<div id="lyricsBox"></div>
<button onclick="startLyrics()">Play Lyrics</button>
</div>

<!-- FANBOARD -->
<div id="fanboard" class="page">
<h2>Fan Messages</h2>
<input id="fanMsg" placeholder="Write your message">
<button onclick="addMessage()">Post</button>
<div id="messages"></div>
</div>

<script>
let coins=0;
let collection=[];
let username="";
let leaderboard=[];

function updateCoins(){
document.getElementById("coinsDisplay").innerText="Coins: "+coins;
}

function showPage(id){
document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
document.getElementById(id).classList.add("active");
}

function startGame(){
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

function buyItem(item,cost){
if(coins>=cost){
coins-=cost;
collection.push(item);
updateCoins();
updateCollection();
alert("You got "+item+"!");
}else{
alert("Not enough coins!");
}
}

function updateCollection(){
let box=document.getElementById("myCollection");
box.innerHTML="";
collection.forEach(i=>{
let div=document.createElement("div");
div.innerText=i;
box.appendChild(div);
});
}

function saveName(){
username=document.getElementById("username").value;
leaderboard.push({name:username,score:coins});
updateLeaderboard();
}

function updateLeaderboard(){
let list=document.getElementById("leaderboardList");
list.innerHTML="";
leaderboard.sort((a,b)=>b.score-a.score);
leaderboard.forEach(player=>{
let div=document.createElement("div");
div.innerText=player.name+" - "+player.score+" coins";
list.appendChild(div);
});
}

function quizKarlyn(){
let ans=prompt("What is Karlyn's fav colour?");
if(ans && ans.toLowerCase()=="white"){
document.getElementById("quizResult").innerHTML="Correct! ☁️ Badge Unlocked!";
}else{
alert("Wrong!");
}
}

function quizAlyssa(){
let ans=prompt("What colour does Alyssa love?");
if(ans && ans.toLowerCase()=="pink"){
document.getElementById("quizResult").innerHTML="Correct! 🎀 Badge Unlocked!";
}else{
alert("Wrong!");
}
}

function quizTrixie(){
let ans=prompt("What does Trixie love wearing?");
if(ans && ans.toLowerCase().includes("wushu")){
document.getElementById("quizResult").innerHTML="Correct! 🥟 Badge Unlocked!";
}else{
alert("Wrong!");
}
}

let lyrics=[
"No limits","No pressure","No ceiling","We go up",
"Walk in like a headline",
"Step so sharp, make the whole world crash",
"We don’t bend, we don’t break",
"We go higher, higher",
"No ceiling — we climb."
];

function startLyrics(){
let box=document.getElementById("lyricsBox");
box.innerHTML="";
let i=0;
let interval=setInterval(()=>{
if(i>=lyrics.length){clearInterval(interval);}
else{
let line=document.createElement("div");
line.innerText=lyrics[i];
line.style.animation="glow 1s alternate infinite";
box.appendChild(line);
i++;
}
},1000);
}

function addMessage(){
let msg=document.getElementById("fanMsg").value;
let div=document.createElement("div");
div.innerText=msg;
document.getElementById("messages").appendChild(div);
}

let countDownDate=new Date("Dec 31, 2026 00:00:00").getTime();
setInterval(function(){
let now=new Date().getTime();
let distance=countDownDate-now;
let days=Math.floor(distance/(1000*60*60*24));
document.getElementById("countdown").innerText="Debut in "+days+" days!";
},1000);

updateCoins();
</script>

</body>
</html>

<script>

let coins=0;
let avatarOutfit="Basic";
let leaderboard=[];

function updateCoins(){
document.getElementById("coinsDisplay").innerText="Coins: "+coins;
updateLevel();
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
heart.innerText="🩷
  ";
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

/* LEVEL SYSTEM */

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

function updateLevel(){
let level=Math.floor(coins/50)+1;
if(level>10) level=10;

let progress=(coins%50)*2;
if(level==10) progress=100;

document.getElementById("levelDisplay").innerText=
"Level "+level+" — "+titles[level-1];

document.getElementById("levelBar").style.width=progress+"%";
}

/* QUIZ SYSTEM */

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

/* OUTFIT SHOP */

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

/* LEADERBOARD */

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

all hearts reserved 
