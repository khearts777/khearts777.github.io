<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>K-Hearts Fan Universe 💖</title>
<link href="https://fonts.googleapis.com/css2?family=Bubblegum+Sans&display=swap" rel="stylesheet">
<style>
body{margin:0;padding:0;font-family:'Bubblegum Sans',cursive;background:linear-gradient(135deg,#ffe6f0,#ffd1ff);color:#000;transition:all 0.3s;}
nav{display:flex;justify-content:center;flex-wrap:wrap;gap:5px;background:#ffb6c1;padding:5px;}
nav button{padding:8px 15px;border:none;border-radius:10px;cursor:pointer;background:#fff0f5;font-weight:bold;transition:all 0.2s;}
nav button:hover{transform:scale(1.1);background:#ff99cc;}
.page{display:none;padding:10px;}
h1,h2,h3{text-align:center;color:#ff3399;}
.member-card{background:#ffe0f5;margin:5px;padding:8px;border-radius:12px;text-align:center;transition:0.3s;cursor:pointer;}
.member-card:hover{transform:scale(1.05);box-shadow:0 0 15px #ff99cc;}
#petContainer{position:relative;width:150px;height:150px;margin:20px auto;}
.pet{position:absolute;font-size:100px;transition:all 0.5s;}
.pet-hat{position:absolute;top:-20px;left:25px;font-size:50px;pointer-events:none;}
.pet-collar{position:absolute;bottom:5px;left:40px;font-size:30px;pointer-events:none;}
#petHappiness{font-weight:bold;color:#ff3399;text-align:center;margin-top:10px;}
.itemBtn{margin:3px;padding:5px;border-radius:10px;cursor:pointer;background:#ffccf0;border:none;transition:0.2s;}
.itemBtn:hover{transform:scale(1.1);background:#ff99cc;}
#chatWindow,#gameArea,#quizArea,#leaderboardList,#lyricsContainer{border:2px solid #ff99cc;padding:5px;border-radius:10px;background:#fff0f5;overflow-y:auto;}
#chatWindow{height:200px;}
.chatBubble{background:#ffe6f0;margin:3px;padding:5px;border-radius:10px;}
#coins,#badges{font-weight:bold;color:#ff3399;}
button.gameBtn{margin:3px;padding:5px;border-radius:10px;cursor:pointer;background:#ffccf0;border:none;transition:0.2s;}
button.gameBtn:hover{transform:scale(1.1);background:#ff99cc;}
</style>
</head>
<body>

<h1>💖 K-Hearts Fan Universe 💖</h1>

<p style="text-align:center;font-size:20px;color:#ff3399;">Always stay strong! K-Hearts coming soon!</p>

<div style="text-align:center;margin-bottom:10px;">
Coins: <span id="coins">0</span> | Badges: <span id="badges">None</span>
</div>

<nav>
<button onclick="showSection('members')">Members</button>
<button onclick="showSection('pets')">Pets</button>
<button onclick="showSection('shop')">Shop</button>
<button onclick="showSection('games')">Games</button>
<button onclick="showSection('quiz')">Quiz</button>
<button onclick="showSection('chat')">AI Chat</button>
<button onclick="showSection('leaderboard')">Leaderboard</button>
<button onclick="showSection('lyrics')">Lyrics</button>
</nav>

<!-- MEMBERS -->
<div id="members" class="page">
<h2>🌸 Meet the Members</h2>
<div id="memberList"></div>
</div>

<!-- PETS -->
<div id="pets" class="page">
<h2>🐾 Your Pet</h2>
<div id="petContainer">
  <div class="pet" id="petEmoji">🐧</div>
  <div class="pet-hat" id="petHat"></div>
  <div class="pet-collar" id="petCollar"></div>
</div>
<p>Happiness: <span id="petHappiness">50</span>/100 💖</p>
<button onclick="choosePet('🐧')">Choose Penguin 🐧</button>
<button onclick="choosePet('🐶')">Choose Dog 🐶</button>
<button onclick="choosePet('🐱')">Choose Cat 🐱</button>
<button onclick="petAction('play')">Play 🎾</button>
<button onclick="petAction('bathe')">Bathe 🛁</button>
</div>

<!-- SHOP -->
<div id="shop" class="page">
<h2>🛒 Pet Items Shop</h2>
<button class="itemBtn" onclick="buyItem('Toy Ball','toy','🎾',10)">Toy Ball - 10 Coins</button>
<button class="itemBtn" onclick="buyItem('Pet Hat','hat','🎀',15)">Pet Hat - 15 Coins</button>
<button class="itemBtn" onclick="buyItem('Pet Collar','collar','💖',20)">Pet Collar - 20 Coins</button>
</div>

<!-- GAMES -->
<div id="games" class="page">
<h2>🎮 Fun Mini-Games</h2>
<div id="gameArea">
<button class="gameBtn" onclick="playMemory()">Memory Match</button>
<button class="gameBtn" onclick="spinWheel()">Spin the Wheel</button>
<button class="gameBtn" onclick="quickTap()">Quick Tap Hearts</button>
<button class="gameBtn" onclick="petTrick()">Pet Trick</button>
</div>
<div id="gameMessage" style="text-align:center;margin-top:10px;color:#ff3399;"></div>
</div>

<!-- QUIZ -->
<div id="quiz" class="page">
<h2>📝 Member Quiz</h2>
<div id="quizArea"></div>
</div>

<!-- AI CHAT -->
<div id="chat" class="page">
<h2>💌 Chat with AI Idols</h2>
<select id="idolSelect">
<option value="Karlyn">Karlyn</option>
<option value="Trixie">Trixie</option>
<option value="Hayley">Hayley</option>
<option value="Alyssa">Alyssa</option>
</select>
<div id="chatWindow"></div>
<input type="text" id="chatInput" placeholder="Say something...">
<button onclick="sendMessage()">Send</button>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="page">
<h2>🏆 Leaderboard</h2>
<div id="leaderboardList"></div>
</div>

<!-- LYRICS -->
<div id="lyrics" class="page">
<h2>🎵 No Limits Lyrics</h2>
<div id="lyricsContainer" style="height:250px;">
<p>No limits<br>No pressure<br>No ceiling<br>We go up</p>
<p>Walk in like a headline, cameras all flash<br>Step so sharp, make the whole world crash<br>Different languages, same ambition<br>Born to win — that’s the only mission</p>
<p>Mirror mirror, we don’t compete<br>We break the glass in designer feet<br>No permission, we elevate<br>Watch how legends are made</p>
<p>We don’t bend, we don’t break<br>Pressure turns to diamonds in our wake<br>Every scar is a shining mark<br>Strike a match — ignite the dark</p>
<p>We go higher, higher<br>Touch the sky, no ceiling<br>Fearless fire, fire<br>Got the whole world feeling</p>
<p>No doubts, no fear<br>We came too far to disappear<br>Global girls, we redefine<br>Step aside — the crown is mine</p>
</div>
</div>

<script>
// ===== DATA =====
if(!localStorage.getItem('kheartsData')){
localStorage.setItem('kheartsData',JSON.stringify({
username:'',coins:0,badges:[],pet:'🐧',petHappiness:50,shopItems:[],chatHistory:[],quizProgress:0
}));
}
let data=JSON.parse(localStorage.getItem('kheartsData'));

// ===== MEMBERS =====
const members=[
{name:'Karlyn',role:'Leader, Main Rapper, Lead Dancer, Sub Vocalist',pet:'🐧',fav:'White, Japanese food, Penguins, Popmarts (Crybabies)'},
{name:'Trixie',role:'Centre, Sub Rapper, Main Dancer, Sub Vocalist',pet:'🐱',fav:'Comfy clothes, SKZ & NJZ'},
{name:'Hayley',role:'Lead Dancer, Lead Vocalist, Maknae',pet:'🐶',fav:'Black, Stray Kids'},
{name:'Alyssa',role:'Main Vocalist, Visual, Sub Rapper & Sub Dancer',pet:'🐶',fav:'Pink, Coquette style, IVE'}
];

// ===== DISPLAY MEMBERS =====
function updateMembers(){
let list=document.getElementById('memberList'); list.innerHTML='';
members.forEach(m=>{
let div=document.createElement('div');
div.className='member-card';
div.innerHTML=`<h3>${m.name} ${m.pet}</h3><p>Role: ${m.role}</p><p>Favorites: ${m.fav}</p>`;
list.appendChild(div);
});
}

// ===== PAGE SWITCH =====
function showSection(id){
document.querySelectorAll('.page').forEach(p=>p.style.display='none');
document.getElementById(id).style.display='block';
}

// ===== PET SYSTEM =====
function updatePetDisplay(){
document.getElementById('petEmoji').innerText=data.pet;
document.getElementById('petHappiness').innerText=data.petHappiness;
document.getElementById('petHat').innerText=data.shopItems.includes('Pet Hat')?'🎀':'';
document.getElementById('petCollar').innerText=data.shopItems.includes('Pet Collar')?'💖':'';
}

function choosePet(pet){
data.pet=pet; data.petHappiness=50; saveData(); updatePetDisplay();
alert('You chose '+pet+'! Take good care of them!');
}

function petAction(action){
let petEl=document.getElementById('petEmoji');
if(action==='play'){
if(!data.shopItems.includes('Toy Ball')){alert('Buy a Toy Ball first!'); return;}
data.petHappiness=Math.min(100,data.petHappiness+10); data.coins+=5;
animatePet('play');
}
if(action==='bathe'){
data.petHappiness=Math.min(100,data.petHappiness+15); data.coins+=5;
animatePet('bathe');
}
saveData(); updatePetDisplay(); updateLeaderboard();
}

function animatePet(action){
let petEl=document.getElementById('petEmoji');
if(action==='play'){let x=0; let dir=1;
let interval=setInterval(()=>{x+=dir*10; petEl.style.transform=`translateX(${x}px)`; if(x>50||x<-50) dir*=-1;},100);
setTimeout(()=>{clearInterval(interval); petEl.style.transform='translateX(0px)';},1000);}
if(action==='bathe'){petEl.style.transform='rotate(20deg)'; setTimeout(()=>{petEl.style.transform='rotate(0deg)';},500);}
}

// ===== SHOP =====
function buyItem(name,type,value,cost){
if(data.coins<cost){alert('Not enough coins!'); return;}
if(!data.shopItems.includes(name)) data.shopItems.push(name);
data.coins-=cost; saveData(); updatePetDisplay(); alert(`Purchased ${name}!`);
}

// ===== CHAT AI =====
function updateChatWindow(){
let win=document.getElementById('chatWindow'); win.innerHTML='';
data.chatHistory.forEach(msg=>{
let p=document.createElement('div'); p.className='chatBubble'; p.innerHTML=msg; win.appendChild(p);
});
win.scrollTop=win.scrollHeight;
}

let lastResponse='';
function sendMessage(){
let input=document.getElementById('chatInput');
if(input.value.trim()==='') return;
let member=document.getElementById('idolSelect').value;
let userMsg=`<b>${data.username||'Fan'}:</b> ${input.value}`;
data.chatHistory.push(userMsg);

let responses={
'Karlyn':['You got this! 💖','Keep shining!','Let’s hype it up! ✨'],
'Trixie':['Haha so cute! 🐱','Try this!','You’re awesome 💕'],
'Hayley':['Calm and steady, you can do it 🐶','Great job!','Keep going!'],
'Alyssa':['Sweet vibes! 🎀','Look at you!','So stylish! 💖']
};

let arr=responses[member];
let response;
do{response=arr[Math.floor(Math.random()*arr.length)];}while(response===lastResponse);
lastResponse=response;
data.chatHistory.push('<b>'+member+':</b> '+response);

data.coins+=5; // reward coins for chatting
input.value=''; saveData(); updateChatWindow(); updateDisplay();
}

// ===== LEADERBOARD =====
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

// ===== QUIZ =====
const quizQuestions=[
{question:"What is Karlyn's favorite color?",options:["White","Pink","Black"],answer:"White",member:"Karlyn"},
{question:"Which pet does Trixie have?",options:["Dog","Cat","Penguin"],answer:"Cat",member:"Trixie"},
{question:"What group does Hayley like?",options:["Stray Kids","Blackpink","IVE"],answer:"Stray Kids",member:"Hayley"},
{question:"Alyssa's favorite style?",options:["Coquette","Comfy","Sporty"],answer:"Coquette",member:"Alyssa"}
];
function loadQuiz(){let area=document.getElementById('quizArea'); area.innerHTML=''; if(data.quizProgress>=quizQuestions.length){alert('Quiz finished! +20 Coins & Badges!'); data.coins+=20; data.badges.push('☁️🎀🐶'); saveData(); updateDisplay(); return;}
let q=quizQuestions[data.quizProgress];
let html=`<p>${q.question}</p>`; q.options.forEach(opt=>{html+=`<button onclick="checkAnswer('${opt}')">${opt}</button>`;}); area.innerHTML=html;
}
function checkAnswer(opt){let q=quizQuestions[data.quizProgress]; if(opt===q.answer){alert('Correct! 🎉'); data.coins+=10;} else {alert('Wrong! ❌');} data.quizProgress++; saveData(); updateDisplay(); loadQuiz();}

// ===== MINI-GAMES =====
function playMemory(){alert('Memory Match: Match pairs! +10 Coins'); data.coins+=10; saveData(); updateDisplay();}
function spinWheel(){let coins=Math.floor(Math.random()*20+5); alert(`Spin the Wheel: You got ${coins} Coins!`); data.coins+=coins; saveData(); updateDisplay();}
function quickTap(){let coins=Math.floor(Math.random()*15+5); alert(`Quick Tap: You earned ${coins} Coins!`); data.coins+=coins; saveData(); updateDisplay();}
function petTrick(){let coins=Math.floor(Math.random()*10+5); alert(`Pet Trick Success! +${coins} Coins`); data.coins+=coins; saveData(); updateDisplay();}

// ===== USERNAME =====
if(!data.username){data.username=prompt("Enter your fan name:"); saveData();}

// ===== SAVE & DISPLAY =====
function saveData(){localStorage.setItem('kheartsData',JSON.stringify(data)); updateLeaderboard();}
function updateDisplay(){document.getElementById('coins').innerText=data.coins; document.getElementById('badges').innerText=data.badges.join(', ')||'None'; updatePetDisplay(); updateMembers(); updateLeaderboard(); updateChatWindow();}

// ===== INITIAL LOAD =====
updateDisplay(); loadQuiz(); showSection('members');
</script>

</body>
</html>
