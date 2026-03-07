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

button{
background:#ff69b4;
border:none;
padding:10px 15px;
border-radius:12px;
margin:4px;
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

.walk{animation:walk 5s infinite;}

@keyframes bounce{
0%{transform:translateY(0)}
50%{transform:translateY(-25px)}
100%{transform:translateY(0)}
}

.playing{animation:bounce 0.6s infinite;}

.chatbox{
height:220px;
overflow:auto;
border:2px solid pink;
background:white;
border-radius:15px;
padding:10px;
text-align:left;
}

#gameArea{
width:300px;
height:300px;
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

<h1>💖 K-Hearts World 💖</h1>

<div id="login">
Enter your Kaes name:<br>
<input id="nameInput">
<button onclick="start()">Enter</button>
</div>

<div id="petSelect" style="display:none">

<h2>Choose Your Pet</h2>

<button onclick="choosePet('🐶')">Dog</button>
<button onclick="choosePet('🐱')">Cat</button>
<button onclick="choosePet('🐧')">Penguin</button>

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
<h2>Welcome <span id="player"></span></h2>
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

</div>

<div id="games" class="section">

<h3>Game 1: Catch the Coin</h3>

<div id="gameArea">
<div id="coin">🪙</div>
</div>

<p>Score: <span id="score">0</span></p>

<hr>

<h3>Game 2: Number Guess</h3>

<button onclick="guessGame()">Play</button>

<hr>

<h3>Game 3: Reaction Tap</h3>

<button onclick="reactionGame()">Tap Fast!</button>

<hr>

<h3>Game 4: Quiz</h3>

<button onclick="quizGame()">Start Quiz</button>

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

<p style="background:white;padding:20px;border-radius:20px;text-align:left">

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

</p>

</div>

</div>

<script>

let coins=100
let health=100
let username=""
let score=0
let secret=Math.floor(Math.random()*10)+1

function start(){

username=document.getElementById("nameInput").value

if(username==="")return

document.getElementById("login").style.display="none"
document.getElementById("petSelect").style.display="block"

}

function choosePet(p){

document.getElementById("pet").innerText=p

document.getElementById("petSelect").style.display="none"
document.getElementById("game").style.display="block"

document.getElementById("player").innerText=username

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

let mood=""

if(health<=10)mood="mad"
else if(health<=30)mood="sad"
else if(health<=50)mood="annoyed"
else if(health<=70)mood="meh"
else if(health<100)mood="playful"
else mood="extremely happy"

document.getElementById("mood").innerText=mood
document.getElementById("petMood").innerText=mood

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

document.getElementById("speech").innerText="Splash!"

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

let coin=document.getElementById("coin")

function moveCoin(){

let x=Math.random()*260
let y=Math.random()*260

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

function guessGame(){

let guess=prompt("Guess number 1-10")

if(guess==secret){

alert("Correct! +20 coins")

coins+=20

secret=Math.floor(Math.random()*10)+1

}else{

alert("Wrong! Try again")

}

update()

}

function reactionGame(){

let start=Date.now()

alert("Click OK then tap again FAST!")

let end=Date.now()

let reaction=end-start

if(reaction<300){

coins+=25
alert("Fast! +25 coins")

}else{

coins+=5
alert("Slow! +5 coins")

}

update()

}

function quizGame(){

let ans=prompt("Who is the leader? A)Karlyn B)Trixie")

if(ans.toLowerCase()=="a"){

coins+=20
alert("Correct!")

}else{

alert("Wrong!")

}

update()

}

function send(){

let input=document.getElementById("chatInput").value.toLowerCase()

if(input==="")return

let box=document.getElementById("chatbox")

box.innerHTML+="<p><b>"+username+":</b> "+input+"</p>"

let reply=""

if(input.includes("hello")||input.includes("hi")){
reply="Hi "+username+"! 💖"
}

else{

let responses=[
"That's interesting!",
"Tell me more!",
"LOL 😂",
"I'm listening.",
"Spill the tea ☕",
"That's iconic.",
"Main character energy!",
"That's cool.",
"I'm curious now.",
"Explain more!",
"That sounds fun.",
"You're hilarious.",
"That's surprising.",
"I'm enjoying this chat!",
"That's a vibe."
]

reply=responses[Math.floor(Math.random()*responses.length)]

}

box.innerHTML+="<p><b>AI:</b> "+reply+"</p>"

box.scrollTop=box.scrollHeight

document.getElementById("chatInput").value=""

}

</script>

</body>
</html>
