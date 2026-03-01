<!DOCTYPE html>
<html>
<head>
<title>K-HEARTS</title>
<style>
/* BODY & FONT */
body {
  margin: 0;
  font-family: Georgia, serif;
  background: linear-gradient(to bottom, #fff0f5, #ffe4ec);
  text-align: center;
  color: #b03060;
  overflow-x: hidden;
  scroll-behavior: smooth;
  cursor: url('https://i.imgur.com/WzLQwNl.png'), auto; /* optional cute cursor */
}

/* NAVBAR */
nav {
  background: rgba(255,255,255,0.8);
  padding: 15px;
  box-shadow: 0 5px 15px rgba(255,182,193,0.4);
  position: sticky;
  top: 0;
  z-index: 1000;
  display: flex;
  justify-content: center;
  gap: 40px;
}
nav a {
  text-decoration: none;
  color: hotpink;
  font-weight: bold;
  font-size: 18px;
  transition: 0.3s;
}
nav a:hover {
  color: #ff1493;
  letter-spacing: 2px;
}

/* TITLE */
h1 {
  font-size: 60px;
  margin-top: 60px;
  color: #ff69b4;
  text-shadow: 0 0 25px #ffb6c1;
  animation: fadeInTitle 2s ease-in-out;
}
@keyframes fadeInTitle {
  0% { opacity:0; transform:translateY(20px);}
  100% { opacity:1; transform:translateY(0);}
}

/* BUTTON */
button {
  padding: 12px 30px;
  border: none;
  border-radius: 25px;
  background: hotpink;
  color: white;
  cursor: pointer;
  margin-top: 20px;
  transition: 0.3s;
}
button:hover {
  background: #ff1493;
  transform: scale(1.05);
}

/* SWIRLS */
.swirl {
  position: fixed;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  border: 2px solid #ff69b4;
  animation: swirlMove 20s linear infinite;
  opacity: 0.5;
}
@keyframes swirlMove {
  0% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-500px) rotate(180deg); }
  100% { transform: translateY(0) rotate(360deg); }
}

/* MEMBER CARDS */
.members {
  display: flex;
  justify-content: center;
  gap: 40px;
  padding: 60px;
  flex-wrap: wrap;
}
.card {
  background: white;
  width: 250px;
  padding: 25px;
  border-radius: 25px;
  box-shadow: 0 15px 30px rgba(255,182,193,0.4);
  cursor: pointer;
  transition: 0.4s;
}
.card:hover {
  transform: translateY(-10px) scale(1.03);
}

/* POPUP */
.popup {
  display: none;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 20px 40px rgba(255,105,180,0.6);
  z-index: 10000;
}
.popup button {
  margin-top: 15px;
  padding: 8px 20px;
  border: none;
  background: hotpink;
  color: white;
  border-radius: 20px;
  cursor: pointer;
}

/* FANDOM REVEAL */
#fandom {
  font-size: 40px;
  margin-top: 20px;
  opacity: 0;
  transition: 1s;
  animation: fadeInFandom 1s forwards;
}
@keyframes fadeInFandom {
  0% {opacity:0;}
  100% {opacity:1;}
}

/* LIGHTSTICK */
.lightstick {
  width: 80px;
  height: 200px;
  margin: 20px auto;
  background: linear-gradient(to top, #ff69b4, #ffe4ec);
  border-radius: 20px;
  box-shadow: 0 0 25px #ff69b4;
  position: relative;
}
.lightstick::after {
  content: '💖';
  position: absolute;
  top: -30px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 40px;
  animation: glowPulse 1.5s infinite alternate;
}
@keyframes glowPulse {
  0% { text-shadow: 0 0 10px #ff69b4; }
  100% { text-shadow: 0 0 25px #ff1493; }
}

/* FOOTER */
footer {
  margin-top: 70px;
  padding: 25px;
  background: white;
  font-size: 14px;
  color: #ff1493;
}
</style>
</head>
<body>

<!-- NAVBAR -->
<nav>
  <a href="#home">Home</a>
  <a href="#members">Members</a>
</nav>

<!-- HOME -->
<h1 id="home">K-HEARTS</h1>
<p>Three Hearts. One Spark.</p>

<!-- Lightstick -->
<div class="lightstick"></div>

<p>
Welcome to the official universe of K-HEARTS ✨  
Cute elegance, soft power, endless sparkle.  
Scroll down to meet the members and see the fandom reveal 💖
</p>

<!-- FANDOM BUTTON -->
<button onclick="revealFandom()">Reveal Official Fandom Name</button>
<div id="fandom">KAES 💖</div>

<!-- SWIRLS -->
<div class="swirl" style="left:10%; animation-delay:0s;"></div>
<div class="swirl" style="left:30%; animation-delay:2s;"></div>
<div class="swirl" style="left:50%; animation-delay:4s;"></div>
<div class="swirl" style="left:70%; animation-delay:1s;"></div>
<div class="swirl" style="left:85%; animation-delay:3s;"></div>

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

<!-- BACKGROUND MUSIC -->
<audio autoplay loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<!-- SPARKLE CURSOR TRAIL -->
<script>
document.addEventListener("mousemove", function(e) {
  var sparkle = document.createElement("div");
  sparkle.innerHTML = "✨";
  sparkle.style.position = "fixed";
  sparkle.style.left = e.pageX + "px";
  sparkle.style.top = e.pageY + "px";
  sparkle.style.pointerEvents = "none";
  sparkle.style.fontSize = "18px";
  sparkle.style.opacity = "0.7";
  sparkle.style.transition = "all 0.5s linear";
  document.body.appendChild(sparkle);
  setTimeout(() => sparkle.remove(), 700);
});
</script>

<!-- POPUP & FANDOM FUNCTIONS -->
<script>
function revealFandom() {
  document.getElementById("fandom").style.opacity = "1";
}
function openPopup(text) {
  document.getElementById("popupText").innerText = text;
  document.getElementById("popup").style.display = "block";
}
function closePopup() {
  document.getElementById("popup").style.display = "none";
}
</script>

<footer>
© 2026 K-HEARTS Official ♡ All Hearts Reserved
</footer>

</body>
</html>
