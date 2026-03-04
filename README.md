<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>K-Hearts Ultimate</title>
<style>
body{
  margin:0;
  font-family:"Comic Sans MS",cursive;
  background:linear-gradient(#ffd6ec,#ffc0e6);
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
.card{
  background:white;
  border-radius:20px;
  padding:15px;
  margin:10px auto;
  width:300px;
}
.pet-area{
  font-size:80px;
  position:relative;
  height:160px;
}
.layer{
  position:absolute;
  left:50%;
  transform:translateX(-50%);
}
#hat{top:0;font-size:40px;}
#collar{top:75px;font-size:30px;}
#toy{top:100px;font-size:40px;}
.chat-box{
  height:220px;
  overflow:auto;
  border:2px solid pink;
  background:white;
  padding:10px;
  text-align:left;
  border-radius:15px;
}
input{
  padding:8px;
  border-radius:10px;
  border:1px solid pink;
}
</style>
</head>

<body>
<h1>💖 K-HEARTS WORLD 💖</h1>

<div id="login">
  <h3>Enter your Kaes name:</h3>
  <input id="nameInput">
  <button onclick="start()">Enter</button>
</div>

<div id="main" style="display:none;">
<p>Fandom: 💖 Kaes 💖</p>
<p>Coins: <span id="coins">100</span> 💰</p>
<p>Happiness: <span id="happy">70</span> 💕</p>
<p>Health: <span id="health">100</span> ❤️</p>
<button onclick="feed()">Feed (-5 coins)</button>
<br>
<button onclick="show('home')">Home</button>
<button onclick="show('members')">Members</button>
<button onclick="show('pets')">Pets</button>
<button onclick="show('games')">Games</button>
<button onclick="show('chat')">AI Chat</button>
<button onclick="show('leaderboard')">Leaderboard</button>
<button onclick="show('lyrics')">Lyrics</button>

<!-- HOME -->
<div id="home" class="section active">
<h2>Welcome <span id="player"></span> 💕</h2>
<p>Future global queens 👑</p>
</div>

<!-- MEMBERS -->
<div id="members" class="section">
<h2>Members</h2>
<div class="card"><b>Karlyn</b> – Leader, Main Rapper, Lead Dancer, Sub Vocalist</div>
<div class="card"><b>Trixie</b> – Centre, Sub Rapper, Main Dancer, Sub Vocalist</div>
<div class="card"><b>Hayley</b> – Lead Dancer, Lead Vocalist, Maknae</div>
<div class="card"><b>Alyssa</b> – Main Vocalist, Visual, Sub Rapper, Sub Dancer</div>
</div>

<!-- PETS -->
<div id="pets" class="section">
<h2>Your Pet</h2>
<button onclick="choosePet('🐶')">Dog</button>
<button onclick="choosePet('🐱')">Cat</button>
<button onclick="choosePet('🐧')">Penguin</button>
<div class="pet-area">
<div id="pet">🐶</div>
<div id="hat" class="layer"></div>
<div id="collar" class="layer"></div>
<div id="toy" class="layer"></div>
</div>
<h3>Shop</h3>
<button onclick="buy('hat','🎀',20)">Bow</button>
<button onclick="buy('hat','👑',30)">Crown</button>
<button onclick="buy('collar','💎',15)">Diamond</button>
<button onclick="buy('collar','🌸',15)">Flower</button>
<button onclick="buy('toy','⚽',10)">Ball</button>
<button onclick="buy('toy','🧸',15)">Teddy</button>
<button onclick="buy('toy','🦴',10)">Bone</button>
<br>
<button onclick="play()">Play (+5)</button>
<button onclick="bathe()">Bathe 🛁</button>
</div>

<!-- GAMES -->
<div id="games" class="section">
<h2>Games</h2>
<button onclick="tap()">Tap (+5)</button>
<button onclick="spin()">Spin</button>
<button onclick="multiply()">Multiply Quiz</button>
<button onclick="addition()">Addition Quiz</button>
<button onclick="spelling()">Spelling Quiz</button>
<button onclick="logic()">Logic Quiz</button>
<button onclick="science()">Science Quiz</button>
</div>

<!-- CHAT -->
<div id="chat" class="section">
<h2>K-Hearts AI</h2>
<div class="chat-box" id="chatBox"></div>
<input id="chatInput">
<button onclick="send()">Send</button>
</div>

<!-- LEADERBOARD -->
<div id="leaderboard" class="section">
<h2>Leaderboard</h2>
<div id="board"></div>
</div>

<!-- LYRICS -->
<div id="lyrics" class="section">
<h2>NO LIMITS</h2>
<div style="background:white;padding:20px;border-radius:20px;text-align:left;max-height:450px;overflow:auto;line-height:1.7;font-size:15px;">

No limits<br>
No pressure<br>
No ceiling<br>
We go up<br><br>

Walk in like a headline, cameras all flash<br>
Step so sharp, make the whole world crash<br>
Different languages, same ambition<br>
Born to win — that’s the only mission<br><br>

Mirror mirror, we don’t compete<br>
We break the glass in designer feet<br>
No permission, we elevate<br>
Watch how legends are made<br><br>

We don’t bend, we don’t break<br>
Pressure turns to diamonds in our wake<br>
Every scar is a shining mark<br>
Strike a match — ignite the dark<br><br>

We go higher, higher<br>
Touch the sky, no ceiling<br>
Fearless fire, fire<br>
Got the whole world feeling<br><br>

No doubts, no fear<br>
We came too far to disappear<br>
Global girls, we redefine<br>
Step aside — the crown is mine<br><br>

Runway rebel, spotlight glow<br>
Soft but savage, let them know<br>
From every city we ignite<br>
Day one queens, built for the fight<br><br>

Whispers turning into cheers<br>
We turned pain into premiere<br>
Every stage, every scene<br>
We don’t follow — we lead<br><br>

Too real, too bold<br>
Too young, too gold<br>
They said slow down — we said watch this<br>
Turn small talk into a hit list<br><br>

Confidence loud, no apologies<br>
Breaking rules is our policy<br>
Future written in neon light<br>
We don’t knock — we own the night<br><br>

If they doubt us, let them talk<br>
We don’t walk — we skywalk<br>
Every fall just fuels the flame<br>
Say our names — remember the game<br><br>

We go higher, higher<br>
World on our shoulders shining<br>
Fearless fire, fire<br>
Perfect timing<br><br>

No glass left to break<br>
No crown left to take<br>
We don’t stop, we redefine<br>
No ceiling — we climb.

</div>
</div>

</div>

<script>
let coins=100;
let happiness=70;
let health=100;
let username="";

let responses=[
"Let’s break that down step by step.",
"What subject is this for?",
"Explain what you’ve tried so far.",
"You’re thinking in the right direction.",
"Try identifying the key concept.",
"Break it into smaller parts.",
"What’s the question REALLY asking?",
"You’ve got this.",
"Check your working carefully.",
"That’s interesting — tell me more.",
"Try to explain it in your own words.",
"Think about patterns you see.",
"Have you tried a different approach?",
"Focus on one step at a time.",
"Remember to double-check your answer.",
"Ask yourself what you know already.",
"Think logically before answering.",
"Keep calm and reason through it.",
"Imagine the problem visually.",
"Look for clues in the question.",
"Use what you learned before.",
"Don’t rush — step by step.",
"Visualize the solution in your mind.",
"Consider examples to guide you.",
"Take a deep breath, then solve.",
"Reflect on why it works that way.",
// JS-specific tips
"Ah! That sounds like JavaScript — try using console.log() to debug.",
"Loops are your friend! for, while, or do-while?",
"Remember: = is assignment, == or === is comparison.",
"Use functions to keep your code neat and reusable.",
"Try checking your brackets — those often break JS.",
"If your button isn’t working, make sure your onclick is correct.",
"Don’t forget semicolons! They can save headaches.",
"Use document.getElementById('id') to select elements.",
"Arrays start at index 0 in JS!",
"Try writing your code in smaller pieces first.",
"Variables can be let, const, or var — choose wisely.",
"Remember to check your console for errors!",
"Functions can return values — use that to store results.",
"Objects are amazing for grouping data together.",
"Event listeners help you make interactive elements.",
"Keep practicing! Small mistakes are normal in JS.",
"Debug step by step and you’ll find the bug.",
"Try searching MDN docs for any JS function you’re unsure of."
];

function start(){
 username=document.getElementById("nameInput").value;
 if(username==="") return;
 document.getElementById("player").innerText=username;
 document.getElementById("login").style.display="none";
 document.getElementById("main").style.display="block";
 updateStats();
 setInterval(()=>{health-=5;if(health<0)health=0;updateStats();},30000);
}

function show(id){
 document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
 document.getElementById(id).classList.add("active");
}

function updateStats(){
 document.getElementById("coins").innerText=coins;
 document.getElementById("happy").innerText=happiness;
 document.getElementById("health").innerText=health;
 document.getElementById("board").innerHTML=username+" — "+coins+" coins";
}

function choosePet(p){document.getElementById("pet").innerText=p;}

function buy(type,emoji,price){
 if(coins>=price){
  coins-=price;
  document.getElementById(type).innerText=emoji;
  updateStats();
 }
}

function play(){coins+=5; happiness+=5; updateStats();}
function bathe(){happiness+=10; health+=10; if(health>100)health=100; updateStats();}
function feed(){if(coins>=5){coins-=5; health+=15; if(health>100)health=100;} updateStats();}

function tap(){coins+=5; updateStats();}
function spin(){let w=Math.floor(Math.random()*30)+1; coins+=w; updateStats();}
function multiply(){let ans=prompt("7 x 8 = ?"); if(ans=="56"){coins+=20;} updateStats();}
function addition(){let ans=prompt("45 + 37 = ?"); if(ans=="82"){coins+=15;} updateStats();}
function spelling(){let ans=prompt("Spell: ambition"); if(ans&&ans.toLowerCase()=="ambition"){coins+=20;} updateStats();}
function logic(){let ans=prompt("If you take 2 apples from 3, how many do YOU have?"); if(ans=="2"){coins+=25;} updateStats();}
function science(){let ans=prompt("Planet we live on?"); if(ans&&ans.toLowerCase()=="earth"){coins+=20;} updateStats();}

function send(){
 let input=document.getElementById("chatInput").value;
 if(input==="") return;
 let box=document.getElementById("chatBox");
 box.innerHTML+="<p><b>"+username+":</b> "+input+"</p>";
 let reply="";
 let text=input.toLowerCase();

 // JS detection
 if(text.includes("js") || text.includes("javascript") || text.includes("button") || text.includes("loop") || text.includes("console") || text.includes("function")){
   reply = responses[Math.floor(Math.random()*(responses.length-15)+15)];
 } 
 else if(text.includes("math")||text.includes("+")||text.includes("x"))
   reply="Let’s solve it step by step. What numbers are we using?";
 else if(text.includes("sad")||text.includes("stress"))
   reply="I’m here for you 💖 What happened?";
 else if(text.includes("essay")||text.includes("write"))
   reply="Start with introduction, 3 key points, then conclusion.";
 else if(text.includes("?"))
   reply="Great question. Let’s think logically about it.";
 else
   reply=responses[Math.floor(Math.random()*15)];

 box.innerHTML+="<p><b>K-Hearts AI:</b> "+reply+"</p>";
 box.scrollTop=box.scrollHeight;
 document.getElementById("chatInput").value="";
}
</script>
</body>
</html>
