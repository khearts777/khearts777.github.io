<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>K-Hearts World</title>

<style>

body{
font-family:Arial;
background:linear-gradient(#ffd6f2,#ffc2e6);
text-align:center;
margin:0;
}

h1{color:#ff1493;}

button{
background:#ff69b4;
border:none;
padding:10px 16px;
margin:5px;
border-radius:15px;
color:white;
cursor:pointer;
}

.section{display:none;padding:20px;}
.active{display:block;}

.pet{
font-size:90px;
position:relative;
}

@keyframes walk{
0%{left:0}
50%{left:80px}
100%{left:0}
}

.walk{
animation:walk 6s infinite;
}

@keyframes bounce{
0%{transform:translateY(0)}
50%{transform:translateY(-25px)}
100%{transform:translateY(0)}
}

.playing{
animation:bounce 0.6s infinite;
}

.chatbox{
height:240px;
overflow:auto;
border:2px solid pink;
background:white;
border-radius:15px;
padding:10px;
text-align:left;
}

#gameArea{
width:320px;
height:320px;
background:white;
margin:auto;
border-radius:20px;
position:relative;
}

#coin{
position:absolute;
font-size:35px;
cursor:pointer;
}

</style>
</head>

<body>

<h1>💖 K-HEARTS WORLD 💖</h1>

<div id="login">
Enter your Kaes name:<br>
<input id="nameInput">
<button onclick="start()">Enter</button>
</div>

<div id="game" style="display:none">

<p>Coins: <span id="coins"></span></p>
<p>Health: <span id="health"></span></p>
<p>Mood: <span id="mood"></span></p>

<button onclick="show('home')">Home</button>
<button onclick="show('pets')">Pets</button>
<button onclick="show('games')">Games</button>
<button onclick="show('chat')">Chat</button>
<button onclick="show('members')">Members</button>
<button onclick="show('lyrics')">Lyrics</button>

<div id="home" class="section active">
<h2>Welcome <span id="player"></span> 💖</h2>
<p>K-Hearts official fan world</p>
</div>

<div id="pets" class="section">

<div id="pet" class="pet walk">🐶</div>

<p>Mood: <span id="petMood"></span></p>

<div id="speech" style="background:white;padding:10px;border-radius:15px;width:200px;margin:auto;">
Hi!
</div>

<br>

<button onclick="feed()">Feed</button>
<button onclick="bathe()">Bathe</button>
<button onclick="play()">Play</button>

<h3>Pet Shop</h3>

<button onclick="buyToy('⚽',10)">Ball</button>
<button onclick="buyToy('🧸',15)">Teddy</button>
<button onclick="buyToy('🦴',10)">Bone</button>

<div id="toy" style="font-size:40px"></div>

</div>

<div id="games" class="section">

<h3>Catch the Coin</h3>

<div id="gameArea">
<div id="coin">🪙</div>
</div>

<p>Score: <span id="score">0</span></p>

</div>

<div id="chat" class="section">

<div class="chatbox" id="chatbox"></div>

<input id="chatInput">
<button onclick="send()">Send</button>

</div>

<div id="members" class="section">

<h3>Members</h3>

<p>Karlyn — Leader, Main Rapper, Lead Dancer</p>
<p>Trixie — Center, Main Dancer</p>
<p>Hayley — Lead Vocalist, Maknae</p>
<p>Alyssa — Main Vocalist, Visual</p>

</div>

<div id="lyrics" class="section">

<h3>No Limits</h3>

<div style="background:white;padding:20px;border-radius:20px;text-align:left">

No limits  
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

No glass left to break  
No crown left to take  
We don’t stop, we redefine  
No ceiling — we climb.

</div>
</div>

</div>

<script>

let coins=100
let health=100
let username=""
let score=0

let responses=[
"Hi!",
"Hey!",
"What's up?",
"Tell me something interesting.",
"That's funny 😂",
"That's wild.",
"I'm listening.",
"Spill the tea.",
"You're hilarious.",
"That's iconic.",
"Main character energy.",
"Interesting...",
"I'm curious now.",
"Explain more.",
"That's adorable.",
"I'm impressed.",
"You're creative.",
"That's clever.",
"Relatable.",
"Same honestly.",
"I'm vibing with this.",
"That escalated quickly.",
"You have good taste.",
"That's exciting.",
"You're funny.",
"That's chaotic but fun.",
"I'm enjoying this conversation.",
"That's surprising.",
"I'm invested now.",
"This is entertaining.",
"That's bold.",
"You're full of ideas.",
"That's dramatic!",
"That sounds crazy.",
"I'm curious.",
"Tell me more.",
"That's unexpected.",
"That's kind of genius.",
"That's a vibe.",
"Cool!"
]

let moods={
mad:["HEY 😡","Take care of me!","I'm angry!"],
sad:["I'm sad...","Play with me","I feel lonely"],
annoyed:["Hmm","You forgot me","I'm bored"],
meh:["I'm ok","Just chilling","What now?"],
playful:["Let's play!","Ball!!","YAY"],
happy:["BEST DAY EVER","I LOVE YOU","Let's go!"]
}

function start(){

username=document.getElementById("nameInput").value

if(username==="")return

document.getElementById("player").innerText=username

document.getElementById("login").style.display="none"
document.getElementById("game").style.display="block"

update()

setInterval(()=>{
health-=5
if(health<0)health=0
update()
},30000)

}

function show(id){

document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"))

document.getElementById(id).classList.add("active")

}

function update(){

document.getElementById("coins").innerText=coins
document.getElementById("health").innerText=health

updateMood()

}

function updateMood(){

let petMood=""

if(health<=10)petMood="mad"
else if(health<=30)petMood="sad"
else if(health<=50)petMood="annoyed"
else if(health<=70)petMood="meh"
else if(health<100)petMood="playful"
else petMood="happy"

document.getElementById("mood").innerText=petMood
document.getElementById("petMood").innerText=petMood

let lines=moods[petMood]

let line=lines[Math.floor(Math.random()*lines.length)]

document.getElementById("speech").innerText=line

}

function feed(){

if(coins>=5){
coins-=5
health+=20
}

if(health>100)health=100

document.getElementById("speech").innerText="Yum!"

update()

}

function bathe(){

health+=10

if(health>100)health=100

document.getElementById("speech").innerText="Bath time!"

update()

}

function play(){

coins+=5
health+=5

let pet=document.getElementById("pet")

pet.classList.add("playing")

setTimeout(()=>{
pet.classList.remove("playing")
},2000)

update()

}

function buyToy(item,price){

if(coins>=price){
coins-=price
document.getElementById("toy").innerText=item
}

update()

}

let coin=document.getElementById("coin")

function moveCoin(){

let x=Math.random()*280
let y=Math.random()*280

coin.style.left=x+"px"
coin.style.top=y+"px"

}

setInterval(moveCoin,1000)

coin.onclick=function(){

score++
coins+=5

document.getElementById("score").innerText=score

moveCoin()

update()

}

function send(){

let input=document.getElementById("chatInput").value

if(input==="")return

let box=document.getElementById("chatbox")

box.innerHTML+="<p><b>"+username+":</b> "+input+"</p>"

let reply=responses[Math.floor(Math.random()*responses.length)]

box.innerHTML+="<p><b>Pet:</b> "+reply+"</p>"

box.scrollTop=box.scrollHeight

document.getElementById("chatInput").value=""

}

</script>

</body>
</html>
