<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I'm Sorry</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            background-color: pink;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            position: relative;
            transition: background-color 0.5s ease;
        }
        .heart {
            position: absolute;
            font-size: 2rem;
            animation: float 2s ease-in-out infinite;
        }
        @keyframes float {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-100px); opacity: 0; }
        }
        .button-container {
            display: flex;
            justify-content: space-between;
            width: 100%;
            max-width: 500px;
            margin-top: 20px;
        }
        .heart-theme {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
        }
        .floating-heart {
            position: absolute;
            font-size: 2rem;
            color: red;
            animation: heart-float 5s linear infinite;
        }
        @keyframes heart-float {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-150px); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="heart-theme" id="heart-theme"></div><div id="start-screen" class="text-center">
    <button onclick="nextSlide()" class="px-6 py-3 bg-blue-500 text-white rounded-lg">Start</button>
</div>

<div id="sorry-screen" class="hidden text-center">
    <h1 class="text-3xl font-bold mb-4">I'm Sorry Tanishuu Suar</h1>
    <button onclick="showNextScreen()" id="ok-btn" class="px-6 py-3 bg-green-500 text-white rounded-lg">It's OK</button>
    <button onclick="moveNotOk()" id="not-ok-btn" class="px-6 py-3 bg-red-500 text-white rounded-lg ml-4">Not OK</button>
</div>

<div id="love-screen" class="hidden text-center">
    <h1 class="text-4xl font-bold mb-4">I Love Uhhh Kiddo ❤️<br>And Sorry for Yesterday's Night</h1>
    <div class="button-container">
        <button onclick="showHearts('🖤', 'black')" class="px-6 py-3 bg-gray-800 text-white rounded-full">I Hate You Too</button>
        <button onclick="showHearts('💖', 'pink')" class="px-6 py-3 bg-red-500 text-white rounded-full">I Love Uhhh Too</button>
    </div>
</div>

<script>
    function nextSlide() {
        document.getElementById("start-screen").classList.add("hidden");
        document.getElementById("sorry-screen").classList.remove("hidden");
    }
    
    function showNextScreen() {
        document.getElementById("sorry-screen").classList.add("hidden");
        document.getElementById("love-screen").classList.remove("hidden");
        document.body.style.backgroundColor = "pink";
    }
    
    function showHearts(type, bgColor) {
        document.body.style.backgroundColor = bgColor;
        for (let i = 0; i < 50; i++) {
            let heart = document.createElement("div");
            heart.innerHTML = type;
            heart.classList.add("heart");
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.animationDuration = (Math.random() * 2 + 2) + "s";
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 2000);
        }
    }
    
    function moveNotOk() {
        let btn = document.getElementById("not-ok-btn");
        let randomX = Math.random() * (window.innerWidth - 100);
        let randomY = Math.random() * (window.innerHeight - 100);
        btn.style.position = "absolute";
        btn.style.left = randomX + "px";
        btn.style.top = randomY + "px";
    }

    function generateFlyingHearts() {
        for (let i = 0; i < 30; i++) {
            let heart = document.createElement("div");
            heart.innerHTML = "❤️";
            heart.classList.add("floating-heart");
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.top = Math.random() * 100 + "vh";
            heart.style.animationDuration = (Math.random() * 5 + 3) + "s";
            document.body.appendChild(heart);
        }
    }
    
    window.onload = generateFlyingHearts;
</script>

</body>
</html>
