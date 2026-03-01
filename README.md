<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>K-Hearts Fan Universe</title>
<style>
body {
  margin:0; font-family:Arial; background:linear-gradient(120deg,#ffc0cb,#ffe6f0);
  color:black; text-align:center; overflow-x:hidden;
}
nav {
  background:#ff66b2; padding:15px; position:sticky; top:0; z-index:100;
}
nav button {
  margin:5px; padding:8px 15px; background:#fff; color:#ff66b2; border:none;
  border-radius:20px; cursor:pointer; font-weight:bold;
}
.page {display:none; padding:20px;}
.active {display:block;}
h1 {font-size:40px; background:linear-gradient(45deg,#ff66b2,#fff);
    -webkit-background-clip:text; color:transparent;}
.avatar-container {position:relative; width:150px; height:320px; margin:0 auto;}
#head{width:80px;height:80px;background:#fddac4;border-radius:50%;position:absolute;top:0;left:35px;z-index:5;}
#hair{width:90px;height:40px;background:#ffaacc;position:absolute;top:10px;left:30px;border-radius:20px;z-index:6;}
#torso{width:80px;height:80px;background:pink;position:absolute;top:80px;left:35px;border-radius:10px;z-index:5;}
#arms{width:100px;height:20px;background:#fddac4;position:absolute;top:90px;left:25px;border-radius:10px;z-index:7;}
#bottom{width:80px;height:80px;background:white;position:absolute;top:160px;left:35px;border-radius:10px;z-index:5;}
#shoes{width:80px;height:20px;background:black;position:absolute;top:240px;left:35px;border-radius:5px;z-index:5;}
#handAccessory{position:absolute;top:160px;left:90px;font-size:30px;z-index:10;}
</style>
</head>
<body>

<nav>
<button onclick="showPage('home')">Home</button>
<button onclick="showPage('avatar')">Avatar</button>
</nav>

<div id="coinsDisplay">Coins: 0</div>
<div id="levelDisplay">Level 1 — Rookie</div>

<!-- HOME PAGE -->
<div id="home" class="page active">
<h1>K-HEARTS</h1>
<p>Always stay strong! K-Hearts coming soon! ✨💖💗💕</p>
</div>

<!-- AVATAR PAGE -->
<div id="avatar" class="page">
<h2>Fan Avatar</h2>
<div class="avatar-container">
<div id="head"></div>
<div id="hair"></div>
<div id="torso"></div>
<div id="arms"></div>
<div id="bottom"></div>
<div id="shoes"></div>
<div id="handAccessory"></div>
</div>
<p>Outfit: <span id="outfitDisplay">Basic</span></p>
<button onclick="changeHair('long')">Long Hair</button>
<button onclick="changeHair('short')">Short Hair</button>
<button onclick="changeHair('ponytail')">Ponytail</button>
</div>

<script>
// ==== DATA STORAGE ====
let data = JSON.parse(localStorage.getItem("kheartsData")) || {
  coins:0, username:"", avatar:{head:"#fddac4",hair:"#ffaacc",torso:"pink",arms:"#fddac4",bottom:"white",shoes:"black",accessory:""}, outfit:"Basic", hairstyle:"long"
};

// Ask username if new
if(!data.username){
  data.username = prompt("Welcome KAES! Enter your name:");
  localStorage.setItem("kheartsData", JSON.stringify(data));
}

// ==== DISPLAY UPDATE ====
function updateDisplay(){
  document.getElementById("coinsDisplay").innerText="Coins: "+data.coins;
  document.getElementById("levelDisplay").innerText="Level 1 — Rookie";
  document.getElementById("head").style.background=data.avatar.head;
  document.getElementById("hair").style.background=data.avatar.hair;
  document.getElementById("torso").style.background=data.avatar.torso;
  document.getElementById("arms").style.background=data.avatar.arms;
  document.getElementById("bottom").style.background=data.avatar.bottom;
  document.getElementById("shoes").style.background=data.avatar.shoes;
  document.getElementById("handAccessory").innerText=data.avatar.accessory;
  document.getElementById("outfitDisplay").innerText=data.outfit;
}
updateDisplay();
function saveData(){localStorage.setItem("kheartsData", JSON.stringify(data));}

// ==== PAGE SWITCH ====
function showPage(id){
  document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
  document.getElementById(id).classList.add("active");
}

// ==== HAIRSTYLE SWITCH ====
function changeHair(style){
  data.hairstyle=style;
  if(style=="long"){data.avatar.hair="#ffaacc";}
  else if(style=="short"){data.avatar.hair="#ff99cc";}
  else if(style=="ponytail"){data.avatar.hair="#ffb3e6";}
  updateDisplay(); saveData();
}
</script>

</body>
</html>

<!-- GAMES PAGE -->
<div id="games" class="page">
<h2>💖 Click Heart Game</h2>
<button onclick="startHearts()">Start</button>
<div id="gameArea" style="position:relative;width:100%;height:200px;"></div>

<h2>☁️ Karlyn Quiz</h2>
<div id="quiz1"></div>
<h2>🎀 Alyssa Quiz</h2>
<div id="quiz2"></div>
<h2>🥟 Trixie Quiz</h2>
<div id="quiz3"></div>

<h2>🎯 Catch the Falling Heart</h2>
<button onclick="startCatchGame()">Start</button>
<div id="catchArea" style="position:relative;width:100%;height:200px;"></div>
</div>

<script>
// ==== COINS & LEVELS ====
const titles = ["Rookie","Trainee","Rising Star","Performer","Stage Slayer","Icon","Global Glow","Elite KAES","Legend","Ultimate KAES"];
function updateLevels(){
  let level = Math.floor(data.coins/50)+1; if(level>10) level=10;
  document.getElementById("levelDisplay").innerText="Level "+level+" — "+titles[level-1];
}
updateLevels();

// ==== CLICK HEART GAME ====
function startHearts(){
  let area = document.getElementById("gameArea"); area.innerHTML="";
  for(let i=0;i<10;i++){
    let h = document.createElement("div");
    h.innerText="💖"; h.style.position="absolute"; h.style.left=Math.random()*90+"%";
    h.style.top=Math.random()*150+"px"; h.style.fontSize="25px"; h.style.cursor="pointer";
    h.onclick=function(){ data.coins+=5; updateDisplay(); updateLevels(); saveData(); h.remove(); };
    area.appendChild(h);
  }
}

// ==== CATCH THE FALLING HEART GAME ====
function startCatchGame(){
  let area = document.getElementById("catchArea"); area.innerHTML="";
  for(let i=0;i<10;i++){
    let h=document.createElement("div"); h.innerText="💖"; 
    h.style.position="absolute"; h.style.left=Math.random()*90+"%"; h.style.top="0px"; h.style.fontSize="25px"; h.style.cursor="pointer";
    h.onclick=function(){ data.coins+=10; updateDisplay(); updateLevels(); saveData(); h.remove(); };
    area.appendChild(h);
    let fall=setInterval(()=>{
      let top=parseInt(h.style.top);
      if(top>=180){ h.remove(); clearInterval(fall); } 
      else{ h.style.top=top+2+"px"; }
    },20);
  }
}

// ==== QUIZZES ====
function createQuiz(container,q,answers,correct,badge){
  let div = document.getElementById(container); div.innerHTML="<p>"+q+"</p>";
  answers.forEach((ans,i)=>{
    let btn = document.createElement("button");
    btn.innerText=ans; btn.className="choiceBtn";
    btn.onclick=function(){
      if(i===correct){
        data.coins+=20; updateDisplay(); updateLevels();
        if(!data.badges.includes(badge)) data.badges.push(badge);
        saveData();
        div.innerHTML="✅ Correct! Badge "+badge+" earned!";
      }else{ div.innerHTML="❌ Wrong! Try again!"; }
    };
    div.appendChild(btn);
  });
}

// QUIZ DATA
createQuiz("quiz1","What is Karlyn's fav group?",["Katseye","Blackpink","IVE"],0,"☁️");
createQuiz("quiz2","What colour does Alyssa love?",["Blue","Pink","Purple"],1,"🎀");
createQuiz("quiz3","What does Trixie love wearing?",["Wushu pants","Jeans","Skirts"],0,"🥟");
</script>

<!-- SHOP PAGE -->
<div id="shop" class="page">
<h2>🛍️ K-Hearts Shop</h2>
<p>Spend your coins to unlock outfits, hairstyles, accessories, and your pink lightstick!</p>
<div id="shopItems"></div>
</div>

<script>
// ==== BADGES ARRAY ====
if(!data.badges) data.badges=[];

// ==== SHOP ITEMS ====
const shopList = [
  {name:"Pink Lightstick", type:"accessory", price:50, symbol:"✨"},
  {name:"Casual Outfit", type:"outfit", price:30, color:"#ffc0cb"},
  {name:"Stage Outfit", type:"outfit", price:50, color:"#ff66b2"},
  {name:"Ponytail Hair", type:"hair", price:20, color:"#ffb3e6"},
  {name:"Short Hair", type:"hair", price:15, color:"#ff99cc"},
  {name:"Bow Accessory", type:"accessory", price:15, symbol:"🎀"},
  {name:"Penguin Plush", type:"accessory", price:10, symbol:"🐧"},
  {name:"Water Bottle", type:"accessory", price:5, symbol:"💧"}
];

// ==== DISPLAY SHOP ====
function displayShop(){
  let div=document.getElementById("shopItems"); div.innerHTML="";
  shopList.forEach((item,i)=>{
    let btn=document.createElement("button");
    btn.innerText=item.name+" - "+item.price+" coins";
    btn.style.margin="5px";
    btn.onclick=function(){buyItem(i);};
    div.appendChild(btn);
  });
}

// ==== BUY ITEM ====
function buyItem(index){
  let item = shopList[index];
  if(data.coins>=item.price){
    data.coins-=item.price;
    if(item.type=="outfit"){ data.outfit=item.name; data.avatar.torso=item.color; data.avatar.bottom=item.color; }
    if(item.type=="hair"){ data.avatar.hair=item.color; data.hairstyle=item.name; }
    if(item.type=="accessory"){ data.avatar.accessory=item.symbol; }
    updateDisplay(); updateLevels(); saveData();
    alert("Purchased "+item.name+"!");
  }else{ alert("Not enough coins!"); }
}
displayShop();
</script>

<!-- NO LIMITS LYRICS PAGE -->
<div id="lyricsPage" class="page">
<h2>🎵 No Limits Lyrics</h2>
<p>Click a line to make it glow ✨</p>
<div id="lyricsArea"></div>
</div>

<!-- FAN CHAT PAGE -->
<div id="chatPage" class="page">
<h2>💌 Chat with K-Hearts</h2>
<div id="chatWindow" style="height:200px;overflow-y:auto;border:1px solid pink;padding:5px;background:#ffe6f0;"></div>
<input type="text" id="chatInput" placeholder="Say something to K-Hearts..." style="width:70%;">
<button onclick="sendMessage()">Send</button>
</div>

<!-- LEADERBOARD PAGE -->
<div id="leaderboard" class="page">
<h2>🏆 KAES Leaderboard</h2>
<p>Your username and coins are saved. Compete with other KAES!</p>
<div id="board"></div>
</div>

<script>
// ==== NO LIMITS LYRICS ====
const lyricsText=[
"No limits","No pressure","No ceiling","We go up",
"Walk in like a headline, cameras all flash",
"Step so sharp, make the whole world crash",
"Different languages, same ambition","Born to win — that’s the only mission",
"Mirror mirror, we don’t compete","We break the glass in designer feet",
"No permission, we elevate","Watch how legends are made",
"We don’t bend, we don’t break","Pressure turns to diamonds in our wake",
"Every scar is a shining mark","Strike a match — ignite the dark",
"We go higher, higher","Touch the sky, no ceiling",
"Fearless fire, fire","Got the whole world feeling",
"No doubts, no fear","We came too far to disappear",
"Global girls, we redefine","Step aside — the crown is mine",
"Runway rebel, spotlight glow","Soft but savage, let them know",
"From every city we ignite","Day one queens, built for the fight",
"Whispers turning into cheers","We turned pain into premiere",
"Every stage, every scene","We don’t follow — we lead",
"Too real, too bold","Too young, too gold",
"They said slow down — we said watch this","Turn small talk into big wins",
"No limits, we begin again","Up and up, we never end"
];

let lyricsArea=document.getElementById("lyricsArea");
lyricsText.forEach(line=>{
  let span=document.createElement("div");
  span.innerHTML="<span>"+line+"</span>";
  span.style.cursor="pointer";
  span.onclick=function(){span.classList.toggle("glow");};
  lyricsArea.appendChild(span);
});

// ==== FAN CHAT ====
  <!-- CHAT -->
<div id="chatPage" class="page">
<h2>💬 KAES Chat with Idols</h2>
<div id="chatWindow" style="height:200px;overflow-y:scroll;background:#fff0f5;padding:10px;border:2px solid #ffb6c1;border-radius:10px;"></div>
<input type="text" id="chatInput" placeholder="Type your message..." style="width:70%;">
<button onclick="sendMessage()">Send</button>
</div>

<!-- DAILY LEADERBOARD -->
<div id="dailyLeaderboardPage" class="page">
<h2>🏅 Daily Leaderboard</h2>
<p>Top KAES fans today!</p>
<div id="dailyBoard"></div>
</div>

<script>
// ==== SETUP LOCAL STORAGE DATA ====
if(!localStorage.getItem('kheartsData')){
  localStorage.setItem('kheartsData',JSON.stringify({username:'',coins:0,badges:[],chat:[],daily:[{name:'?',coins:0},{name:'?',coins:0},{name:'?',coins:0}]}));
}
let data=JSON.parse(localStorage.getItem('kheartsData'));

// ==== CHAT FUNCTIONS ====
function updateChatWindow(){
  let chatWin=document.getElementById('chatWindow');
  chatWin.innerHTML='';
  data.chat.forEach(msg=>{
    let p=document.createElement('p'); p.innerHTML=msg; chatWin.appendChild(p);
  });
  chatWin.scrollTop=chatWin.scrollHeight;
}
function sendMessage(){
  let input=document.getElementById('chatInput');
  if(input.value.trim()===''){return;}
  let userMsg="<b>"+(data.username||'Guest')+":</b> "+input.value;
  data.chat.push(userMsg);

  // Idol responses (randomized)
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
function saveData(){ localStorage.setItem('kheartsData',JSON.stringify(data)); }

// ==== DAILY LEADERBOARD FUNCTIONS ====
function updateDailyLeaderboard(){
  let board=document.getElementById('dailyBoard');
  board.innerHTML='';
  // Sort daily by coins
  data.daily.sort((a,b)=>b.coins-a.coins);
  data.daily.forEach((player,i)=>{
    let p=document.createElement('p');
    p.innerText=(i+1)+". "+player.name+" — "+player.coins+" coins";
    board.appendChild(p);
  });
}

// ==== ADD/UPDATE DAILY SCORES ====
function submitDailyScore(name,coins){
  if(!name) name='Guest';
  let existing=data.daily.find(p=>p.name===name);
  if(existing){ existing.coins=coins; } 
  else{ data.daily.push({name:name,coins:coins}); }
  saveData(); updateDailyLeaderboard();
}

// ==== EXAMPLE USAGE ====
// Prompt for username if not set
if(!data.username){
  data.username=prompt("Enter your KAES fan name:");
  saveData();
}

// Initialize chat and leaderboard
updateChatWindow();
updateDailyLeaderboard();
</script>
if(!data.chatHistory) data.chatHistory=[];
const responses = [
  "✨ KAES love your energy!",
  "💖 Keep shining, "+data.username+"!",
  "🌸 That outfit looks amazing!",
  "☁️ We noticed your coins, keep going!",
  "🎀 You're our top fan today!",
  "🥟 Stay strong, KAES is always here!"
];

function sendMessage(){
  let input=document.getElementById("chatInput");
  if(input.value.trim()=="") return;
  let chatWin=document.getElementById("chatWindow");
  let msgDiv=document.createElement("div");
  msgDiv.innerHTML="<b>"+data.username+":</b> "+input.value;
  chatWin.appendChild(msgDiv);
  // Member response
  let r=responses[Math.floor(Math.random()*responses.length)];
  let respDiv=document.createElement("div");
  respDiv.innerHTML="<b>K-Hearts:</b> "+r;
  respDiv.style.color="#ff66b2";
  chatWin.appendChild(respDiv);
  chatWin.scrollTop=chatWin.scrollHeight;
  data.chatHistory.push({user:input.value,response:r});
  saveData();
  input.value="";
}

// ==== LEADERBOARD ====
function displayLeaderboard(){
  let board=document.getElementById("board");
  board.innerHTML="<p>"+data.username+" — "+data.coins+" coins</p>";
  // Normally we’d show global leaderboard, but localStorage demo only shows this player
}
displayLeaderboard();

// ==== MINI-GAME: Fashion Match ====
function miniFashionMatch(){
  // Could be added later: matching items for coins
  // Placeholder for extra games
}
</script>

<style>
.glow{color:#ff66b2;font-weight:bold;text-shadow:2px 2px 5px #fff;}
</style>

<!-- MUSIC & FAN REVEAL -->
<div id="musicPage" class="page">
<h2>🎶 Background Music</h2>
<button onclick="toggleMusic()">Play / Pause “No Limits”</button>
<audio id="bgMusic" src="no_limits_instrumental.mp3" preload="auto"></audio>

<h2>💖 Fandom Name Reveal</h2>
<p id="fandomReveal" style="font-size:30px;color:#ff66b2;">✨ Click to reveal! ✨</p>
<button onclick="revealFandom()">Reveal KAES 💗</button>
</div>

<!-- DAILY BONUS -->
<div id="bonusPage" class="page">
<h2>🎁 Daily Bonus</h2>
<p>Claim your daily coins!</p>
<button onclick="claimBonus()">Claim Bonus</button>
<p id="bonusMessage"></p>
</div>

<!-- SCREENSHOT -->
<div id="screenshotPage" class="page">
<h2>📸 Screenshot Your Avatar</h2>
<p>Use your device screenshot to save your avatar & outfit!</p>
</div>

<script>
// ==== MUSIC ====
let music=document.getElementById("bgMusic");
function toggleMusic(){if(music.paused) music.play(); else music.pause();}

// ==== FANDOM REVEAL ====
function revealFandom(){
  let p=document.getElementById("fandomReveal");
  p.innerHTML="💖 KAES 💖";
  p.style.animation="sparkle 2s ease infinite";
}
let style=document.createElement("style");
style.innerHTML="@keyframes sparkle{0%{text-shadow:0 0 2px #fff;}50%{text-shadow:0 0 20px #fff;}100%{text-shadow:0 0 2px #fff;}}";
document.head.appendChild(style);

// ==== DAILY BONUS ====
function claimBonus(){
  let today=new Date().toDateString();
  if(data.lastBonus===today){document.getElementById("bonusMessage").innerText="Already claimed today!"; return;}
  let coinsEarned=Math.floor(Math.random()*20)+10;
  data.coins+=coinsEarned; data.lastBonus=today; updateDisplay(); updateLevels(); saveData();
  document.getElementById("bonusMessage").innerText="You earned "+coinsEarned+" coins today! 💖";
}

// ==== ADD NAV BUTTONS FOR NEW PAGES ====
let nav=document.querySelector("nav");
["Games","Shop","Lyrics","Chat","Leaderboard","Music","Daily Bonus","Screenshot"].forEach((page,i)=>{
  let btn=document.createElement("button");
  btn.innerText=page;
  btn.onclick=function(){showPage(page.toLowerCase().replace(/ /g,""))};
  nav.appendChild(btn);
});
</script>

<!-- FULL OUTFITS & PETS -->
<div id="extrasPage" class="page">
<h2>👗 Outfits & Pets</h2>
<p>Customize your full-body avatar with layered outfits and cute pets! 🐧🐱</p>
<button onclick="togglePet('penguin')">Toggle Penguin 🐧</button>
<button onclick="togglePet('kitten')">Toggle Kitten 🐱</button>

<h2>🎵 Rhythm Tap Game</h2>
<p>Tap the hearts to the beat of No Limits!</p>
<button onclick="startRhythmGame()">Start Rhythm Game</button>
<div id="rhythmArea" style="position:relative;width:100%;height:200px;"></div>

<h2>🎤 Stage Performance</h2>
<p>Click perform to see your avatar dance on stage!</p>
<button onclick="performStage()">Perform</button>
<div id="stageArea" style="position:relative;width:100%;height:250px;background:#ffe6f0;"></div>
</div>

<script>
// ==== PETS ====
if(!data.pets) data.pets={penguin:false,kitten:false};
function togglePet(type){
  data.pets[type]=!data.pets[type]; saveData(); updateAvatarPets();
}
function updateAvatarPets(){
  let hand=document.getElementById("handAccessory");
  hand.innerText="";
  if(data.avatar.accessory) hand.innerText+=data.avatar.accessory;
  if(data.pets.penguin) hand.innerText+=" 🐧";
  if(data.pets.kitten) hand.innerText+=" 🐱";
}
updateAvatarPets();

// ==== RHYTHM TAP GAME ====
function startRhythmGame(){
  let area=document.getElementById("rhythmArea"); area.innerHTML="";
  for(let i=0;i<10;i++){
    let h=document.createElement("div"); h.innerText="💖";
    h.style.position="absolute"; h.style.left=Math.random()*90+"%"; h.style.top="0px"; h.style.fontSize="30px"; h.style.cursor="pointer";
    h.onclick=function(){ data.coins+=15; updateDisplay(); updateLevels(); saveData(); h.remove(); };
    area.appendChild(h);
    let fall=setInterval(()=>{
      let top=parseInt(h.style.top); if(top>=180){ h.remove(); clearInterval(fall); } else{ h.style.top=top+4+"px"; }
    },20);
  }
}

// ==== STAGE PERFORMANCE ====
function performStage(){
  let stage=document.getElementById("stageArea"); stage.innerHTML="";
  let avatarClone=document.querySelector(".avatar-container").cloneNode(true);
  avatarClone.style.position="absolute"; avatarClone.style.left="40%"; avatarClone.style.top="20px";
  stage.appendChild(avatarClone);
  avatarClone.style.animation="dance 1s ease infinite alternate";
}
let style2=document.createElement("style");
style2.innerHTML="@keyframes dance{0%{transform:translateY(0px) rotate(0deg);}50%{transform:translateY(-10px) rotate(5deg);}100%{transform:translateY(0px) rotate(-5deg);}}";
document.head.appendChild(style2);

// ==== EXTRA CHAT PERSONALIZATION ====
responses.push(
  "☁️ Karlyn notices your outfit!",
  "🎀 Alyssa loves your pink vibes!",
  "🥟 Trixie is cheering for you!"
);
</script>

<!-- EXTRA OUTFITS & STAGE PROPS -->
<div id="extras2Page" class="page">
<h2>🎀 Extra Outfits & Stage Props</h2>
<p>Unlock more outfits, props, and accessories for your avatar!</p>
<button onclick="buyExtraOutfit('Glitter Dress',40,'#ff99ff')">Glitter Dress - 40 coins</button>
<button onclick="buyExtraOutfit('Comfy Hoodie',20,'#ffb6c1')">Comfy Hoodie - 20 coins</button>
<button onclick="buyExtraProp('Lightstick Pink',30,'✨')">Lightstick Pink - 30 coins</button>
<button onclick="buyExtraProp('Stage Microphone',25,'🎤')">Stage Microphone - 25 coins</button>
</div>

<script>
// ==== EXTRA OUTFITS / PROPS ====
function buyExtraOutfit(name,price,color){
  if(data.coins>=price){
    data.coins-=price; data.outfit=name; data.avatar.torso=color; data.avatar.bottom=color;
    updateDisplay(); updateLevels(); saveData(); alert("Purchased "+name+"!");
  } else{ alert("Not enough coins!"); }
}
function buyExtraProp(name,price,symbol){
  if(data.coins>=price){
    data.coins-=price; data.avatar.accessory=symbol;
    updateDisplay(); updateLevels(); saveData(); alert("Purchased "+name+"!");
  } else{ alert("Not enough coins!"); }
}

// ==== ANIMATED LIGHTSTICK EFFECT ====
let lightstickInterval;
function startLightstick(){
  let hand=document.getElementById("handAccessory");
  if(data.avatar.accessory==="✨"){
    let toggle=true;
    lightstickInterval=setInterval(()=>{
      hand.style.color=toggle?"#ff66b2":"#fff";
      toggle=!toggle;
    },400);
  }
}
function stopLightstick(){clearInterval(lightstickInterval); hand.style.color="#000";}

// ==== HUNDREDS OF NON-REPEATING CHAT RESPONSES ====
const extraResponses=[
"💖 You're glowing today, "+data.username+"!",
"🌸 Karlyn loves your vibe!",
"☁️ Alyssa noticed your coins, amazing!",
"🎀 Trixie is cheering for your outfit!",
"✨ Keep stacking those badges!",
"🥟 Your pets are adorable!",
"💗 Stage performance is perfect!",
"🌟 KAES universe shines brighter with you!",
"🎶 Your rhythm tap skills are amazing!",
"💞 We see your hard work and dedication!",
"💖 Keep up the energy, "+data.username+"!",
"☁️ Karlyn says hello!",
"🎀 Alyssa waves at you!",
"🥟 Trixie claps for you!",
"✨ Coins rain from the sky for you!",
"🌸 Your avatar looks fab today!",
"💗 Keep dancing, never stop!",
"🎶 No Limits! Feel the beat!",
"💞 You're top fan material!",
"🌟 Stage lights sparkle for you!"
];

// Add to main responses array
responses.push(...extraResponses);
</script>

<!-- SEASONAL EVENTS -->
<div id="eventsPage" class="page">
<h2>🎉 Seasonal Events</h2>
<p>Special outfits and props appear during events!</p>
<button onclick="activateEvent('Halloween')">🎃 Halloween Event</button>
<button onclick="activateEvent('Valentine')">💖 Valentine Event</button>
<button onclick="activateEvent('Winter')">❄️ Winter Event</button>
<div id="eventItems"></div>
</div>

<!-- GLOBAL LEADERBOARD -->
<div id="globalLeaderboardPage" class="page">
<h2>🌍 Global Leaderboard</h2>
<p>Top 5 KAES fans based on coins & achievements!</p>
<div id="globalBoard"></div>
</div>

<script>
// ==== SEASONAL EVENTS ====
function activateEvent(eventName){
  let items=document.getElementById("eventItems");
  items.innerHTML="";
  if(eventName==="Halloween"){
    items.innerHTML="<p>🎃 Pumpkin Hat - 50 coins</p><p>🕸️ Spider Accessory - 30 coins</p>";
  } else if(eventName==="Valentine"){
    items.innerHTML="<p>💘 Heart Wings - 50 coins</p><p>🍫 Chocolate Prop - 30 coins</p>";
  } else if(eventName==="Winter"){
    items.innerHTML="<p>❄️ Snow Hoodie - 50 coins</p><p>☃️ Snowball Accessory - 30 coins</p>";
  }
  alert(eventName+" event is now active! Collect special items!");
}

// ==== GLOBAL LEADERBOARD ====
// Demo: For now, localStorage stores only this user
function displayGlobalLeaderboard(){
  let board=document.getElementById("globalBoard");
  board.innerHTML="<p>1. "+data.username+" — "+data.coins+" coins</p>";
  board.innerHTML+="<p>2. ??? — ??? coins</p>";
  board.innerHTML+="<p>3. ??? — ??? coins</p>";
  board.innerHTML+="<p>4. ??? — ??? coins</p>";
  board.innerHTML+="<p>5. ??? — ??? coins</p>";
}
displayGlobalLeaderboard();
</script>

<!-- FAN MISSIONS -->
<div id="missionsPage" class="page">
<h2>📝 Fan Missions</h2>
<p>Complete missions to earn extra coins and badges!</p>
<ul>
  <li>Play 3 games 💖 — earn 20 coins</li>
  <li>Buy an outfit 🛍️ — earn 15 coins</li>
  <li>Complete all quizzes ☁️🎀🥟 — earn badge combo</li>
</ul>
<button onclick="completeMissions()">Complete Mission</button>
<p id="missionMsg"></p>
</div>

<!-- EASTER EGG OUTFITS -->
<div id="easterEggPage" class="page">
<h2>🎁 Easter Egg Outfits & Props</h2>
<p>Find hidden items to unlock secret outfits & accessories!</p>
<button onclick="unlockEasterEgg('Secret Glitter')">Unlock Secret Glitter Outfit - 100 coins</button>
<button onclick="unlockEasterEgg('Mystery Pet')">Unlock Mystery Pet - 50 coins</button>
</div>

<!-- MUSIC RHYTHM MINI-GAME -->
<div id="beatGamePage" class="page">
<h2>🎵 Beat-Synced Mini-Game</h2>
<p>Tap the hearts exactly on the beat to earn bonus coins!</p>
<button onclick="startBeatGame()">Start Beat Game</button>
<div id="beatArea" style="position:relative;width:100%;height:200px;"></div>
</div>

<script>
// ==== FAN MISSIONS ====
function completeMissions(){
  let coinsEarned=0;
  if(!data.missionsCompleted) data.missionsCompleted=[];
  if(!data.missionsCompleted.includes("play3games")) { coinsEarned+=20; data.missionsCompleted.push("play3games"); }
  if(!data.missionsCompleted.includes("buyOutfit")) { coinsEarned+=15; data.missionsCompleted.push("buyOutfit"); }
  if(!data.missionsCompleted.includes("allQuizzes")) { coinsEarned+=30; data.missionsCompleted.push("allQuizzes"); data.badges.push("☁️🎀🥟"); }
  data.coins+=coinsEarned; updateDisplay(); updateLevels(); saveData();
  document.getElementById("missionMsg").innerText="You earned "+coinsEarned+" coins for completing missions!";
}

// ==== EASTER EGGS ====
function unlockEasterEgg(item){
  if(item==="Secret Glitter"){ data.coins-=100; data.outfit="Secret Glitter"; data.avatar.torso="#ff66ff"; data.avatar.bottom="#ff66ff"; alert("Secret Glitter Outfit unlocked!"); }
  if(item==="Mystery Pet"){ data.coins-=50; data.avatar.accessory="🦄"; alert("Mystery Pet unlocked! 🦄"); }
  updateDisplay(); updateLevels(); saveData();
}

// ==== BEAT GAME ====
function startBeatGame(){
  let area=document.getElementById("beatArea"); area.innerHTML="";
  for(let i=0;i<15;i++){
    let h=document.createElement("div"); h.innerText="💖"; 
    h.style.position="absolute"; h.style.left=Math.random()*90+"%"; h.style.top="0px"; h.style.fontSize="30px"; h.style.cursor="pointer";
    h.onclick=function(){ data.coins+=20; updateDisplay(); updateLevels(); saveData(); h.remove(); };
    area.appendChild(h);
    let fall=setInterval(()=>{
      let top=parseInt(h.style.top); if(top>=180){ h.remove(); clearInterval(fall); } else{ h.style.top=top+5+"px"; }
    },16);
  }
}

// ==== ADVANCED CHAT RESPONSES BASED ON AVATAR & COINS ====
function getAdvancedResponse(){
  let msgs=[
    "💖 "+data.username+", your avatar looks amazing with "+data.outfit+"!",
    "☁️ Karlyn says: Loving your coins, keep stacking!",
    "🎀 Alyssa noticed your pets! So cute!",
    "🥟 Trixie cheers for your stage performance!"
  ];
  if(data.coins>100) msgs.push("✨ Wow "+data.username+", you're a top collector!");
  if(data.avatar.accessory==="✨") msgs.push("💗 Lightstick is glowing perfectly for the concert!");
  return msgs[Math.floor(Math.random()*msgs.length)];
}
// Example usage in chat: responses.push(getAdvancedResponse());
responses.push(getAdvancedResponse());
</script>

<!-- CONCERT STAGE -->
<div id="concertPage" class="page">
<h2>🎆 Animated Concert Stage</h2>
<p>Watch your avatar perform on a full animated stage with pulsing lights!</p>
<button onclick="startConcert()">Start Concert</button>
<div id="concertStage" style="position:relative;width:100%;height:300px;background:#ffe6f0;overflow:hidden;"></div>
</div>

<!-- DANCE BATTLE -->
<div id="danceBattlePage" class="page">
<h2>💃 Avatar Dance Battle</h2>
<p>Challenge AI idols and earn coins & badges!</p>
<button onclick="startDanceBattle()">Start Dance Battle</button>
<div id="battleArea" style="position:relative;width:100%;height:250px;background:#fff0f5;"></div>
</div>

<!-- WEEKLY FAN REWARDS -->
<div id="weeklyRewardsPage" class="page">
<h2>🏆 Weekly Top Fan Rewards</h2>
<p>Check back weekly to see if you're a top KAES fan!</p>
<div id="weeklyRewardArea"></div>
</div>

<script>
// ==== CONCERT STAGE ====
function startConcert(){
  let stage=document.getElementById("concertStage"); stage.innerHTML="";
  let avatarClone=document.querySelector(".avatar-container").cloneNode(true);
  avatarClone.style.position="absolute"; avatarClone.style.left="40%"; avatarClone.style.top="50px";
  stage.appendChild(avatarClone);

  // Add pulsing lights
  for(let i=0;i<5;i++){
    let light=document.createElement("div"); light.style.position="absolute";
    light.style.width="20px"; light.style.height="20px"; light.style.borderRadius="50%";
    light.style.background="#ff66b2"; light.style.left=(i*18)+"%"; light.style.top="250px";
    stage.appendChild(light);
    setInterval(()=>{light.style.background=light.style.background=="#ff66b2"?"#ffc0cb":"#ff66b2";},500);
  }

  avatarClone.style.animation="dance 1s ease infinite alternate";
}

// ==== DANCE BATTLE ====
function startDanceBattle(){
  let area=document.getElementById("battleArea"); area.innerHTML="";
  // Player avatar
  let player=document.querySelector(".avatar-container").cloneNode(true);
  player.style.position="absolute"; player.style.left="20%"; player.style.top="50px"; area.appendChild(player);
  player.style.animation="dance 1s ease infinite alternate";
  
  // AI Idol avatar
  let ai=document.createElement("div"); ai.innerText="🤖"; ai.style.position="absolute"; ai.style.left="70%"; ai.style.top="50px"; ai.style.fontSize="50px"; area.appendChild(ai);
  
  // Simple outcome
  let win=Math.random()>0.5;
  setTimeout(()=>{
    if(win){ data.coins+=50; data.badges.push("🏅Dance Battle Winner"); updateDisplay(); updateLevels(); saveData(); alert("You WON the dance battle! +50 coins and a badge!"); }
    else{ alert("You lost! Try again to earn more coins."); }
  },3000);
}

// ==== WEEKLY FAN REWARDS ====
function displayWeeklyRewards(){
  let area=document.getElementById("weeklyRewardArea"); area.innerHTML="";
  let rewards=["💖 Extra 50 coins","🎀 Exclusive Outfit","☁️ Special Pet","✨ Lightstick Animation Upgrade"];
  rewards.forEach((r,i)=>{ area.innerHTML+="<p>"+(i+1)+". "+r+"</p>"; });
}
displayWeeklyRewards();
</script>

<!-- MOBILE-FRIENDLY NAV -->
<nav id="mainNav" style="display:flex;flex-wrap:wrap;gap:5px;background:#ffb6c1;padding:5px;justify-content:center;"></nav>

<!-- CONFETTI CANVAS -->
<canvas id="confettiCanvas" style="position:absolute;top:0;left:0;width:100%;height:100%;pointer-events:none;"></canvas>

<script>
// ==== MOBILE-FRIENDLY PAGE SHOW ====
function showPage(pageId){
  document.querySelectorAll('.page').forEach(p=>{p.style.display='none';p.style.opacity=0;});
  let page=document.getElementById(pageId);
  if(page){ page.style.display='block'; fadeIn(page); }
}

function fadeIn(el){
  let op=0; let timer=setInterval(()=>{ if(op>=1){clearInterval(timer);} else{ op+=0.05; el.style.opacity=op; }},20);
}

// ==== FAN ACHIEVEMENT NOTIFICATIONS ====
function showAchievement(msg){
  let notif=document.createElement('div');
  notif.innerText=msg;
  notif.style.position='fixed'; notif.style.top='10px'; notif.style.right='10px';
  notif.style.background='#ff66b2'; notif.style.color='#fff'; notif.style.padding='10px'; notif.style.borderRadius='10px';
  notif.style.zIndex=9999; notif.style.boxShadow='0 0 10px #fff';
  document.body.appendChild(notif);
  setTimeout(()=>{notif.remove();},3000);
}

// Example: show achievement when earning badge
function earnBadge(badge){
  if(!data.badges.includes(badge)){ data.badges.push(badge); saveData(); showAchievement("🏅 Badge Earned: "+badge); }
}

// ==== CONFETTI ANIMATION ====
const canvas=document.getElementById('confettiCanvas');
const ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;
let confetti=[]; 
function createConfetti(){for(let i=0;i<100;i++){confetti.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*6+2,dx:(Math.random()-0.5)*2,dy:Math.random()*3+2,color:`hsl(${Math.random()*360},100%,70%)`});}}
function drawConfetti(){ctx.clearRect(0,0,canvas.width,canvas.height); confetti.forEach(c=>{ctx.fillStyle=c.color;ctx.beginPath();ctx.arc(c.x,c.y,c.r,0,2*Math.PI);ctx.fill();c.x+=c.dx;c.y+=c.dy;if(c.y>canvas.height){c.y=0;c.x=Math.random()*canvas.width;}}); requestAnimationFrame(drawConfetti);}
createConfetti(); drawConfetti();

// ==== ADJUST ON RESIZE ====
window.addEventListener('resize',()=>{canvas.width=window.innerWidth;canvas.height=window.innerHeight;});

// ==== EXAMPLES OF ACHIEVEMENTS ====
if(!data.achievements) data.achievements=[];
function checkAchievements(){
  if(data.coins>=100 && !data.achievements.includes('100 Coins')){
    data.achievements.push('100 Coins'); saveData(); showAchievement("💖 Achievement Unlocked: 100 Coins!");
  }
  if(data.badges.length>=5 && !data.achievements.includes('5 Badges')){
    data.achievements.push('5 Badges'); saveData(); showAchievement("🎀 Achievement Unlocked: 5 Badges!");
  }
}
setInterval(checkAchievements,3000);
</script>
