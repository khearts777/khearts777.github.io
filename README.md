<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>K-Hearts Official Fan Universe</title>
<style>
body{margin:0;font-family:Arial;background:linear-gradient(120deg,#ffc0cb,#ffe6f0);color:black;text-align:center;overflow-x:hidden;}
nav{background:#ff66b2;padding:15px;position:sticky;top:0;z-index:100;}
nav button{margin:5px;padding:8px 15px;background:#fff;color:#ff66b2;border:none;border-radius:20px;cursor:pointer;font-weight:bold;}
.page{display:none;padding:20px;}
.active{display:block;}
h1{font-size:40px;background:linear-gradient(45deg,#ff66b2,#fff);-webkit-background-clip:text;color:transparent;}
button{padding:10px 18px;margin:5px;border-radius:20px;border:none;cursor:pointer;background:#ff66b2;color:white;font-weight:bold;}
.choiceBtn{background:white;color:black;margin:3px;}
.shop-box{background:#ffddee;margin:10px auto;padding:15px;width:300px;border-radius:20px;}
.avatar-container{position:relative;width:150px;height:320px;margin:0 auto;}
#head{width:80px;height:80px;background:#fddac4;border-radius:50%;position:absolute;top:0;left:35px;z-index:5;}
#torso{width:80px;height:80px;background:pink;position:absolute;top:80px;left:35px;border-radius:10px;z-index:5;}
#bottom{width:80px;height:80px;background:white;position:absolute;top:160px;left:35px;border-radius:10px;z-index:5;}
#shoes{width:80px;height:20px;background:black;position:absolute;top:240px;left:35px;border-radius:5px;z-index:5;}
#handAccessory{position:absolute;top:160px;left:90px;font-size:30px;z-index:10;}
.levelBarOuter{width:80%;height:20px;background:#fff;margin:10px auto;border-radius:20px;}
.levelBarInner{height:100%;width:0%;background:#ff66b2;border-radius:20px;transition:0.5s;}
.heart{position:absolute;font-size:25px;animation:float 5s linear infinite;cursor:pointer;}
@keyframes float{from{transform:translateY(100vh);}to{transform:translateY(-10vh);}}
#chatBox{width:90%;max-width:500px;height:200px;background:#fff;border-radius:15px;margin:0 auto;overflow-y:auto;padding:10px;text-align:left;color:black;}
#chatInput{width:70%;padding:8px;border-radius:10px;border:1px solid #ff66b2;}
.member-card{background:#ffddee;border-radius:15px;margin:10px auto;padding:10px;width:250px;}
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
<button onclick="showPage('chat')">Fan Chat</button>
</nav>

<div id="coinsDisplay">Coins: 0</div>
<div id="levelDisplay">Level 1 — Rookie</div>
<div class="levelBarOuter"><div id="levelBar" class="levelBarInner"></div></div>

<!-- HOME -->
<div id="home" class="page active">
<h1>K-HEARTS</h1>
<p>Always stay strong! K-Hearts coming soon!</p>
<p>✨💖💗💕</p>
</div>

<!-- PROMPT USER NAME -->
<script>
let data=JSON.parse(localStorage.getItem("kheartsData"))||{coins:0,username:"",avatar:"🙂",outfit:"Basic",hasLightstick:false,leaderboard:[],badges:[]};
if(!data.username){data.username=prompt("Welcome KAES! Enter your name:");localStorage.setItem("kheartsData",JSON.stringify(data));}
</script>

<!-- GAMES -->
<div id="games" class="page">
<h2>💖 Click Heart Game</h2>
<button onclick="startHearts()">Start</button>
<div id="gameArea"></div>

<h2>☁️ Karlyn Quiz</h2><div id="quiz1"></div>
<h2>🎀 Alyssa Quiz</h2><div id="quiz2"></div>
<h2>🥟 Trixie Quiz</h2><div id="quiz3"></div>

<h2>🎯 Catch the Falling Heart</h2>
<button onclick="startCatchGame()">Start</button>
<div id="catchArea" style="position:relative;width:100%;height:200px;"></div>
</div>

<!-- AVATAR -->
<div id="avatar" class="page">
<h2>Fan Avatar</h2>
<div class="avatar-container">
<div id="head"></div>
<div id="torso"></div>
<div id="bottom"></div>
<div id="shoes"></div>
<div id="handAccessory"></div>
</div>
<p>Outfit: <span id="outfitDisplay">Basic</span></p>
</div>

<!-- SHOP -->
<div id="shop" class="page">
<h2>Avatar Outfit Shop</h2>
<div class="shop-box"><p>Pink Bow Outfit 🎀 (30 coins)</p><button onclick="buyOutfit('🎀 Coquette',30)">Buy</button></div>
<div class="shop-box"><p>Penguin Hoodie 🐧 (40 coins)</p><button onclick="buyOutfit('🐧 Penguin',40)">Buy</button></div>
<div class="shop-box"><p>Stage Queen Fit 👑 (60 coins)</p><button onclick="buyOutfit('👑 Queen',60)">Buy</button></div>
<div class="shop-box"><p>Phone 📱 (20 coins)</p><button onclick="buyOutfit('📱 Phone',20)">Buy</button></div>
<div class="shop-box"><p>Water Bottle 💧 (15 coins)</p><button onclick="buyOutfit('💧 Water',15)">Buy</button></div>
<div class="shop-box"><p>Official Pink Lightstick 💗 (Level 5)</p><button onclick="unlockLightstick()">Unlock</button></div>
</div>

<!-- MEMBERS -->
<div id="members" class="page">
<h2>K-Hearts Members</h2>
<div class="member-card">
<h3>Karlyn ☁️</h3>
<p>Leader • Main Rapper • Sub Vocal • 154cm • Loves Japanese food, penguins, Katseye fan</p>
</div>
<div class="member-card">
<h3>Alyssa 🎀</h3>
<p>Main Vocal • Sub Rapper • Visual • 150cm • Loves Pink, coquette style, collects cute items, loves IVE</p>
</div>
<div class="member-card">
<h3>Trixie 🥟</h3>
<p>Main Dancer • Lead Rapper • Sub Vocal • 153cm • Loves comfy outfits, Wushu pants, SKZ & NJZ fan</p>
</div>
</div>

<!-- FANDOM -->
<div id="fandom" class="page">
<h2>Fandom Name Reveal</h2>
<button onclick="revealFandom()">Reveal</button>
<h1 id="fandomName" style="display:none;color:#ff66b2;"></h1>
<p id="fandomDesc"></p>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="page">
<div id="leaderboardList"></div>
</div>

<!-- FAN CHAT -->
<div id="chat" class="page">
<h2>Fan Chat with K-Hearts</h2>
<div id="chatBox"></div>
<input id="chatInput" placeholder="Type a message...">
<button onclick="sendMessage()">Send</button>
</div>

<script>
/* DATA STORAGE */
function saveData(){localStorage.setItem("kheartsData",JSON.stringify(data));}

const titles=["Rookie","Trainee","Rising Star","Performer","Stage Slayer","Icon","Global Glow","Elite KAES","Legend","Ultimate KAES"];
let avatarPieces={head:"#fddac4",torso:"pink",bottom:"white",shoes:"black",accessory:""};

function updateDisplay(){
document.getElementById("coinsDisplay").innerText="Coins: "+data.coins;
let level=Math.floor(data.coins/50)+1; if(level>10)level=10;
document.getElementById("levelDisplay").innerText="Level "+level+" — "+titles[level-1];
document.getElementById("levelBar").style.width=((data.coins%50)*2)+"%";
document.getElementById("head").style.background=avatarPieces.head;
document.getElementById("torso").style.background=avatarPieces.torso;
document.getElementById("bottom").style.background=avatarPieces.bottom;
document.getElementById("shoes").style.background=avatarPieces.shoes;
document.getElementById("handAccessory").innerHTML=avatarPieces.accessory;
}
updateDisplay();

function showPage(id){document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));document.getElementById(id).classList.add("active");}

/* HEART GAME */
function startHearts(){let area=document.getElementById("gameArea");area.innerHTML="";
for(let i=0;i<10;i++){let heart=document.createElement("div");heart.innerText="💖";heart.className="heart";heart.style.left=Math.random()*90+"%";
heart.onclick=function(){data.coins+=5;updateDisplay();saveData();heart.remove();};
area.appendChild(heart);}}

/* CATCH GAME */
function startCatchGame(){let area=document.getElementById("catchArea");area.innerHTML="";
for(let i=0;i<10;i++){let h=document.createElement("div");h.innerText="💖";h.style.position="absolute";h.style.left=Math.random()*90+"%";h.style.top="0px";h.style.cursor="pointer";
h.onclick=function(){data.coins+=10;updateDisplay();saveData();h.remove();};
area.appendChild(h);let fall=setInterval(()=>{let top=parseInt(h.style.top);if(top>=180){h.remove();clearInterval(fall);}else{h.style.top=top+2+"px";}},20);}}

function createQuiz(container,q,answers,correct,badge){let div=document.getElementById(container);div.innerHTML="<p>"+q+"</p>";
answers.forEach((ans,i)=>{let btn=document.createElement("button");btn.innerText=ans;btn.className="choiceBtn";btn.onclick=function(){
if(i===correct){data.coins+=20;updateDisplay();data.badges.push(badge);saveData();div.innerHTML="Correct! Badge "+badge;}else{div.innerHTML="Wrong! Try again!";}};div.appendChild(btn);});}

createQuiz("quiz1","What is Karlyn's fav group?",["Katseye","Blackpink","IVE"],0,"☁️");
createQuiz("quiz2","What colour does Alyssa love?",["Blue","Pink","Purple"],1,"🎀");
createQuiz("quiz3","What does Trixie love wearing?",["Wushu pants","Jeans","Skirts"],0,"🥟");

/* OUTFITS */
function buyOutfit(name,cost){
if(data.coins>=cost){data.coins-=cost;data.outfit=name;
if(name=="🎀 Coquette"){avatarPieces.torso="pink";avatarPieces.bottom="white";avatarPieces.accessory="🎀";}
if(name=="🐧 Penguin"){avatarPieces.torso="#aee1f9";avatarPieces.bottom="#f0f0f0";avatarPieces.accessory="🐧";}
if(name=="👑 Queen"){avatarPieces.torso="gold";avatarPieces.bottom="black";avatarPieces.accessory="👑";}
if(name=="📱 Phone"){avatarPieces.accessory="📱";}
if(name=="💧 Water"){avatarPieces.accessory="💧";}
updateDisplay();saveData();}else{alert("Not enough coins!");}
}

/* LIGHTSTICK */
function unlockLightstick(){let level=Math.floor(data.coins/50)+1;
if(level>=5){data.hasLightstick=true;avatarPieces.accessory="💗";updateDisplay();saveData();alert("Pink Lightstick Unlocked!");}else{alert("Reach Level 5 to unlock!");}}

/* FANDOM */
function revealFandom(){document.getElementById("fandomName").style.display="block";document.getElementById("fandomName").innerText="KAES";document.getElementById("fandomDesc").innerText="KAES stands for K-Hearts Angels & Energy Squad. You are our power, our light, our forever."}

/* LEADERBOARD */
function updateLeaderboard(){let list=document.getElementById("leaderboardList");list.innerHTML="";
data.leaderboard.sort((a,b)=>b.coins-a.coins);
data.leaderboard.forEach(p=>{let div=document.createElement("div");div.innerText=p.username+" — "+p.coins+" coins — "+titles[Math.floor(p.coins/50)>9?9:Math.floor(p.coins/50)];list.appendChild(div);});}
updateLeaderboard();

/* FAN CHAT */
function sendMessage(){let input=document.getElementById("chatInput");let msg=input.value;if(!msg)return;
let chat=document.getElementById("chatBox");let userMsg=document.createElement("div");userMsg.innerText=data.username+": "+msg;chat.appendChild(userMsg);
let responses=["Keep shining KAES!","You're amazing!","K-Hearts loves you!","Great job!","how are u", "share this website with your friends!","hope you are feeling well!","believe in urself", "😛" "🫩","🥀","😭","😄", "okayyy" ,"niceee!" what r ur fav stuff? " what do u like to do?", "have a great day!" ];
let idolMsg=document.createElement("div");idolMsg.innerText="K-Hearts: "+responses[Math.floor(Math.random()*responses.length)];chat.appendChild(idolMsg);
chat.scrollTop=chat.scrollHeight;input.value="";}
</script>

</body>
</html>
