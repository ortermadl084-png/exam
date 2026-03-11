# exam <!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sistem Ujian Anti-Cheat V4</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Arial', sans-serif; background: #f0f2f5; user-select: none; -webkit-user-select: none; }
        
        /* Layar Kunci (Overlay) */
        #lock-screen { 
            display: none; position: fixed; top: 0; left: 0; 
            width: 100vw; height: 100vh; background: #1a1a1a; 
            color: #ff4d4d; text-align: center; z-index: 10000; padding: 15% 10%;
        }

        .container { max-width: 600px; margin: auto; background: white; min-height: 100vh; padding: 20px; }
        .card { background: #fff; border: 1px solid #ddd; padding: 20px; border-radius: 8px; margin-bottom: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); }
        .btn-start { width: 100%; padding: 15px; background: #007bff; color: white; border: none; border-radius: 5px; font-weight: bold; font-size: 16px; }
        input[type="password"] { width: 100%; padding: 12px; margin-top: 20px; border: 1px solid #ff4d4d; border-radius: 5px; background: #333; color: white; text-align: center; }
        .btn-unlock { width: 100%; padding: 12px; margin-top: 10px; background: #ff4d4d; color: white; border: none; border-radius: 5px; font-weight: bold; }
    </style>
</head>
<body oncontextmenu="return false;">

    <div id="lock-screen">
        <h1 style="font-size: 40px;">🚫 TERKUNCI</h1>
        <p style="margin-top: 20px; color: #ccc;">Kamu mencoba keluar atau membuka aplikasi lain. Pelanggaran tercatat!</p>
        <input type="password" id="passInput" placeholder="Password Pengawas">
        <button class="btn-unlock" onclick="unlock()">BUKA KUNCI</button>
    </div>

    <div class="container" id="main-content">
        <div id="setup-screen">
            <h2 style="color: #007bff; margin-bottom: 10px;">Persiapan Ujian</h2>
            <p style="margin-bottom: 20px; color: #666;">Klik tombol di bawah untuk memulai. Jangan keluar dari halaman selama ujian berlangsung.</p>
            <button class="btn-start" onclick="start()">MULAI SEKARANG</button>
        </div>

        <div id="exam-screen" style="display:none;">
            <div style="background: #333; color: white; padding: 10px; border-radius: 5px; margin-bottom: 20px;">
                Status: <strong>Sedang Mengawasi...</strong>
            </div>
            
            <div class="card">
                <p><strong>Soal 1:</strong> Jika $a(t) = 6t$, tentukan kecepatan $v$ saat $t = 3$ detik jika $v(0) = 2$.</p>
                <input type="radio" name="q1"> 25 m/s <br>
                <input type="radio" name="q1"> 29 m/s <br>
                <input type="radio" name="q1"> 31 m/s
            </div>

            <div class="card">
                <p><strong>Soal 2:</strong> Apakah yang dimaksud dengan Hukum Inersia?</p>
                <input type="radio" name="q2"> Hukum I Newton <br>
                <input type="radio" name="q2"> Hukum II Newton <br>
                <input type="radio" name="q2"> Hukum III Newton
            </div>
        </div>
    </div>

    <script>
        const KEY = "110423"; // Password yang lo minta

        // Fungsi Mulai
        function start() {
            document.getElementById('setup-screen').style.display = 'none';
            document.getElementById('exam-screen').style.display = 'block';
            localStorage.setItem("exam_active", "true");
            
            // Masuk Fullscreen (Biaya biar lebih pro)
            if (document.documentElement.requestFullscreen) {
                document.documentElement.requestFullscreen();
            }
        }

        // Deteksi Pindah Tab / Tombol Home
        document.addEventListener("visibilitychange", function() {
            if (document.hidden && localStorage.getItem("exam_active") === "true") {
                lock();
            }
        });

        function lock() {
            localStorage.setItem("is_locked", "true");
            document.getElementById('lock-screen').style.display = 'block';
            document.getElementById('main-content').style.display = 'none';
        }

        function unlock() {
            const input = document.getElementById('passInput').value;
            if (input === KEY) {
                localStorage.removeItem("is_locked");
                document.getElementById('lock-screen').style.display = 'none';
                document.getElementById('main-content').style.display = 'block';
                document.getElementById('passInput').value = ""; // reset input
            } else {
                alert("Salah Bruh!");
            }
        }

        // Cek status saat loading (Anti-Refresh)
        window.onload = function() {
            if (localStorage.getItem("is_locked") === "true") {
                lock();
            }
        };
    </script>
</body>
</html>
