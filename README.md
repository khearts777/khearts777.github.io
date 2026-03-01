<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>K-Hearts Fan Universe</title>
<style>
body{margin:0;padding:0;font-family:sans-serif;background:#ffe6f0;color:#000;}
nav{display:flex;gap:5px;background:#ffb6c1;padding:5px;justify-content:center;flex-wrap:wrap;}
nav button{padding:5px 10px;background:#fff0f5;border:none;border-radius:5px;cursor:pointer;}
.page{display:none;padding:10px;}
h2,h1{color:#ff3399;text-align:center;}
#faceContainer{position:relative;width:200px;height:200px;margin:10px auto;background:#ffe0f5;border-radius:50%;border:2px solid #ff99ff;}
.face-part{position:absolute;text-align:center;width:100%;}
#hair{top:0;height:60px;background:#ff66b2;border-radius:50%;}
#eyes{top:70px;height:30px;font-size:24px;}
#blush{top:110px;height:20px;font-size:24px;color:#ff9999;}
#mouth{top:130px;height:30px;font-size:24px;}
#accessory{top:10px;right:10px;font-size:24px;position:absolute;}
#petContainer{margin:10px auto;text-align:center;font-size:50px;}
button.itemBtn{margin:2px;padding:5px;}
#chatWindow{height:150px;overflow-y:auto;border:1px solid #ff99ff;padding:5px;margin-bottom:5px;}
#lyricsArea{height:200px;overflow-y:auto;border:1px solid #ff99ff;padding:5px;margin-bottom:5px;}
</style>
</head>
<body>

<nav>
<button onclick="showPage('home')">Home</button>
<button onclick="showPage('members')">Members</button>
<button onclick="showPage('avatar')">Avatar</button>
<button onclick="showPage('shop')">Shop</button>
<button onclick="showPage('pets')">Pets</button>
<button onclick="showPage('lyrics')">Lyrics</button>
<button onclick="showPage('chat')">Chat</button>
<button onclick="showPage('leaderboard')">Leaderboard</button>
</nav>

<!-- HOME PAGE -->
<div id="home" class="page" style="display:block;">
<h1>💖 Welcome to K-Hearts Fan Universe 💖</h1>
<p style="text-align:center;">Fandom Name Reveal: <span id="fandomReveal">???</span></p>
<button onclick="document.getElementById('fandomReveal').innerText='KAES';">Reveal KAES</button>
<p style="text-align:center;font-size:20px;color:#ff3399;">Always stay strong! K-Hearts coming soon!</p>
</div>

<!-- MEMBERS PAGE -->
<div id="members" class="page">
<h2>🌸 Meet the Members</h2>
<div id="memberList"></div>
</div>

<!-- AVATAR PAGE -->
<div id="avatar" class="page">
<h2>🎀 Your Face Avatar</h2>
<div id="faceContainer">
<div id="hair" class="face-part"></div>
<div id="eyes" class="face-part">👀 👀</div>
<div id="blush" class="face-part">😊 😊</div>
<div id="mouth" class="face-part">😄</div>
<div id="accessory" class="face-part">📱</div>
</div>
<p>Coins: <span id="coins">0</span> | Badges: <span id="badges">None</span></p>
</div>

<!-- SHOP PAGE -->
<div id="shop" class="page">
<h2>🛒 Shop</h2>
<button class="itemBtn" onclick="buyItem('Pink Hair','hair','#ff66b2',10)">Pink Hair - 10 Coins</button>
<button class="itemBtn" onclick="buyItem('Blue Hair','hair','#66ccff',10)">Blue Hair - 10 Coins</button>
<button class="itemBtn" onclick="buyItem('Blush','blush','😊',5)">Blush - 5 Coins</button>
<button class="itemBtn" onclick="buyItem('Red Blush','blush','😍',5)">Red Blush - 5 Coins</button>
<button class="itemBtn" onclick="buyItem('Phone','accessory','📱',15)">Phone - 15 Coins</button>
<button class="itemBtn" onclick="buyItem('Headphones','accessory','🎧',15)">Headphones - 15 Coins</button>
</div>

<!-- PETS PAGE -->
<div id="pets" class="page">
<h2>🐾 Your Pet</h2>
<div id="petContainer">🐧</div>
<button onclick="petAction('play')">Play with Ball 🎾</button>
<button onclick="petAction('bathe')">Bathe 🛁</button>
<p>Happiness: <span id="petHappiness">50</span>/100</p>
</div>

<!-- LYRICS PAGE -->
<div id="lyrics" class="page">
<h2>🎵 No Limits Lyrics</h2>
<div id="lyricsArea">
<p>No limits<br>No pressure<br>No ceiling<br>We go up</p>
<p>Walk in like a headline, cameras all flash<br>Step so sharp, make the whole world crash<br>Different languages, same ambition<br>Born to win — that’s the only mission</p>
<p>Mirror mirror, we don’t compete<br>We break the glass in designer feet<br>No permission, we elevate<br>Watch how legends are made</p>
<p>We don’t bend, we don’t break<br>Pressure turns to diamonds in our wake<br>Every scar is a shining mark<br>Strike a match — ignite the dark</p>
<p>We go higher, higher<br>Touch the sky, no ceiling<br>Fearless fire, fire<br>Got the whole world feeling</p>
<p>No doubts, no fear<br>We came too far to disappear<br>Global girls, we redefine<br>Step aside — the crown is mine</p>
<!-- Add remaining lyrics similarly -->
</div>
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

<script>
// ==== INITIAL DATA ====
if(!localStorage.getItem('kheartsData')){
localStorage.setItem('kheartsData',JSON.stringify({
username:'',coins:0,badges:[],hairColor:'#ff66b2',blush:'😊',accessory:'📱',pet:'🐧',petHappiness:50,chat:[]}));
}
let data=JSON.parse(localStorage.getItem('kheartsData'));

// ==== MEMBERS DATA ====
const members=[
{name:'Karlyn',role:'Leader, Main Rapper, Lead Dancer, Sub Vocalist',pet:'🐧',fav:'White, Japanese food, Penguins, Popmarts (Crybabies)'},
{name:'Trixie',role:'Centre, Sub Rapper, Main Dancer, Sub Vocalist',pet:'🐱',fav:'Comfy clothes, SKZ & NJZ'},
{name:'Hayley',role:'Lead Dancer, Lead Vocalist, Maknae',pet:'🐧',fav:'Black, Stray Kids'},
{name:'Alyssa',role:'Main Vocalist, Visual, Sub Rapper & Sub Dancer',pet:'🐶',fav:'Pink, Coquette style, IVE'}
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

// ==== DISPLAY FUNCTIONS ====
function updateDisplay(){
document.getElementById('coins').innerText=data.coins;
document.getElementById('badges').innerText=data.badges.join(', ')||'None';
document.getElementById('hair').style.backgroundColor=data.hairColor;
document.getElementById('blush').innerText=data.blush;
document.getElementById('accessory').innerText=data.accessory;
document.getElementById('petContainer').innerText=data.pet;
document.getElementById('petHappiness').innerText=data.petHappiness;
updateMembers();
updateLeaderboard();
updateChatWindow();
}
function showPage(id){
document.querySelectorAll('.page').forEach(p=>p.style.display='none');
document.getElementById(id).style.display='block';
}

// ==== SHOP ====
function buyItem(name,part,value,cost){
if(data.coins<cost){alert('Not enough coins!'); return;}
data.coins-=cost;
if(part==='hair') data.hairColor=value;
if(part==='blush') data.blush=value;
if(part==='accessory') data.accessory=value;
alert(`Purchased ${name}!`);
saveData(); updateDisplay();
}

// ==== PET ACTION ====
function petAction(action){
if(action==='play'){data.petHappiness=Math.min(100,data.petHappiness+10); alert('You played with your pet!');}
if(action==='bathe'){data.petHappiness=Math.min(100,data.petHappiness+15); alert('You bathed your pet!');}
saveData(); updateDisplay();
}

// ==== CHAT ====
function updateChatWindow(){
let win=document.getElementById('chatWindow');
win.innerHTML='';
data.chat.forEach(msg=>{let p=document.createElement('p');p.innerHTML=msg;win.appendChild(p);});
win.scrollTop=win.scrollHeight;
}
function sendMessage(){
let input=document.getElementById('chatInput');
if(input.value.trim()==='') return;
let userMsg=`<b>${data.username}:</b> ${input.value}`;
data.chat.push(userMsg);
let idolReplies=[
`Karlyn waves at you!`,
`Trixie smiles!`,
`Hayley cheers!`,
`Alyssa claps!`,
`Your coins: ${data.coins}`,
`Your badges: ${data.badges.join(',')||'None'}`
];
data.chat.push('<b>Idol:</b> '+idolReplies[Math.floor(Math.random()*idolReplies.length)]);
saveData(); updateChatWindow();
input.value='';
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

// ==== INITIALIZE USERNAME ====
if(!data.username){data.username=prompt("Enter your fan name:"); saveData();}
function saveData(){localStorage.setItem('kheartsData',JSON.stringify(data));}

// ==== INITIAL DISPLAY ====
updateDisplay();
</script>

</body>
</html>
