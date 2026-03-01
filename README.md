<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>K-Hearts Fan Universe</title>
<link href="https://fonts.googleapis.com/css2?family=Bubblegum+Sans&display=swap" rel="stylesheet">
<style>
body {
  margin:0; padding:0;
  font-family:'Bubblegum Sans', cursive;
  background: linear-gradient(135deg, #ffe6f0, #ffd1ff);
  color:#000;
  transition: all 0.3s;
}
nav {
  display:flex; justify-content:center; flex-wrap:wrap; gap:5px;
  background:#ffb6c1; padding:5px;
}
nav button {
  padding:8px 15px; border:none; border-radius:10px;
  cursor:pointer; background:#fff0f5; font-weight:bold;
  transition:all 0.2s;
}
nav button:hover {transform:scale(1.1); background:#ff99cc;}
.page {display:none; padding:10px;}
h1,h2,h3 {text-align:center; color:#ff3399;}
.member-card {
  background:#ffe0f5; margin:5px; padding:8px;
  border-radius:12px; text-align:center;
  transition:0.3s; cursor:pointer;
}
.member-card:hover {transform:scale(1.05); box-shadow:0 0 15px #ff99cc;}
#petContainer {font-size:120px; text-align:center; margin:20px auto; transition:all 0.3s;}
#petHappiness {font-weight:bold; color:#ff3399;}
.itemBtn {margin:3px; padding:5px; border-radius:10px; cursor:pointer; background:#ffccf0; border:none; transition:0.2s;}
.itemBtn:hover {transform:scale(1.1); background:#ff99cc;}
#chatWindow {height:200px; overflow-y:auto; border:2px solid #ff99cc; padding:5px; border-radius:10px; background:#fff0f5;}
.chatBubble {background:#ffe6f0; margin:3px; padding:5px; border-radius:10px;}
#quizArea button {margin:3px; padding:5px; border-radius:10px; cursor:pointer; background:#ffccf0; border:none; transition:0.2s;}
#quizArea button:hover {transform:scale(1.1); background:#ff99cc;}
#coins,#badges {font-weight:bold; color:#ff3399;}
</style>
</head>
<body>

<nav>
<button onclick="showPage('home')">Home</button>
<button onclick="showPage('members')">Members</button>
<button onclick="showPage('pets')">Pets</button>
<button onclick="showPage('shop')">Shop</button>
<button onclick="showPage('quiz')">Quiz</button>
<button onclick="showPage('chat')">Chat</button>
<button onclick="showPage('leaderboard')">Leaderboard</button>
<button onclick="showPage('lyrics')">Lyrics</button>
</nav>

<!-- HOME PAGE -->
<div id="home" class="page" style="display:block;">
<h1>💖 Welcome to K-Hearts Fan Universe 💖</h1>
<p style="text-align:center;">Fandom Name Reveal: <span id="fandomReveal">???</span></p>
<button onclick="revealFandom()">Reveal KAES 🎀</button>
<p style="text-align:center;font-size:20px;color:#ff3399;">Always stay strong! K-Hearts coming soon!</p>
</div>

<!-- MEMBERS PAGE -->
<div id="members" class="page">
<h2>🌸 Meet the Members</h2>
<div id="memberList"></div>
</div>

<!-- PETS PAGE -->
<div id="pets" class="page">
<h2>🐾 Your Pet</h2>
<div id="petContainer">🐧</div>
<p>Happiness: <span id="petHappiness">50</span>/100 💖</p>
<button onclick="choosePet('🐧')">Choose Penguin 🐧</button>
<button onclick="choosePet('🐶')">Choose Dog 🐶</button>
<button onclick="choosePet('🐱')">Choose Cat 🐱</button>
<button onclick="petAction('play')">Play 🎾</button>
<button onclick="petAction('bathe')">Bathe 🛁</button>
</div>

<!-- SHOP PAGE -->
<div id="shop" class="page">
<h2>🛒 Pet Items Shop</h2>
<button class="itemBtn" onclick="buyItem('Toy Ball','toy','🎾',10)">Toy Ball - 10 Coins</button>
<button class="itemBtn" onclick="buyItem('Pet Hat','hat','🎀',15)">Pet Hat - 15 Coins</button>
<button class="itemBtn" onclick="buyItem('Pet Collar','collar','💖',20)">Pet Collar - 20 Coins</button>
</div>

<!-- QUIZ PAGE -->
<div id="quiz" class="page">
<h2>📝 Member Quiz</h2>
<div id="quizArea"></div>
<p>Coins: <span id="coins">0</span> | Badges: <span id="badges">None</span></p>
</div>

<!-- CHAT PAGE -->
<div id="chat" class="page">
<h2>💌 Chat with Idols</h2>
<div id="chatWindow"></div>
<input type="text" id="chatInput" placeholder="Say something...">
<button onclick="sendMessage()">Send</button>
</div>

<!-- LEADERBOARD PAGE -->
<div id="leaderboard" class="page">
<h2>🏆 Leaderboard</h2>
<div id="leaderboardList"></div>
</div>

<!-- LYRICS PAGE -->
<div id="lyrics" class="page">
<h2>🎵 No Limits Lyrics</h2>
<div style="height:250px; overflow-y:auto; border:2px solid #ff99cc; padding:5px; border-radius:10px;">
<p>No limits<br>No pressure<br>No ceiling<br>We go up</p>
<p>Walk in like a headline, cameras all flash<br>Step so sharp, make the whole world crash<br>Different languages, same ambition<br>Born to win — that’s the only mission</p>
<p>Mirror mirror, we don’t compete<br>We break the glass in designer feet<br>No permission, we elevate<br>Watch how legends are made</p>
<p>We don’t bend, we don’t break<br>Pressure turns to diamonds in our wake<br>Every scar is a shining mark<br>Strike a match — ignite the dark</p>
<p>We go higher, higher<br>Touch the sky, no ceiling<br>Fearless fire, fire<br>Got the whole world feeling</p>
<p>No doubts, no fear<br>We came too far to disappear<br>Global girls, we redefine<br>Step aside — the crown is mine</p>
</div>
</div>

<script>
// ==== DATA ====
if(!localStorage.getItem('kheartsData')){
localStorage.setItem('kheartsData',JSON.stringify({username:'',coins:0,badges:[],pet:'🐧',petHappiness:50,shopItems:[],chat:[]}));
}
let data=JSON.parse(localStorage.getItem('kheartsData'));

// ==== MEMBERS ====
const members=[
{name:'Karlyn',role:'Leader, Main Rapper, Lead Dancer, Sub Vocalist',pet:'🐧',fav:'White, Japanese food, Penguins, Popmarts (Crybabies)'},
{name:'Trixie',role:'Centre, Sub Rapper, Main Dancer, Sub Vocalist',pet:'🐱',fav:'Comfy clothes, SKZ & NJZ'},
{name:'Hayley',role:'Lead Dancer, Lead Vocalist, Maknae',pet:'🐶',fav:'Black, Stray Kids'},
{name:'Alyssa',role:'Main Vocalist, Visual, Sub Rapper & Sub Dancer',pet:'🐶',fav:'Pink, Coquette style, IVE'}
];

// ==== DISPLAY MEMBERS ====
function updateMembers(){
let list=document.getElementById('memberList'); list.innerHTML='';
members.forEach(m=>{
let div=document.createElement('div');
div.className='member-card';
div.innerHTML=`<h3>${m.name} ${m.pet}</h3><p>Role: ${m.role}</p><p>Favorites: ${m.fav}</p>`;
list.appendChild(div);
});
}

// ==== PAGE DISPLAY ====
function showPage(id){
document.querySelectorAll('.page').forEach(p=>p.style.display='none');
document.getElementById(id).style.display='block';
}

// ==== PET SYSTEM ====
function choosePet(pet){
data.pet=pet; data.petHappiness=50; saveData(); updateDisplay();
alert('You chose '+pet+'! Take good care of them!');
}
function petAction(action){
if(action==='play'){data.petHappiness=Math.min(100,data.petHappiness+10); alert('Your pet is happy! 💖'); data.coins+=5;}
if(action==='bathe'){data.petHappiness=Math.min(100,data.petHappiness+15); alert('Your pet is clean and happy! 🛁💖'); data.coins+=5;}
saveData(); updateDisplay();
}

// ==== SHOP ====
function buyItem(name,type,value,cost){
if(data.coins<cost){alert('Not enough coins!'); return;}
data.coins-=cost; data.shopItems.push(name);
alert(`Purchased ${name}!`);
saveData(); updateDisplay();
}

// ==== CHAT ====
function updateChatWindow(){
let win=document.getElementById('chatWindow'); win.innerHTML='';
data.chat.forEach(msg=>{let p=document.createElement('div'); p.className='chatBubble'; p.innerHTML=msg; win.appendChild(p);});
win.scrollTop=win.scrollHeight;
}
function sendMessage(){
let input=document.getElementById('chatInput');
if(input.value.trim()===''){return;}
let userMsg=`<b>${data.username || 'Fan'}:</b> ${input.value}`;
data.chat.push(userMsg);
let responses=[
`Karlyn waves at you! 💖`,`Trixie smiles! 🐱`,`Hayley cheers! 🐶`,`Alyssa claps! 🎀`,
`Your coins: ${data.coins}`,'Keep playing with your pet!','You are awesome 💖',
`Your badges: ${data.badges.join(',')||'None'}`,'Yay! Pet loves you! 🎾'
];
data.chat.push('<b>Idol:</b> '+responses[Math.floor(Math.random()*responses.length)]);
input.value=''; saveData(); updateChatWindow();
}

// ==== LEADERBOARD ====
if(!localStorage.getItem('kheartsLeaderboard')) localStorage.setItem('kheartsLeaderboard','[]');
function updateLeaderboard(){
let list=JSON.parse(localStorage.getItem('kheartsLeaderboard'));
let found=list.find(u=>u.name===data.username);
if(found){found.coins=data.coins;} else {list.push({name:data.username,coins:data.coins});}
list.sort((a,b)=>b.coins-a.coins);
localStorage.setItem('kheartsLeaderboard',JSON.stringify(list));
let lb=document.getElementById('leaderboardList'); lb.innerHTML='';
list.forEach((u,i)=>{let p=document.createElement('p'); p.innerText=(i+1)+". "+u.name+" — "+u.coins+" coins"; lb.appendChild(p);});
}

// ==== QUIZ ====
const quizQuestions=[
{question:"What is Karlyn's favorite color?",options:["White","Pink","Black"],answer:"White",member:"Karlyn"},
{question:"Which pet does Trixie have?",options:["Dog","Cat","Penguin"],answer:"Cat",member:"Trixie"},
{question:"What group does Hayley like?",options:["Stray Kids","Blackpink","IVE"],answer:"Stray Kids",member:"Hayley"},
{question:"Alyssa's favorite style?",options:["Coquette","Comfy","Sporty"],answer:"Coquette",member:"Alyssa"}
];
let currentQ=0;
function loadQuiz(){
let area=document.getElementById('quizArea'); area.innerHTML='';
if(currentQ>=quizQuestions.length){alert('Quiz finished! +20 Coins & Badges!'); data.coins+=20; data.badges.push('☁️🎀🐶'); saveData(); updateDisplay(); return;}
let q=quizQuestions[currentQ];
let html=`<p>${q.question}</p>`;
q.options.forEach(opt=>{html+=`<button onclick="checkAnswer('${opt}')">${opt}</button>`;});
area.innerHTML=html;
}
function checkAnswer(opt){
let q=quizQuestions[currentQ];
if(opt===q.answer){alert('Correct! 🎉'); data.coins+=10;} else {alert('Wrong! ❌');}
currentQ++; saveData(); updateDisplay(); loadQuiz();
}

// ==== FANDOM REVEAL ====
function revealFandom(){document.getElementById('fandomReveal').innerText='KAES 🎀';}

// ==== USERNAME PROMPT ====
if(!data.username){data.username=prompt("Enter your fan name:"); saveData();}

// ==== SAVE & UPDATE ====
function saveData(){localStorage.setItem('kheartsData',JSON.stringify(data)); updateLeaderboard();}
function updateDisplay(){
document.getElementById('coins').innerText=data.coins;
document.getElementById('badges').innerText=data.badges.join(', ')||'None';
document.getElementById('petContainer').innerText=data.pet;
document.getElementById('petHappiness').innerText=data.petHappiness;
updateMembers(); updateLeaderboard(); updateChatWindow();
}

// ==== INITIAL LOAD ====
updateDisplay(); loadQuiz();
</script>

</body>
</html>
