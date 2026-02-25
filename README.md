# website-Kejutan-seru-seruan
web
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sebuah Kejutan Untukmu</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .container {
            text-align: center;
            padding: 40px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 30px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.2);
            max-width: 500px;
            position: relative;
        }

        h1 {
            color: #e91e63;
            font-size: 2.5em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .heart {
            font-size: 80px;
            animation: heartbeat 1s infinite;
            display: inline-block;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .message {
            font-size: 1.3em;
            color: #555;
            margin: 30px 0;
            line-height: 1.8;
            min-height: 100px;
        }

        .btn {
            background: linear-gradient(45deg, #e91e63, #ff5722);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.2em;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 20px rgba(233, 30, 99, 0.4);
            margin: 10px;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(233, 30, 99, 0.5);
        }

        .btn:active {
            transform: translateY(0);
        }

        .hidden {
            display: none;
        }

        .floating-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: -1;
        }

        .floating-heart {
            position: absolute;
            font-size: 30px;
            animation: floatUp 4s linear forwards;
            opacity: 0;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        .photo-frame {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(45deg, #ff9a9e, #fad0c4);
            margin: 0 auto 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 80px;
            border: 5px solid white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .surprise-box {
            background: #fff0f5;
            padding: 20px;
            border-radius: 20px;
            margin-top: 20px;
            border: 3px dashed #e91e63;
        }

        .countdown {
            font-size: 3em;
            color: #e91e63;
            font-weight: bold;
        }

        .final-message {
            font-size: 2em;
            color: #e91e63;
            animation: pulse 0.5s infinite alternate;
        }

        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }

        .gallery {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .gallery-item {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, #ff9a9e, #fecfef);
            border-radius: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 40px;
            animation: bounce 2s infinite;
        }

        .gallery-item:nth-child(2) { animation-delay: 0.2s; }
        .gallery-item:nth-child(3) { animation-delay: 0.4s; }
        .gallery-item:nth-child(4) { animation-delay: 0.6s; }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
    </style>
</head>
<body>
    <div class="floating-hearts" id="floatingHearts"></div>

    <div class="container" id="mainContainer">
        <!-- Halaman 1: Pembukaan -->
        <div id="page1">
            <div class="heart">💕</div>
            <h1>Hai Kamu!</h1>
            <p class="message">
                Aku punya sesuatu buat kamu...<br>
                Tapi kamu harus klik tombol di bawah dulu! 😏
            </p>
            <button class="btn" onclick="goToPage2()">Apa nih? 👀</button>
        </div>

        <!-- Halaman 2: Loading -->
        <div id="page2" class="hidden">
            <div class="photo-frame">💖</div>
            <h1>Sedang Memuat...</h1>
            <p class="message">
                Tunggu sebentar yaa...<br>
                Aku sedang menyiapkan kejutan untukmu! 💫
            </p>
            <div class="surprise-box">
                <p class="countdown" id="countdown">3</p>
            </div>
        </div>

        <!-- Halaman 3: Gallery -->
        <div id="page3" class="hidden">
            <h1>✨ Galeri Kita ✨</h1>
            <div class="gallery">
                <div class="gallery-item">📸</div>
                <div class="gallery-item">💑</div>
                <div class="gallery-item">❤️</div>
                <div class="gallery-item">🥰</div>
            </div>
            <p class="message">
                Ingat moment-moment indah kita?<br>
                Banyak ya kenangan yang sudah kita lewati... 😊
            </p>
            <button class="btn" onclick="goToPage4()">Iyaa, aku ingat! 💕</button>
        </div>

        <!-- Halaman 4: Pesan Utama -->
        <div id="page4" class="hidden">
            <div class="heart">💗</div>
            <h1>Kamulah Wanitaku! 💕</h1>
            <div class="surprise-box">
                <p class="message">
                    Kamu adalah wanita yang membuatku tersenyum setiap hari.<br><br>
                    Meskipun kadang kamu nyebelin... 😝<br>
                    Tapi aku tetap sayang kamu!<br><br>
                    Terima kasih sudah menjadi bagian dari hidupku. ❤️
                </p>
            </div>
            <button class="btn" onclick="showFinal()">Aku juga sayang kamu! 🥰</button>
        </div>

        <!-- Halaman 5: Final -->
        <div id="page5" class="hidden">
            <div style="font-size: 100px;">💍</div>
            <p class="final-message">
                KITA JODOH YA! 💑<br><br>
                <span style="font-size: 0.5em; color: #888;">
                    (Jangan lupa traktir aku makan kalau jadi 😋)
                </span>
            </p>
            <button class="btn" onclick="restart()">Iyaaa! Muat Ulang 💕</button>
        </div>
    </div>

    <script>
        // Buat hati melayang
        function createFloatingHeart() {
            const heart = document.createElement('div');
            heart.className = 'floating-heart';
            heart.innerHTML = ['💕', '💖', '💗', '💓', '❤️', '🥰'][Math.floor(Math.random() * 6)];
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 3 + 3) + 's';
            document.getElementById('floatingHearts').appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 6000);
        }

        // Buat hati setiap 500ms
        setInterval(createFloatingHeart, 500);

        // Fungsi navigasi halaman
        function goToPage2() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            
            // Countdown
            let count = 3;
            const countdownEl = document.getElementById('countdown');
            const countdownInterval = setInterval(() => {
                count--;
                countdownEl.textContent = count;
                if (count <= 0) {
                    clearInterval(countdownInterval);
                    goToPage3();
                }
            }, 1000);
        }

        function goToPage3() {
            document.getElementById('page2').classList.add('hidden');
            document.getElementById('page3').classList.remove('hidden');
        }

        function goToPage4() {
            document.getElementById('page3').classList.add('hidden');
            document.getElementById('page4').classList.remove('hidden');
        }

        function showFinal() {
            document.getElementById('page4').classList.add('hidden');
            document.getElementById('page5').classList.remove('hidden');
            
            // Buat banyak hati
            for (let i = 0; i < 30; i++) {
                setTimeout(createFloatingHeart, i * 100);
            }
        }

        function restart() {
            document.getElementById('page5').classList.add('hidden');
            document.getElementById('page1').classList.remove('hidden');
        }

        // Efek suara klik (opsional)
        document.querySelectorAll('.btn').forEach(btn => {
            btn.addEventListener('click', () => {
                // Kamu bisa tambahkan efek suara di sini
                console.log('Click!');
            });
        });
    </script>
</body>
</html>
