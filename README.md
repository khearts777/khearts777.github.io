<!DOCTYPE html>
<html>
<head>
<title>K-HEARTS Official</title>
<style>
/* BODY */
body {
  margin:0;
  font-family: Georgia, serif;
  background: linear-gradient(to bottom, #fff0f5, #ffe4ec);
  color: #b03060;
  scroll-behavior: smooth;
  overflow-x: hidden;
  position: relative;
}

/* NAVBAR */
nav {
  position: sticky;
  top:0;
  background: rgba(255,255,255,0.85);
  display: flex;
  justify-content: center;
  gap: 40px;
  padding: 15px;
  box-shadow: 0 5px 15px rgba(255,182,193,0.4);
  z-index: 1000;
}
nav a {
  text-decoration: none;
  color: hotpink;
  font-weight: bold;
  font-size: 18px;
  transition:0.3s;
}
nav a:hover {
  color:#ff1493;
  letter-spacing:2px;
  text-shadow:0 0 10px #ff69b4;
  animation: wiggle 0.5s;
}
@keyframes wiggle{
  0%{transform:rotate(0deg);}
  25%{transform:rotate(5deg);}
  50%{transform:rotate(-5deg);}
  75%{transform:rotate(3deg);}
  100%{transform:rotate(0deg);}
}

/* HEADINGS */
h1,h2 {
  text-align:center;
  color:#ff69b4;
  text-shadow:0 0 25px #ffb6c1;
  margin-top:50px;
}
h1 {font-size:60px; animation: fadeIn 2s;}
h2 {font-size:45px; margin-top:80px;}

/* BUTTONS */
button {
  padding:12px 30px;
  border:none;
  border-radius:25px;
  background: hotpink;
  color:white;
  cursor:pointer;
  margin:20px;
  transition:0.3s;
}
button:hover {background:#ff1493; transform:scale(1.05);}

/* LIGHTSTICK */
.lightstick {
  width:80px;
  height:200px;
  margin:20px auto;
  background:linear-gradient(to top, #ff69b4, #ffe4ec);
  border-radius:20px;
  box-shadow:0 0 25px #ff69b4;
  position:relative;
  animation: lightstickPop 1s ease-out;
}
.lightstick::after {
  content:'💖';
  position:absolute;
  top:-30px;
  left:50%;
  transform:translateX(-50%);
  font-size:40px;
  animation: glowPulse 1.5s infinite alternate;
}
@keyframes glowPulse {
  0% {text-shadow:0 0 10px #ff69b4;}
  100% {text-shadow:0 0 25px #ff1493;}
}
@keyframes lightstickPop{
  0% {transform:scale(0);}
  100% {transform:scale(1);}
}

/* MEMBER CARDS */
.members {
  display:flex;
  justify-content:center;
  gap:40px;
  padding:60px;
  flex-wrap:wrap;
}
.card {
  background:white;
  width:250px;
  padding:25px;
  border-radius:25px;
  box-shadow:0 15px 30px rgba(255,182,193,0.4);
  cursor:pointer;
  transition:0.4s;
  text-align:center;
}
.card:hover {
  transform:translateY(-10px) scale(1.05);
  box-shadow:0 0 25px #ff69b4;
}

/* POPUP */
.popup {
  display:none;
  position:fixed;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  background:white;
  padding:30px;
  border-radius:20px;
  box-shadow:0 20px 40px rgba(255,105,180,0.6);
  z-index:10000;
}
.popup button {
  margin-top:15px;
  padding:8px 20px;
  border:none;
  background:hotpink;
  color:white;
  border-radius:20px;
  cursor:pointer;
}

/* FANDOM */
#fandom {
  font-size:40px;
  margin-top:20px;
  opacity:0;
  transition:1s;
  color:#ff69b4;
  text-shadow:0 0 25px #ffb6c1;
  display:inline-block;
  animation: fandomGlow 1s infinite alternate;
}
@keyframes fandomGlow{
  0%{text-shadow:0 0 15px #ff69b4;}
  100%{text-shadow:0 0 35px #ff1493;}
}

/* COUNTDOWN */
#countdown {
  font-size:35px;
  margin:30px 0;
  color:#ff1493;
  text-shadow:0 0 15px #ffb6c1;
  position:relative;
}

/* NO LIMITS SONG TEASER */
#song {
  font-size:30px;
  color:#ff69b4;
  text-shadow:0 0 15px #ffb6c1;
  overflow:hidden;
  white-space:nowrap;
  width:100%;
}
#song span{
  display:inline-block;
  padding-left:100%;
  animation: scrollSong 15s linear infinite;
}
@keyframes scrollSong{
  0%{transform:translateX(0);}
  100%{transform:translateX(-120%);}
}

/* SWIRLS & HEARTS */
.swirl, .heart {
  position:fixed;
  width:50px; height:50px;
  border-radius:50%;
  opacity:0.5;
  animation: floatMove 15s linear infinite;
}
.swirl {border:2px solid #ff69b4;}
.heart::after {content:"💖"; font-size:50px;}

/* ANIMATIONS */
@keyframes fadeIn {0%{opacity:0;}100%{opacity:1;}}
@keyframes floatMove{
  0%{transform:translateY(0) rotate(0deg);}
  50%{transform:translateY(-600px) rotate(180deg);}
  100%{transform:translateY(0) rotate(360deg);}
}

/* FOOTER */
footer{
  margin-top:70px;
  padding:25px;
  background:white;
  font-size:14px;
  color:#ff1493;
}
</style>
</head>
<body>

<nav>
<a href="#home">Home</a>
<a href="#members">Members</a>
<a href="#fandom-section">Fandom</a>
<a href="#countdown-section">Debut Countdown</a>
<a href="#song-section">No Limits</a>
</nav>

<!-- HOME -->
<h1 id="home">K-HEARTS</h1>
<p>Three Hearts. One Spark.</p>
<div class="lightstick"></div>

<!-- MEMBERS -->
<h2 id="members">Meet K-HEARTS</h2>
<section class="members">
<div class="card" onclick="openPopup('Karlyn: Leader, Main Rapper, Lead Dancer, Sub Vocalist')">Karlyn</div>
<div class="card" onclick="openPopup('Alyssa: Visual, Main Vocalist, Sub Rapper')">Alyssa</div>
<div class="card" onclick="openPopup('Trixie: Main Dancer, Lead Rapper, Sub Vocalist')">Trixie</div>
</section>

<div class="popup" id="popup">
<div id="popupText"></div>
<button onclick="closePopup()">Close</button>
</div>

<!-- FANDOM REVEAL -->
<h2 id="fandom-section">Fandom Reveal</h2>
<button onclick="revealFandom()">Click to Reveal KAES</button>
<div id="fandom">✨KAES✨</div>

<!-- DEBUT COUNTDOWN -->
<h2 id="countdown-section">Debut Countdown</h2>
<div id="countdown"></div>

<!-- SONG TEASER -->
<h2 id="song-section">First Song: No Limits</h2>
<div id="song"><span>♪ No Limits, K-HEARTS shine, sparkle & fly, no limits, dream high ♪</span></div>

<!-- SWIRLS & HEARTS -->
<div class="swirl" style="left:10%; animation-delay:0s;"></div>
<div class="swirl" style="left:30%; animation-delay:2s;"></div>
<div class="swirl" style="left:50%; animation-delay:4s;"></div>
<div class="heart" style="left:20%; animation-delay:1s;"></div>
<div class="heart" style="left:75%; animation-delay:3s;"></div>

<!-- SPARKLE CURSOR -->
<script>
document.addEventListener("mousemove", function(e){
  var sparkle=document.createElement("div");
  sparkle.innerHTML="✨";
  sparkle.style.position="fixed";
  sparkle.style.left=e.pageX+"px";
  sparkle.style.top=e.pageY+"px";
  sparkle.style.pointerEvents="none";
  sparkle.style.fontSize="18px";
  sparkle.style.opacity="0.7";
  sparkle.style.transition="all 0.5s linear";
  document.body.appendChild(sparkle);
  setTimeout(()=>sparkle.remove(),700);
});
</script>

<!-- FUNCTIONS -->
<script>
function revealFandom(){document.getElementById("fandom").style.opacity="1";}
function openPopup(text){document.getElementById("popupText").innerText=text; document.getElementById("popup").style.display="block";}
function closePopup(){document.getElementById("popup").style.display="none";}

/* COUNTDOWN TIMER */
var countDownDate = new Date();
countDownDate.setDate(countDownDate.getDate()+30); // 30 days
var x = setInterval(function(){
  var now=new Date().getTime();
  var distance=countDownDate-now;
  var days=Math.floor(distance/(1000*60*60*24));
  var hours=Math.floor((distance%(1000*60*60*24))/(1000*60*60));
  var minutes=Math.floor((distance%(1000*60*60))/(1000*60));
  var seconds=Math.floor((distance%(1000*60))/1000);
  document.getElementById("countdown").innerHTML=days+"d "+hours+"h "+minutes+"m "+seconds+"s";
  if(distance<0){clearInterval(x); document.getElementById("countdown").innerHTML="✨K-HEARTS Debuted!✨";}
},1000);
</script>

<footer>
© 2026 K-HEARTS Official ♡ All Hearts Reserved
</footer>

</body>
</html>
