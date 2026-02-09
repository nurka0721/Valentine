<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>A Special Message for You 💍</title>
    <style>
        :root { --primary: #ff4d6d; --secondary: #fff0f3; }
        body { margin: 0; padding: 0; background: var(--secondary); font-family: 'SF Pro Display', -apple-system, sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; overflow: hidden; text-align: center; }
        #card { background: white; padding: 30px; border-radius: 25px; box-shadow: 0 15px 35px rgba(255, 77, 109, 0.2); width: 85%; max-width: 350px; position: relative; z-index: 10; }
        h1 { color: var(--primary); font-size: 1.8rem; margin-bottom: 10px; }
        p { color: #555; font-size: 1.1rem; line-height: 1.4; margin-bottom: 25px; }
        .btn-container { display: flex; justify-content: space-around; align-items: center; position: relative; height: 60px; }
        .btn { border: none; padding: 12px 30px; font-size: 1.2rem; border-radius: 50px; cursor: pointer; transition: 0.3s; font-weight: bold; }
        #yesBtn { background: var(--primary); color: white; box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4); }
        #noBtn { background: #eee; color: #888; position: absolute; }
        #celebration { display: none; flex-direction: column; align-items: center; }
        .heart { position: fixed; font-size: 2rem; pointer-events: none; animation: fly 3s linear forwards; }
        @keyframes fly { to { transform: translateY(-100vh) rotate(360deg); opacity: 0; } }
    </style>
</head>
<body>
    <div id="card">
        <div id="question">
            <h1 id="title">Hey Beautiful... 💍</h1>
            <p id="text">I want to spend every Valentine's Day making you smile. Will you be my Valentine?</p>
            <div class="btn-container">
                <button id="yesBtn" class="btn" onclick="celebrate()">YES</button>
                <button id="noBtn" class="btn" onmouseover="moveNo()" onclick="moveNo()">No</button>
            </div>
        </div>
        <div id="celebration">
            <h1>I KNEW IT! ❤️</h1>
            <p>You've made me the luckiest person alive. Get ready for a night you'll never forget!</p>
            <span style="font-size: 4rem;">💍🌹👩‍❤️‍👨</span>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const card = document.getElementById('card');
        const question = document.getElementById('question');
        const celebration = document.getElementById('celebration');

        // The "Emotional Kill Shot" - No button dodges the touch/click
        function moveNo() {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        }

        function celebrate() {
            question.style.display = 'none';
            celebration.style.display = 'flex';
            setInterval(createHeart, 150);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = ['❤️','💖','💗','🌹','💍'][Math.floor(Math.random()*5)];
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.top = '100vh';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 3000);
        }
    </script>
</body>
</html>
