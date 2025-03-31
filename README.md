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
        }
        @keyframes fall {
            from { transform: translateY(-10vh); opacity: 1; }
            to { transform: translateY(100vh); opacity: 0; }
        }
        .heart {
            position: fixed;
            color: red;
            font-size: 24px;
            animation: fall 2s linear infinite;
        }
        @keyframes move {
            0% { transform: translateX(0); }
            50% { transform: translateX(50px); }
            100% { transform: translateX(-50px); }
        }
    </style>
</head>
<body class="flex justify-center items-center h-screen bg-pink-200">
    <div id="start-screen" class="text-center">
        <button onclick="nextSlide()" class="px-6 py-3 bg-blue-500 text-white rounded-lg">Start</button>
    </div><div id="sorry-screen" class="hidden text-center">
    <h1 class="text-3xl font-bold mb-4">I'm Sorry Tanishuu Suar</h1>
    <button onclick="showHearts()" id="ok-btn" class="px-6 py-3 bg-green-500 text-white rounded-lg">It's OK</button>
    <button onclick="moveNotOk()" id="not-ok-btn" class="px-6 py-3 bg-red-500 text-white rounded-lg ml-4">Not OK</button>
</div>

<script>
    function nextSlide() {
        document.getElementById("start-screen").classList.add("hidden");
        document.getElementById("sorry-screen").classList.remove("hidden");
    }
    
    function showHearts() {
        document.getElementById("sorry-screen").innerHTML = "<h1 class='text-4xl font-bold mb-4'>I Love Youu Kiddo ❤️</h1>";
        for (let i = 0; i < 50; i++) {
            let heart = document.createElement("div");
            heart.innerHTML = "❤️";
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
</script>

</body>
</html>
