# Pihurani
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Pihurani ❤️</title>

<style>
body {
    margin: 0;
    overflow: hidden;
    font-family: 'Segoe UI', sans-serif;
}

/* Pages */
.page {
    width: 100%;
    height: 100vh;
    display: none;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    color: white;
    text-align: center;
    position: absolute;
    transition: opacity 1s ease;
}

#page1 {
    display: flex;
    background: linear-gradient(135deg, #ff758c, #ff7eb3);
}

#page2 {
    background: linear-gradient(135deg, #87CEFA, #FFD1DC);
    transition: background 3s ease;
}

/* Night Mode */
.night {
    background: linear-gradient(135deg, #0f2027, #203a43, #2c5364) !important;
}

/* Glass Card */
.card {
    backdrop-filter: blur(15px);
    background: rgba(255,255,255,0.1);
    padding: 40px;
    border-radius: 20px;
}

/* Button */
button {
    margin-top: 20px;
    padding: 15px 30px;
    font-size: 1.2rem;
    border: none;
    border-radius: 30px;
    background: white;
    color: #ff4e50;
    cursor: pointer;
    transition: 0.3s;
}

button:hover {
    background: #ff4e50;
    color: white;
    transform: scale(1.1);
}

/* Typing Text */
.typing {
    font-size: 2rem;
    border-right: 3px solid white;
    white-space: nowrap;
    overflow: hidden;
    text-shadow: 0 0 10px white;
}

/* Cat Animation */
.cat {
    position: absolute;
    bottom: 30px;
    left: -200px;
    width: 150px;
    animation: moveCat 12s linear infinite, bounce 2s infinite;
}

@keyframes moveCat {
    0% { left: -200px; }
    100% { left: 100%; }
}

@keyframes bounce {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
}

/* Heart Rain */
.heart {
    position: absolute;
    color: pink;
    font-size: 18px;
    animation: fall linear infinite;
    opacity: 0.8;
}

@keyframes fall {
    0% { transform: translateY(-10vh) scale(1); }
    100% { transform: translateY(110vh) scale(1.5); }
}

/* Stars */
.star {
    position: absolute;
    width: 2px;
    height: 2px;
    background: white;
    opacity: 0.8;
    animation: twinkle 2s infinite alternate;
}

@keyframes twinkle {
    from { opacity: 0.3; }
    to { opacity: 1; }
}
</style>
</head>

<body>

<!-- MUSIC -->
<audio id="music" loop>
    <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mp3">
</audio>

<!-- PAGE 1 -->
<div id="page1" class="page">
    <div class="card">
        <h1>Welcome Pihurani 💖</h1>
        <button onclick="goNext()">Click Here</button>
    </div>
</div>

<!-- PAGE 2 -->
<div id="page2" class="page">
    <h1 class="typing" id="text"></h1>
    <img class="cat" src="https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif">
</div>

<script>
function goNext() {
    let p1 = document.getElementById("page1");
    let p2 = document.getElementById("page2");

    p1.style.opacity = "0";
    setTimeout(() => {
        p1.style.display = "none";
        p2.style.display = "flex";
        p2.style.opacity = "1";
    }, 800);

    startTyping();
    startHearts();
    startDayNightCycle();

    let music = document.getElementById("music");
    music.volume = 0.5;
    music.play().catch(() => {});
}

/* Typing Effect */
const message = "🐾 ma da ladle meawwwwwwwww gp gp gp 🐾 💖";
let i = 0;

function startTyping() {
    function type() {
        if (i < message.length) {
            document.getElementById("text").innerHTML += message.charAt(i);
            i++;
            setTimeout(type, 70);
        }
    }
    type();
}

/* Heart Rain */
function startHearts() {
    setInterval(() => {
        let heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "💖";

        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = (Math.random() * 3 + 3) + "s";

        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 6000);
    }, 250);
}

/* Day-Night Cycle */
function startDayNightCycle() {
    const page = document.getElementById("page2");

    setInterval(() => {
        page.classList.toggle("night");

        if (page.classList.contains("night")) {
            createStars();
        } else {
            removeStars();
        }
    }, 8000);
}

/* Stars */
function createStars() {
    for (let i = 0; i < 80; i++) {
        let star = document.createElement("div");
        star.classList.add("star");

        star.style.left = Math.random() * 100 + "vw";
        star.style.top = Math.random() * 100 + "vh";

        document.body.appendChild(star);
    }
}

function removeStars() {
    document.querySelectorAll(".star").forEach(s => s.remove());
}
</script>

</body>
</html>
