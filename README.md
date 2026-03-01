<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>K-Hearts Fan Universe</title>
<style>
body{margin:0;padding:0;font-family:sans-serif;background:#ffe6f0;color:#000;}
nav{display:flex;flex-wrap:wrap;gap:5px;background:#ffb6c1;padding:5px;justify-content:center;}
nav button{padding:5px 10px;background:#fff0f5;border:none;border-radius:5px;cursor:pointer;}
.page{display:none;padding:10px;}
.avatar-container{position:relative;width:150px;height:300px;margin:10px;}
.avatar-part{position:absolute;}
.outfit-torso{width:100%;height:50%;top:100px;background:#ffb6c1;}
.outfit-bottom{width:100%;height:50%;top:200px;background:#ff99ff;}
.pet{position:absolute;bottom:10px;left:10px;font-size:30px;}
.confetti{position:absolute;top:0;left:0;width:100%;height:100%;pointer-events:none;}
.fade-in{animation:fadeIn 0.5s;}
@keyframes fadeIn{from{opacity:0;}to{opacity:1;}}
</style>
</head>
<body>

<nav>
<button onclick="showPage('homePage')">Home</button>
<button onclick="showPage('avatarPage')">Avatar</button>
<button onclick="showPage('chatPage')">Chat</button>
<button onclick="showPage('gamesPage')">Games</button>
<button onclick="showPage('shopPage')">Shop</button>
<button onclick="showPage('leaderboardPage')">Leaderboard</button>
<button onclick="showPage('lyricsPage')">Lyrics</button>
<button onclick="showPage('eventsPage')">Events</button>
</nav>

<!-- HOME -->
<div id="homePage" class="page" style="display:block;">
<h1 style="text-align:center;color:#ff66b2;">💖 Welcome to K-Hearts Fan Universe 💖</h1>
<p style="text-align:center;">✨ KAES Fandom Name Reveal: <span id="fandomReveal"></span> ✨</p>
<button onclick="revealFandom()">Reveal KAES</button>
</div>

<!-- AVATAR -->
<div id="avatarPage" class="page">
<h2>🎀 Your Avatar</h2>
<div class="avatar-container" id="avatarContainer">
<div class="avatar-part outfit-torso" id="torso"></div>
<div class="avatar-part outfit-bottom" id="bottom"></div>
<div class="avatar-part pet" id="pet">🐧</div>
</div>
<p>Coins: <span id="coins">0</span> | Badges: <span id="badges">None</span></p>
</div>

<!-- CHAT -->
<div id="chatPage" class="page">
<h2>💬 Chat with Idols</h2>
<div id="chatWindow" style="height:200px;overflow-y:scroll;background:#fff0f5;padding:10px;border:2px solid #ffb6c1;border-radius:10px;"></div>
<input type="text" id="chatInput" placeholder="Type your message..." style="width:70%;">
<button onclick="sendMessage()">Send</button>
</div>

<!-- GAMES -->
<div id="gamesPage" class="page">
<h2>🎮 Games & Mini-Games</h2>
<button onclick="playBeatGame()">🎵 Rhythm Tap</button>
<button onclick="playDanceBattle()">💃 Dance Battle</button>
<button onclick="playHeartCatch()">💖 Heart Catch</button>
<button onclick="playQuiz()">📝 Quiz</button>
</div>

<!-- SHOP -->
<div id="shopPage" class="page">
<h2>🛍️ Shop</h2>
<button onclick="buyItem('Glitter Dress',40,'#ff99ff')">Glitter Dress - 40 coins</button>
<button onclick="buyItem('Comfy Hoodie',20,'#ffb6c1')">Comfy Hoodie - 20 coins</button>
<button onclick="buyItem('Pink Lightstick',30,'✨')">Pink Lightstick - 30 coins</button>
<button onclick="buyItem('Penguin Pet',25,'🐧')">Penguin Pet - 25 coins</button>
</div>

<!-- LEADERBOARD -->
<div id="leaderboardPage" class="page">
<h2>🏅 Leaderboard</h2>
<div id="dailyBoard"></div>
</div>

<!-- LYRICS -->
<div id="lyricsPage" class="page">
<h2>🎶 "No Limits" Lyrics</h2>
<pre id="lyrics"></pre>
</div>

<!-- EVENTS -->
<div id="eventsPage" class="page">
<h2>🎉 Seasonal Events</h2>
<button onclick="activateEvent('Halloween')">🎃 Halloween</button>
<button onclick="activateEvent('Valentine')">💖 Valentine</button>
<button onclick="activateEvent('Winter')">❄️ Winter</button>
<div id="eventItems"></div>
</div>

<canvas id="confettiCanvas" class="confetti"></canvas>

<script>
// ==== DATA STORAGE ====
if(!localStorage.getItem('kheartsData')){
localStorage.setItem('kheartsData',JSON.stringify({
username:'',coins:0,badges:[],outfit:'Default',pet:'🐧',chat:[],daily:[]}));
}
let data=JSON.parse(localStorage.getItem('kheartsData'));

// ==== GENERAL FUNCTIONS ====
function saveData(){localStorage.setItem('kheartsData',JSON.stringify(data));updateDisplay();}
function updateDisplay(){
document.getElementById('coins').innerText=data.coins;
document.getElementById('badges').innerText=data.badges.join(', ')||'None';
document.getElementById('torso').style.backgroundColor=(data.outfitColor||'#ffb6c1');
document.getElementById('bottom').style.backgroundColor=(data.outfitColor||'#ff99ff');
document.getElementById('pet').innerText=data.pet||'🐧';
updateLeaderboard();
}
function showPage(id){document.querySelectorAll('.page').forEach(p=>p.style.display='none');document.getElementById(id).style.display='block';fadeIn(document.getElementById(id));}
function fadeIn(el){let op=0;let timer=setInterval(()=>{if(op>=1){clearInterval(timer);}else{op+=0.05;el.style.opacity=op;}},20);}

// ==== FAN NAME REVEAL ====
function revealFandom(){document.getElementById('fandomReveal').innerText='KAES';}

// ==== CHAT FUNCTIONS ====
function updateChatWindow(){
let chatWin=document.getElementById('chatWindow'); chatWin.innerHTML='';
data.chat.forEach(msg=>{let p=document.createElement('p');p.innerHTML=msg;chatWin.appendChild(p);});
chatWin.scrollTop=chatWin.scrollHeight;
}
function sendMessage(){
let input=document.getElementById('chatInput'); if(input.value.trim()===''){return;}
let userMsg="<b>"+(data.username||'Guest')+":</b> "+input.value;
data.chat.push(userMsg);
// Idol responses
let idolResponses=[
"☁️ Karlyn noticed your message!",
"🎀 Alyssa waves hello!",
"🥟 Trixie cheers you on!",
"💖 You're amazing, keep going!",
"✨ KAES universe shines because of you!"
];
let idolReply="<b>Idol:</b> "+idolResponses[Math.floor(Math.random()*idolResponses.length)];
data.chat.push(idolReply);
saveData(); updateChatWindow(); input.value='';
}

// ==== LEADERBOARD ====
function updateLeaderboard(){
let board=document.getElementById('dailyBoard'); board.innerHTML='';
let dailyCopy=[...data.daily];
dailyCopy.sort((a,b)=>b.coins-a.coins);
dailyCopy.forEach((p,i)=>{let pElem=document.createElement('p'); pElem.innerText=(i+1)+". "+p.name+" — "+p.coins+" coins";board.appendChild(pElem);});
}

// ==== SHOP ITEMS ====
function buyItem(name,cost,colorOrSymbol){
if(data.coins<cost){alert("Not enough coins!");return;}
data.coins-=cost;
if(name.includes('Dress')||name.includes('Hoodie')){data.outfit=name; data.outfitColor=colorOrSymbol;}
if(name.includes('Pet')){data.pet=colorOrSymbol;}
if(name.includes('Lightstick')){data.pet=colorOrSymbol;}
saveData(); alert(name+" purchased!");updateDisplay();
}

// ==== EVENTS ====
function activateEvent(eventName){
let items=document.getElementById('eventItems'); items.innerHTML='';
if(eventName==="Halloween"){items.innerHTML="<p>🎃 Pumpkin Hat - 50 coins</p><p>🕸️ Spider Accessory - 30 coins</p>";}
else if(eventName==="Valentine"){items.innerHTML="<p>💘 Heart Wings - 50 coins</p><p>🍫 Chocolate Prop - 30 coins</p>";}
else if(eventName==="Winter"){items.innerHTML="<p>❄️ Snow Hoodie - 50 coins</p><p>☃️ Snowball Accessory - 30 coins</p>";}
alert(eventName+" event is now active!");
}

// ==== LYRICS ====
const lyricsText=`No limits
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
No ceiling — we climb.`;
document.getElementById('lyrics').innerText=lyricsText;

// ==== INITIALIZE USERNAME ====
if(!data.username){data.username=prompt("Enter your KAES fan name:"); saveData();}

// ==== INITIAL DISPLAY ====
updateDisplay(); updateChatWindow(); updateLeaderboard();

// ==== SIMPLE GAMES PLACEHOLDER ====
function playBeatGame(){alert("Beat Game coming soon! Tap hearts on the rhythm.");}
function playDanceBattle(){alert("Dance Battle coming soon! Challenge AI idols.");}
function playHeartCatch(){alert("Heart Catch coming soon! Collect hearts!");}
function playQuiz(){alert("Quiz coming soon! Test your KAES knowledge!");}

// ==== CONFETTI ====
const canvas=document.getElementById('confettiCanvas'); const ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;
let confetti=[];
for(let i=0;i<100;i++){confetti.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*6+2,dx:(Math.random()-0.5)*2,dy:Math.random()*3+2,color:`hsl(${Math.random()*360},100%,70%)`});}
function drawConfetti(){ctx.clearRect(0,0,canvas.width,canvas.height); confetti.forEach(c=>{ctx.fillStyle=c.color;ctx.beginPath();ctx.arc(c.x,c.y,c.r,0,2*Math.PI);ctx.fill();c.x+=c.dx;c.y+=c.dy;if(c.y>canvas.height){c.y=0;c.x=Math.random()*canvas.width;}});requestAnimationFrame(drawConfetti);}
drawConfetti(); window.addEventListener('resize',()=>{canvas.width=window.innerWidth;canvas.height=window.innerHeight;});
</script>

</body>
</html>
