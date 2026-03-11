# exam<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Exam Warden Pro - Physics OSN</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f4f7f6; user-select: none; -webkit-user-select: none; }
        #lock-screen { display: none; position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: #000; color: #ff0000; text-align: center; z-index: 10000; padding-top: 20%; }
        .container { max-width: 500px; margin: auto; background: white; min-height: 100vh; padding: 20px; position: relative; }
        .card { display: none; padding: 20px; border: 1px solid #ddd; border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); margin-top: 20px; }
        .card.active { display: block; }
        .header { display: flex; justify-content: space-between; align-items: center; background: #2c3e50; color: white; padding: 10px; border-radius: 5px; position: sticky; top: 0; z-index: 100; }
        .nav-btns { display: flex; justify-content: space-between; margin-top: 20px; }
        button { padding: 12px 20px; border: none; border-radius: 5px; font-weight: bold; cursor: pointer; }
        .btn-next { background: #3498db; color: white; }
        .btn-prev { background: #95a5a6; color: white; }
        .btn-submit { background: #27ae60; color: white; width: 100%; margin-top: 20px; display: none; }
        input[type="password"] { width: 80%; padding: 10px; margin-top: 20px; background: #222; color: white; border: 1px solid red; text-align: center; }
    </style>
</head>
<body oncontextmenu="return false;">

    <div id="lock-screen">
        <h1>🔒 DEVICE LOCKED</h1>
        <p>Pelanggaran: Terdeteksi pindah tab!</p>
        <input type="password" id="passInput" placeholder="Password Pengawas">
        <button onclick="unlock()" style="background: red; color: white; margin-top: 10px;">UNLOCK</button>
    </div>

    <div class="container" id="main-content">
        <div class="header">
            <span>Ujian Fisika</span>
            <span id="timer">30:00</span>
        </div>

        <div id="exam-container">
            <div class="card active" data-q="1">
                <h3>Soal 1</h3>
                <p>Benda jatuh bebas dari ketinggian h. Berapa kecepatannya saat menyentuh tanah?</p>
                <input type="radio" name="q1" value="A"> $\sqrt{gh}$ <br>
                <input type="radio" name="q1" value="B"> $\sqrt{2gh}$ <br>
                <input type="radio" name="q1" value="C"> $2gh$
            </div>
            <div class="card" data-q="2">
                <h3>Soal 2</h3>
                <p>Dimensi dari gaya adalah...</p>
                <input type="radio" name="q2" value="A"> $[M][L][T]^{-2}$ <br>
                <input type="radio" name="q2" value="B"> $[M][L][T]^{-1}$ <br>
                <input type="radio" name="q2" value="C"> $[M][L]^2[T]^{-2}$
            </div>
            </div>

        <div class="nav-btns">
            <button class="btn-prev" id="prevBtn" onclick="changeQuestion(-1)" disabled>Back</button>
            <button class="btn-next" id="nextBtn" onclick="changeQuestion(1)">Next</button>
        </div>
        
        <button class="btn-submit" id="submitBtn" onclick="submitExam()">KIRIM JAWABAN</button>
    </div>

    <script>
        const KEY = "110423";
        const NOMOR_WA = "628xxxxxxxxxx"; // <--- GANTI JADI NOMOR LO
        let currentQ = 1;
        let totalQ = 2; // Ganti jadi 15 kalau soalnya sudah lo input semua
        let timeLeft = 30 * 60; // 30 Menit

        // Timer Logic
        let timerInterval = setInterval(() => {
            let mins = Math.floor(timeLeft / 60);
            let secs = timeLeft % 60;
            document.getElementById('timer').innerText = `${mins}:${secs < 10 ? '0' : ''}${secs}`;
            if (timeLeft <= 0) {
                clearInterval(timerInterval);
                submitExam();
            }
            timeLeft--;
        }, 1000);

        function changeQuestion(step) {
            document.querySelector(`.card[data-q="${currentQ}"]`).classList.remove('active');
            currentQ += step;
            document.querySelector(`.card[data-q="${currentQ}"]`).classList.add('active');
            
            document.getElementById('prevBtn').disabled = currentQ === 1;
            document.getElementById('nextBtn').style.display = currentQ === totalQ ? 'none' : 'block';
            document.getElementById('submitBtn').style.display = currentQ === totalQ ? 'block' : 'none';
        }

        document.addEventListener("visibilitychange", () => {
            if (document.hidden) {
                localStorage.setItem("locked", "true");
                showLock();
            }
        });

        function showLock() {
            document.getElementById('lock-screen').style.display = 'block';
            document.getElementById('main-content').style.display = 'none';
        }

        function unlock() {
            if (document.getElementById('passInput').value === KEY) {
                localStorage.removeItem("locked");
                document.getElementById('lock-screen').style.display = 'none';
                document.getElementById('main-content').style.display = 'block';
            } else { alert("Salah!"); }
        }

        function submitExam() {
            let answers = "";
            for(let i=1; i<=totalQ; i++) {
                let val = document.querySelector(`input[name="q${i}"]:checked`)?.value || "Kosong";
                answers += `No ${i}: ${val}%0A`;
            }
            let url = `https://wa.me/${NOMOR_WA}?text=Hasil Ujian OSN%0A%0A${answers}`;
            window.location.href = url;
        }

        window.onload = () => { if(localStorage.getItem("locked")) showLock(); };
    </script>
</body>
</html>
