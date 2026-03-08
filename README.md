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

.playing{animation:bounce .6s infinite;}

.chatbox{
height:220px;
overflow:auto;
border:2px solid pink;
background:white;
border-radius:15px;
padding:10px;
text-align:left;
}

.card{
width:60px;
height:60px;
display:inline-block;
background:white;
margin:5px;
border-radius:10px;
line-height:60px;
font-size:30px;
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
<button onclick="choosePet('🦊')">Fox</button>
<button onclick="choosePet('🐼')">Panda</button>

</div>

<div id="game" style="display:none">

<p>Coins: <span id="coins"></span> | XP: <span id="xp"></span></p>
<p>Health: <span id="health"></span> | Mood: <span id="mood"></span></p>

<button onclick="show('home')">Home</button>
<button onclick="show('pets')">Pets</button>
<button onclick="show('games')">Games</button>
<button onclick="show('shop')">Shop</button>
<button onclick="show('chat')">Chat</button>
<button onclick="show('members')">Members</button>
<button onclick="show('lyrics')">Lyrics</button>

<div id="home" class="section active">
<h2>Welcome <span id="player"></span></h2>
</div>

<div id="pets" class="section">

<div id="pet" class="pet walk">🐶</div>

<p id="speech">Hi!</p>

<button onclick="feed()">Feed</button>
<button onclick="bathe()">Bathe</button>
<button onclick="play()">Play</button>
<button onclick="sleep()">Sleep</button>

</div>

<div id="shop" class="section">

<h3>Accessories</h3>

<button onclick="buy('🎩',30)">Hat</button>
<button onclick="buy('👑',50)">Crown</button>
<button onclick="buy('🕶️',40)">Glasses</button>

<p>Current: <span id="acc"></span></p>

</div>

<div id="games" class="section">

<h3>Catch Coin</h3>
<button onclick="coinGame()">Play</button>

<h3>Number Guess</h3>
<button onclick="guessGame()">Play</button>

<h3>Reaction Game</h3>
<button onclick="reactionGame()">Play</button>

<h3>Quiz</h3>
<button onclick="quiz()">Play</button>

<h3>Memory Game</h3>
<div id="memory"></div>

</div>

<div id="chat" class="section">

<div class="chatbox" id="chatbox"></div>

<input id="chatInput">
<button onclick="send()">Send</button>

</div>

<div id="members" class="section">

<h2>🌟 Members</h2>

<p><b>Karlyn</b> — Leader, Main Rapper, Lead Dancer</p>
<p><b>Trixie</b> — Center, Main Dancer</p>
<p><b>Hayley</b> — Lead Vocalist, Maknae</p>
<p><b>Alyssa</b> — Main Vocalist, Visual</p>

</div>

<div id="lyrics" class="section">

<h2>No Limits</h2>

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

We go higher, higher  
Touch the sky, no ceiling  
Fearless fire, fire  
Got the whole world feeling  

No doubts, no fear  
We came too far to disappear  
Global girls, we redefine  
Step aside — the crown is mine  

</p>

</div>

</div>

<script>

let coins=100
let xp=0
let health=100
let username=""
let accessory=""
let secret=Math.floor(Math.random()*10)+1

let memory={color:""}

function save(){
localStorage.setItem("khearts",JSON.stringify({coins,xp,health,accessory}))
}

function load(){
let d=JSON.parse(localStorage.getItem("khearts"))
if(d){
coins=d.coins
xp=d.xp
health=d.health
accessory=d.accessory
}
}

function start(){

username=document.getElementById("nameInput").value
if(username==="")return

load()

document.getElementById("login").style.display="none"
document.getElementById("petSelect").style.display="block"

}

function choosePet(p){

document.getElementById("pet").innerText=p

document.getElementById("petSelect").style.display="none"
document.getElementById("game").style.display="block"

document.getElementById("player").innerText=username

update()

}

function show(id){

document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"))
document.getElementById(id).classList.add("active")

}

function update(){

document.getElementById("coins").innerText=coins
document.getElementById("xp").innerText=xp
document.getElementById("health").innerText=health
document.getElementById("acc").innerText=accessory

let mood=""

if(health<=20)mood="mad"
else if(health<=40)mood="sad"
else if(health<=60)mood="meh"
else if(health<=80)mood="playful"
else mood="happy"

document.getElementById("mood").innerText=mood

save()

}

function feed(){
coins-=5
health+=20
if(health>100)health=100
document.getElementById("speech").innerText="Yum!"
update()
}

function bathe(){
health+=10
document.getElementById("speech").innerText="Splash!"
update()
}

function play(){

xp+=5
coins+=5

let p=document.getElementById("pet")
p.classList.add("playing")

setTimeout(()=>p.classList.remove("playing"),2000)

update()

}

function sleep(){
health=100
document.getElementById("speech").innerText="Zzz..."
update()
}

function buy(item,cost){

if(coins>=cost){
coins-=cost
accessory=item
}

update()

}

function coinGame(){

coins+=10
xp+=5
alert("You found coins!")

update()

}

function guessGame(){

let g=prompt("Guess 1-10")

if(g==secret){
alert("Correct!")
coins+=20
}

update()

}

function reactionGame(){

let start=Date.now()
alert("Click OK then click again fast!")
let end=Date.now()

if(end-start<300){
coins+=20
alert("Fast!")
}else{
coins+=5
}

update()

}

function quiz(){

let a=prompt("Who is leader? A)Karlyn B)Trixie")

if(a.toLowerCase()=="a"){
coins+=20
alert("Correct!")
}

update()

}

function send(){

let input=document.getElementById("chatInput").value
let lower=input.toLowerCase()

let box=document.getElementById("chatbox")

box.innerHTML+="<p><b>"+username+":</b> "+input+"</p>"

let reply=""

if(lower.includes("hello")||lower.includes("hi")){
reply="Hi "+username+"! 💖 I'm really happy to chat with you."
}

else if(lower.includes("favorite color")){
memory.color=input.split("is")[1]
reply="Nice! I'll remember your favorite color is "+memory.color
}

else{

let responses=[

"That's really interesting. Tell me more about it!",
"I'm enjoying this chat actually.",
"That's a fun thing to talk about.",
"Your pet looks like it wants attention too 🐾",
"That's such a random but funny thing to say.",
"I wonder what you'll say next.",
"That's actually a cool idea.",
"This conversation is getting interesting.",
"ooh! nice!.",
"yeahh ikr?!.",
"okayyy!.",
"how r u tdy?."

]

reply=responses[Math.floor(Math.random()*responses.length)]

}

box.innerHTML+="<p><b>AI:</b> "+reply+"</p>"

document.getElementById("chatInput").value=""

box.scrollTop=box.scrollHeight

}

update()

</script>

</body>
</html>
