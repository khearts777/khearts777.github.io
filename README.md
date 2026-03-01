 <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>K-Hearts Fan Universe Stage 1</title>
<style>
body{margin:0;padding:0;font-family:sans-serif;background:#ffe6f0;color:#000;}
nav{display:flex;gap:5px;background:#ffb6c1;padding:5px;justify-content:center;flex-wrap:wrap;}
nav button{padding:5px 10px;background:#fff0f5;border:none;border-radius:5px;cursor:pointer;}
.page{display:none;padding:10px;}
.avatar-container{position:relative;width:150px;height:300px;margin:10px;border:2px solid #ff99ff;border-radius:10px;background:#fff0f5;}
.avatar-part{position:absolute;}
.outfit-torso{width:100%;height:50%;top:100px;background:#ffb6c1;}
.outfit-bottom{width:100%;height:50%;top:200px;background:#ff99ff;}
.hair{top:0;width:100%;height:100px;background:#ff66b2;}
.pet{position:absolute;bottom:10px;left:10px;font-size:30px;}
</style>
</head>
<body>

<nav>
<button onclick="showPage('homePage')">Home</button>
<button onclick="showPage('membersPage')">Members</button>
<button onclick="showPage('avatarPage')">Avatar</button>
</nav>

<!-- HOME PAGE -->
<div id="homePage" class="page" style="display:block;">
<h1 style="text-align:center;color:#ff66b2;">💖 Welcome to K-Hearts Fan Universe 💖</h1>
<p style="text-align:center;">✨ KAES Fandom Name Reveal: <span id="fandomReveal">???</span> ✨</p>
<button onclick="revealFandom()">Reveal KAES</button>
<p style="text-align:center;font-size:20px;color:#ff3399;">Always stay strong! K-Hearts coming soon!</p>
</div>

<!-- MEMBERS PAGE -->
<div id="membersPage" class="page">
<h2>🌸 Meet the Members</h2>
<div id="memberList"></div>
</div>

<!-- AVATAR PAGE -->
<div id="avatarPage" class="page">
<h2>🎀 Your Avatar</h2>
<div class="avatar-container" id="avatarContainer">
<div class="avatar-part hair" id="hair"></div>
<div class="avatar-part outfit-torso" id="torso"></div>
<div class="avatar-part outfit-bottom" id="bottom"></div>
<div class="avatar-part pet" id="pet">🐧</div>
</div>
<p>Coins: <span id="coins">0</span> | Badges: <span id="badges">None</span></p>
</div>

<script>
// ==== DATA STORAGE ====
if(!localStorage.getItem('kheartsData')){
localStorage.setItem('kheartsData',JSON.stringify({
username:'',coins:0,badges:[],outfitColor:'#ffb6c1',hairColor:'#ff66b2',pet:'🐧'}));
}
let data=JSON.parse(localStorage.getItem('kheartsData'));

// ==== MEMBERS PAGE ====
const members=[
{name:'Karlyn',role:'Leader, Main Rapper, Lead Dancer, Sub Vocalist',pet:'🐧',fav:'White, Japanese food, Penguins, Popmarts (Crybabies)'},
{name:'Alyssa',role:'Visual, Main Vocalist, Sub Rapper',pet:'🐶',fav:'Pink, Coquette girl, Loves IVE, Collects cute items'},
{name:'Trixie',role:'Main Dancer, Lead Rapper, Sub Vocalist',pet:'🐱',fav:'Wushu pants, comfy fits, Loves SKZ and NJZ'}
];
function updateMembers(){
let list=document.getElementById('memberList');
list.innerHTML='';
members.forEach(m=>{
let div=document.createElement('div');
div.innerHTML=`<h3>${m.name} ${m.pet}</h3><p>Role: ${m.role}</p><p>Favorites: ${m.fav}</p>`;
list.appendChild(div);
});
}

// ==== GENERAL FUNCTIONS ====
function saveData(){localStorage.setItem('kheartsData',JSON.stringify(data));updateDisplay();}
function updateDisplay(){
document.getElementById('coins').innerText=data.coins;
document.getElementById('badges').innerText=data.badges.join(', ')||'None';
document.getElementById('torso').style.backgroundColor=data.outfitColor;
document.getElementById('bottom').style.backgroundColor='#ff99ff';
document.getElementById('hair').style.backgroundColor=data.hairColor;
document.getElementById('pet').innerText=data.pet;
updateMembers();
}
function showPage(id){
document.querySelectorAll('.page').forEach(p=>p.style.display='none');
document.getElementById(id).style.display='block';
}

// ==== FAN NAME REVEAL ====
function revealFandom(){document.getElementById('fandomReveal').innerText='KAES';}

// ==== INITIALIZE USERNAME ====
if(!data.username){
data.username=prompt("Enter your KAES fan name:");
saveData();
}

// ==== INITIAL DISPLAY ====
updateDisplay();
</script>

</body>
</html>

<script>
// ==== QUIZZES ====
const quizzes=[
{
member:'Karlyn',
questions:[
{q:'Favorite color?', options:['White','Pink','Blue'], answer:'White'},
{q:'Favorite food?', options:['Sushi','Pizza','Ramen'], answer:'Sushi'},
{q:'Favorite animal?', options:['Penguin','Dog','Cat'], answer:'Penguin'}
]
},
{
member:'Alyssa',
questions:[
{q:'Favorite color?', options:['White','Pink','Red'], answer:'Pink'},
{q:'Favorite type of girl?', options:['Coquette','Cool','Sporty'], answer:'Coquette'},
{q:'Favorite group?', options:['IVE','Blackpink','BTS'], answer:'IVE'}
]
},
{
member:'Trixie',
questions:[
{q:'Favorite clothing?', options:['Wushu pants','Jeans','Skirt'], answer:'Wushu pants'},
{q:'Favorite group?', options:['SKZ','IVE','TXT'], answer:'SKZ'},
{q:'Favorite food?', options:['Any','Sushi','Pizza'], answer:'Any'}
]
}
];

function playQuiz(){
let memberQuiz=quizzes[Math.floor(Math.random()*quizzes.length)];
let score=0;
for(let i=0;i<memberQuiz.questions.length;i++){
let q=memberQuiz.questions[i];
let userAns=prompt(`${memberQuiz.member} Quiz:\n${q.q}\nOptions: ${q.options.join(', ')}`);
if(userAns && userAns.toLowerCase()===q.answer.toLowerCase()){
score++; alert('Correct!'); 
}else{alert('Oops! Correct answer: '+q.answer);}
}
// Reward
if(score===memberQuiz.questions.length){
let badge='';
if(memberQuiz.member==='Karlyn') badge='☁️';
if(memberQuiz.member==='Alyssa') badge='🎀';
if(memberQuiz.member==='Trixie') badge='🥟';
if(!data.badges.includes(badge)) data.badges.push(badge);
data.coins+=50; // reward coins
alert(`Perfect! You earned 50 coins + badge ${badge}!`);
}else{
data.coins+=score*10; // partial coins
alert(`You got ${score} correct. Coins earned: ${score*10}`);
}
saveData();
}

// ==== SIMPLE MINI-GAMES ====
function playBeatGame(){alert("🎵 Rhythm Tap! You earned 20 coins!"); data.coins+=20; saveData(); updateDisplay();}
function playDanceBattle(){alert("💃 Dance Battle! You earned 30 coins!"); data.coins+=30; saveData(); updateDisplay();}
function playHeartCatch(){alert("💖 Heart Catch! You earned 25 coins!"); data.coins+=25; saveData(); updateDisplay();}
</script>

<script>
// ==== SHOP ITEMS ====
const shopItems=[
{name:'Glitter Dress',cost:40,type:'outfit',color:'#ff99ff'},
{name:'Comfy Hoodie',cost:20,type:'outfit',color:'#ffb6c1'},
{name:'Pink Lightstick',cost:30,type:'prop',symbol:'✨'},
{name:'Penguin Pet',cost:25,type:'pet',symbol:'🐧'},
{name:'Dog Pet',cost:25,type:'pet',symbol:'🐶'},
{name:'Cat Pet',cost:25,type:'pet',symbol:'🐱'}
];

function buyItem(name){
let item=shopItems.find(i=>i.name===name);
if(!item){alert('Item not found!'); return;}
if(data.coins<item.cost){alert('Not enough coins!'); return;}
data.coins-=item.cost;

// Apply item
if(item.type==='outfit'){data.outfitColor=item.color;}
if(item.type==='pet'){data.pet=item.symbol;}
if(item.type==='prop'){alert('You got the '+name+'!');} // can add more prop effects
alert('Purchased '+name+'!');
saveData();
updateDisplay();
}

// ==== LEADERBOARD ====
if(!localStorage.getItem('kheartsLeaderboard')) localStorage.setItem('kheartsLeaderboard',JSON.stringify([]));
function updateLeaderboard(){
let lb=document.getElementById('dailyBoard'); if(!lb) return;
let list=JSON.parse(localStorage.getItem('kheartsLeaderboard'));
let found=list.find(u=>u.name===data.username);
if(found){found.coins=data.coins;} else {list.push({name:data.username,coins:data.coins});}
list.sort((a,b)=>b.coins-a.coins);
localStorage.setItem('kheartsLeaderboard',JSON.stringify(list));
lb.innerHTML='';
list.forEach((u,i)=>{let p=document.createElement('p'); p.innerText=(i+1)+". "+u.name+" — "+u.coins+" coins"; lb.appendChild(p);});
}

// ==== INITIAL DISPLAY UPDATE ====
updateLeaderboard();
</script>

<script>
// ==== AVATAR LAYERING ====
function setAvatarLayer(outfitColor, hairColor, petSymbol){
document.getElementById('torso').style.backgroundColor=outfitColor||'#ffb6c1';
document.getElementById('bottom').style.backgroundColor='#ff99ff';
document.getElementById('hair').style.backgroundColor=hairColor||'#ff66b2';
document.getElementById('pet').innerText=petSymbol||'🐧';
}

// ==== FULL AVATAR UPDATE ====
function updateAvatar(){
setAvatarLayer(data.outfitColor,data.hairColor,data.pet);
updateDisplay();
}

// ==== MINI-GAMES FULL FUNCTIONAL ====
function playBeatGame(){
let earned=Math.floor(Math.random()*30)+20;
alert(`🎵 Rhythm Tap! You earned ${earned} coins!`);
data.coins+=earned;
saveData(); updateAvatar(); updateLeaderboard(); showConfetti();
}
function playDanceBattle(){
let earned=Math.floor(Math.random()*40)+20;
alert(`💃 Dance Battle! You earned ${earned} coins!`);
data.coins+=earned;
saveData(); updateAvatar(); updateLeaderboard(); showConfetti();
}
function playHeartCatch(){
let earned=Math.floor(Math.random()*35)+15;
alert(`💖 Heart Catch! You earned ${earned} coins!`);
data.coins+=earned;
saveData(); updateAvatar(); updateLeaderboard(); showConfetti();
}

// ==== QUIZZES FULL FUNCTIONAL ====
function playQuiz(){
let memberQuiz=quizzes[Math.floor(Math.random()*quizzes.length)];
let score=0;
for(let i=0;i<memberQuiz.questions.length;i++){
let q=memberQuiz.questions[i];
let userAns=prompt(`${memberQuiz.member} Quiz:\n${q.q}\nOptions: ${q.options.join(', ')}`);
if(userAns && userAns.toLowerCase()===q.answer.toLowerCase()){
score++; alert('Correct!'); 
}else{alert('Oops! Correct answer: '+q.answer);}
}
let badge='';
if(score===memberQuiz.questions.length){
if(memberQuiz.member==='Karlyn') badge='☁️';
if(memberQuiz.member==='Alyssa') badge='🎀';
if(memberQuiz.member==='Trixie') badge='🥟';
if(!data.badges.includes(badge)) data.badges.push(badge);
data.coins+=50; alert(`Perfect! You earned 50 coins + badge ${badge}!`);
}else{
data.coins+=score*10; alert(`You got ${score} correct. Coins earned: ${score*10}`);
}
saveData(); updateAvatar(); updateLeaderboard(); showConfetti();
}

// ==== CHAT FULL FUNCTIONAL ====
function updateChatWindow(){
let chatWin=document.getElementById('chatWindow'); 
chatWin.innerHTML='';
data.chat.forEach(msg=>{
let p=document.createElement('p'); p.innerHTML=msg; chatWin.appendChild(p);
}); chatWin.scrollTop=chatWin.scrollHeight;
}

function sendMessage(){
let input=document.getElementById('chatInput');
if(input.value.trim()===''){return;}
let userMsg=`<b>${data.username}:</b> ${input.value}`;
data.chat.push(userMsg);

// Personalized idol responses
let idolResponses=[
`☁️ Karlyn waves at you wearing your outfit!`,
`🎀 Alyssa wags her pet dog at you!`,
`🥟 Trixie purrs with her cat!`,
`💖 You have ${data.coins} coins now! Keep going!`,
`✨ Your badges: ${data.badges.join(', ')||'None'} shine brightly!`,
`🌸 Your avatar looks amazing today!`
];
let idolReply="<b>Idol:</b> "+idolResponses[Math.floor(Math.random()*idolResponses.length)];
data.chat.push(idolReply);
saveData(); updateChatWindow(); input.value='';
}

// ==== CONFETTI ====
const canvas=document.getElementById('confettiCanvas'); const ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;
let confetti=[];
for(let i=0;i<150;i++){
confetti.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*6+2,dx:(Math.random()-0.5)*2,dy:Math.random()*3+2,color:`hsl(${Math.random()*360},100%,70%)`});
}
function drawConfetti(){
ctx.clearRect(0,0,canvas.width,canvas.height);
confetti.forEach(c=>{
ctx.fillStyle=c.color;
ctx.beginPath();
ctx.arc(c.x,c.y,c.r,0,2*Math.PI);
ctx.fill();
c.x+=c.dx; c.y+=c.dy;
if(c.y>canvas.height){c.y=0;c.x=Math.random()*canvas.width;}
});
requestAnimationFrame(drawConfetti);
}
drawConfetti();
function showConfetti(){for(let i=0;i<50;i++){confetti.push({x:Math.random()*canvas.width,y:0,r:Math.random()*6+2,dx:(Math.random()-0.5)*2,dy:(Math.random()*3)+2,color:`hsl(${Math.random()*360},100%,70%)`});}}

// ==== INITIALIZE ====
updateAvatar(); updateChatWindow(); updateLeaderboard();
</script>

