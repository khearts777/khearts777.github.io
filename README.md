<!DOCTYPE html>
<html>
<head>
<title>K-HEARTS</title>

<style>
body {
  margin: 0;
  font-family: Georgia, serif;
  background: linear-gradient(to bottom, #fff0f5, #ffe4ec);
  text-align: center;
  color: #b03060;
  overflow-x: hidden;
}

/* LOADING SCREEN */
#loader {
  position: fixed;
  width: 100%;
  height: 100%;
  background: #fff0f5;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  color: hotpink;
  z-index: 9999;
  animation: fadeOut 2s forwards;
  animation-delay: 2s;
}

@keyframes fadeOut {
  to { opacity: 0; visibility: hidden; }
}

/* FLOATING SPARKLES */
.sparkle {
  position: fixed;
  bottom: -20px;
  animation: floatUp 10s linear infinite;
  opacity: 0.6;
  font-size: 20px;
}

@keyframes floatUp {
  0% { transform: translateY(0); opacity: 0.6; }
  100% { transform: translateY(-110vh); opacity: 0; }
}

/* HEADER */
header {
  padding: 80px 20px;
}

h1 {
  font-size: 65px;
  letter-spacing: 4px;
  color: #ff69b4;
  text-shadow: 0 0 20px #ffb6c1;
}

.subtitle {
  font-size: 20px;
}

/* COUNTDOWN */
#countdown {
  font-size: 22px;
  margin: 20px;
  color: #ff1493;
}

/* MEMBER CARDS */
.members {
  display: flex;
  justify-content: center;
  gap: 40px;
  padding: 50px;
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
  transform: scale(1.08);
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

footer {
  margin-top: 70px;
  padding: 25px;
  background: white;
}
</style>
</head>

<body>

<div id="loader">✨ K-HEARTS ✨</div>

<!-- FLOATING SPARKLES -->
<div class="sparkle" style="left:10%;">💖</div>
<div class="sparkle" style="left:30%;animation-delay:2s;">✨</div>
<div class="sparkle" style="left:50%;animation-delay:4s;">🌸</div>
<div class="sparkle" style="left:70%;animation-delay:1s;">💎</div>
<div class="sparkle" style="left:85%;animation-delay:3s;">💗</div>

<header>
<h1>K-HEARTS</h1>
<p class="subtitle">Three Hearts. One Spark.</p>

<div id="countdown"></div>

<p>
Welcome to our official universe.  
Where elegance meets sparkle and every heartbeat shines brighter.  
Stay with us. Grow with us. Glow with us.
</p>
</header>

<section class="members">
<div class="card" onclick="openPopup('Yujin - Leader, Main Rapper, Lead Dancer, Sub Vocalist')">Yujin</div>
<div class="card" onclick="openPopup('Wonyoung - Visual, Main Vocalist, Sub Rapper')">Wonyoung</div>
<div class="card" onclick="openPopup('Gaeul - Main Dancer, Lead Rapper, Sub Vocalist')">Gaeul</div>
</section>

<div class="popup" id="popup">
<div id="popupText"></div>
<button onclick="closePopup()">Close</button>
</div>

<footer>
© 2026 K-HEARTS Official ♡ All Hearts Reserved
</footer>

<!-- BACKGROUND MUSIC -->
<audio autoplay loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<script>
/* COUNTDOWN TIMER (Set comeback date here) */
var comebackDate = new Date("March 30, 2026 00:00:00").getTime();

var x = setInterval(function() {
  var now = new Date().getTime();
  var distance = comebackDate - now;

  var days = Math.floor(distance / (1000 * 60 * 60 * 24));
  document.getElementById("countdown").innerHTML =
    "Comeback in " + days + " days 💖";

}, 1000);

/* POPUP FUNCTIONS */
function openPopup(text) {
  document.getElementById("popupText").innerText = text;
  document.getElementById("popup").style.display = "block";
}

function closePopup() {
  document.getElementById("popup").style.display = "none";
}

/* CURSOR SPARKLE */
document.addEventListener("mousemove", function(e) {
  var sparkle = document.createElement("div");
  sparkle.innerHTML = "✨";
  sparkle.style.position = "fixed";
  sparkle.style.left = e.pageX + "px";
  sparkle.style.top = e.pageY + "px";
  sparkle.style.pointerEvents = "none";
  sparkle.style.animation = "fade 1s forwards";
  document.body.appendChild(sparkle);
  setTimeout(() => sparkle.remove(), 1000);
});
</script>

</body>
</html>

body {
  margin: 0;
  font-family: Georgia, serif;
  background: linear-gradient(to bottom, #fff0f5, #ffe4ec);
  text-align: center;
  color: #b03060;
  overflow-x: hidden;
}

/* NAV BAR */
nav {
  background: white;
  padding: 15px;
  box-shadow: 0 5px 15px rgba(255,182,193,0.4);
  position: sticky;
  top: 0;
}

nav a {
  margin: 0 20px;
  text-decoration: none;
  color: hotpink;
  font-weight: bold;
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
  text-shadow: 0 0 15px #ffb6c1;
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
  transition: 0.4s;
}

.card:hover {
  transform: translateY(-10px);
}

/* FANDOM REVEAL */
#fandom {
  font-size: 40px;
  margin-top: 30px;
  opacity: 0;
  transition: 1s;
}

footer {
  margin-top: 70px;
  padding: 25px;
  background: white;
}

<!DOCTYPE html>
<html>
<head>
<title>K-HEARTS</title>
<link rel="stylesheet" href="style.css">
</head>
<body>

<nav>
  <a href="index.html">Home</a>
  <a href="members.html">Members</a>
</nav>

<h1>K-HEARTS</h1>
<p>Three Hearts. One Spark.</p>

<p>
Welcome to the official universe of K-HEARTS.  
Cute elegance. Soft power. Endless sparkle.
</p>

<button onclick="revealFandom()">Reveal Official Fandom Name</button>

<div id="fandom">KAES 💖</div>

<footer>
© 2026 K-HEARTS Official ♡ All Hearts Reserved
</footer>

<script>
function revealFandom() {
  document.getElementById("fandom").style.opacity = "1";
}
</script>

</body>
</html>

<!DOCTYPE html>
<html>
<head>
<title>K-HEARTS Members</title>
<link rel="stylesheet" href="style.css">
</head>
<body>

<nav>
  <a href="index.html">Home</a>
  <a href="members.html">Members</a>
</nav>

<h1>Meet K-HEARTS</h1>

<section class="members">

  <div class="card">
    <h2>Karlyn</h2>
    <p>Leader</p>
    <p>Main Rapper</p>
    <p>Lead Dancer</p>
    <p>Sub Vocalist</p>
  </div>

  <div class="card">
    <h2>Alyssa</h2>
    <p>Visual</p>
    <p>Main Vocalist</p>
    <p>Sub Rapper</p>
  </div>

  <div class="card">
    <h2>Trixie</h2>
    <p>Main Dancer</p>
    <p>Lead Rapper</p>
    <p>Sub Vocalist</p>
  </div>

</section>

<footer>
Forever with KAES 💗
</footer>

</body>
</html>
