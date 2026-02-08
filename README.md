# Nni-chocolate-day
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My NNI: The Gold Edition</title>
    <style>
        :root {
            --dark-cocoa: #2d1b15;
            --gold: #d4af37;
            --silk: #fff8f0;
            --heart-red: #ff4d6d;
        }

        body {
            background: radial-gradient(circle, #3e2723, #1a0f0d);
            color: var(--silk);
            font-family: 'Trebuchet MS', sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .main-card {
            background: rgba(45, 27, 21, 0.9);
            border: 2px solid var(--gold);
            border-radius: 30px;
            padding: 30px;
            text-align: center;
            max-width: 500px;
            width: 100%;
            box-shadow: 0 0 50px rgba(0,0,0,0.8);
            backdrop-filter: blur(10px);
        }

        /* Photo Gallery */
        .gallery {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin: 20px 0;
        }
        .photo-slot {
            width: 80px;
            height: 80px;
            background: var(--gold);
            border-radius: 15px;
            overflow: hidden;
            border: 2px solid white;
        }
        .photo-slot img { width: 100%; height: 100%; object-fit: cover; }

        /* Compliment Box */
        .fortune-box {
            background: rgba(212, 175, 55, 0.1);
            border: 1px dashed var(--gold);
            padding: 15px;
            border-radius: 15px;
            margin: 20px 0;
        }

        /* Voucher */
        .voucher {
            background: linear-gradient(45deg, var(--gold), #f9e29c);
            color: var(--dark-cocoa);
            padding: 15px;
            border-radius: 10px;
            font-weight: bold;
            display: none;
            margin-top: 20px;
            border: 2px dashed #5d4037;
        }

        /* Buttons */
        .btn-gold {
            background: var(--gold);
            color: var(--dark-cocoa);
            padding: 12px 25px;
            border-radius: 50px;
            border: none;
            font-weight: bold;
            cursor: pointer;
            margin: 10px;
            transition: 0.3s;
        }
        .btn-gold:hover { transform: scale(1.1); box-shadow: 0 0 15px var(--gold); }

        #noBtn { background: #555; color: white; position: absolute; }

        .meter-bar {
            width: 100%; height: 15px; background: #444; border-radius: 10px; margin: 10px 0;
        }
        .fill {
            height: 100%; width: 0%; background: var(--heart-red); border-radius: 10px; transition: 2s;
        }

        @keyframes float {
            0% { transform: translateY(0); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100vh); opacity: 0; }
        }
        .heart { position: fixed; color: var(--heart-red); pointer-events: none; animation: float 3s linear forwards; }
    </style>
</head>
<body>

    <div class="main-card">
        <h1 style="color: var(--gold); letter-spacing: 2px;">THE NNI PRIVILEGE ✨</h1>
        
        <div class="gallery">
            <div class="photo-slot"><img src="https://via.placeholder.com/80?text=Us" alt="You"></div>
            <div class="photo-slot"><img src="https://via.placeholder.com/80?text=❤️" alt="Me"></div>
            <div class="photo-slot"><img src="https://via.placeholder.com/80?text=Smile" alt="Happy"></div>
        </div>

        <p>A personal portal for the sweetest person ever.</p>

        <div class="fortune-box">
            <p id="compliment">"Click the button for a secret compliment..."</p>
            <button class="btn-gold" style="padding: 5px 15px; font-size: 12px;" onclick="newCompliment()">New Secret</button>
        </div>

        <hr style="border-color: #444;">

        <div id="game-zone">
            <h3>Do you love me as much as chocolate?</h3>
            <button class="btn-gold" onclick="startScanner()" id="yesBtn">YES, MORE!</button>
            <button class="btn-gold" id="noBtn" onmouseover="moveNo()">NO</button>
        </div>

        <div id="scanner" style="display:none;">
            <p>Scanning Sweetness Levels...</p>
            <div class="meter-bar"><div class="fill" id="fill"></div></div>
            <p id="status">Reading NNI's heart...</p>
            
            <div class="voucher" id="voucher">
                🎟️ OFFICIAL VOUCHER 🎟️<br>
                Valid for: 1 Large Chocolate Box & 100 Kisses<br>
                <small>Signed: Your AI Assistant (On behalf of your Human)</small>
            </div>
        </div>
    </div>

    <script>
        const compliments = [
            "Your smile is brighter than a golden wrapper! ✨",
            "You are the 'Limited Edition' of humans. ❤️",
            "If you were a chocolate, you'd be the most expensive one! 🍫",
            "My favorite notification is your name on my screen. 📱",
            "You're the caramel filling to my dark chocolate. 🍯"
        ];

        function newCompliment() {
            const text = document.getElementById('compliment');
            text.innerText = compliments[Math.floor(Math.random() * compliments.length)];
            createHeart();
        }

        function moveNo() {
            const btn = document.getElementById('noBtn');
            btn.style.left = Math.random() * 80 + 'vw';
            btn.style.top = Math.random() * 80 + 'vh';
        }

        function startScanner() {
            document.getElementById('game-zone').style.display = 'none';
            document.getElementById('scanner').style.display = 'block';
            
            setTimeout(() => {
                document.getElementById('fill').style.width = '100%';
                document.getElementById('status').innerText = "CALIBRATION ERROR: Too sweet to measure! 😍";
                document.getElementById('voucher').style.display = 'block';
                setInterval(createHeart, 200);
            }, 500);
        }

        function createHeart() {
            const h = document.createElement('div');
            h.innerHTML = '❤️';
            h.className = 'heart';
            h.style.left = Math.random() * 100 + 'vw';
            h.style.top = '100vh';
            h.style.fontSize = (Math.random() * 20 + 20) + 'px';
            document.body.appendChild(h);
            setTimeout(() => h.remove(), 3000);
        }
    </script>
</body>
</html>
