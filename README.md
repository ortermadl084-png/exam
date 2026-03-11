# exam <!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Exam Warden Pro - 15 Soal</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: sans-serif; background: #f4f7f6; user-select: none; -webkit-user-select: none; }
        #lock-screen { display: none; position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: #000; color: red; text-align: center; z-index: 10000; padding-top: 20%; }
        .container { max-width: 500px; margin: auto; background: white; min-height: 100vh; padding: 20px; }
        .header { display: flex; justify-content: space-between; background: #2c3e50; color: white; padding: 15px; border-radius: 5px; position: sticky; top: 0; }
        .card { display: none; padding: 20px; border: 1px solid #ddd; border-radius: 10px; margin-top: 20px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .card.active { display: block; }
        .nav-btns { display: flex; justify-content: space-between; margin-top: 30px; }
        button { padding: 12px 25px; border: none; border-radius: 5px; font-weight: bold; cursor: pointer; }
        .btn-next { background: #3498db; color: white; }
        .btn-prev { background: #95a5a6; color: white; }
        .btn-submit { background: #27ae60; color: white; width: 100%; margin-top: 20px; display: none; }
        input[type="password"] { width: 80%; padding: 12px; margin-top: 20px; background: #222; color: white; border: 1px solid red; text-align: center; }
        .option { display: block; padding: 10px; margin: 5px 0; background: #eee; border-radius: 5px; }
    </style>
</head>
<body oncontextmenu="return false;">

    <div id="lock-screen">
        <h1>🔒 DEVICE LOCKED</h1>
        <p>Terdeteksi pindah tab!</p>
        <input type="password" id="passInput" placeholder="Password Pengawas">
        <button onclick="unlock()" style="background: red; color: white; margin-top: 10px; padding: 10px;">UNLOCK</button>
    </div>

    <div class="container" id="main-content">
        <div class="header">
            <span>Ujian Fisika XI</span>
            <span id="timer">30:00</span>
        </div>

        <div id="exam-container">
            <div class="card active" data-q="1"><h3>Soal 1</h3><p>Besaran yang memiliki nilai dan arah adalah...</p>
                <label class="option"><input type="radio" name="q1" value="A"> Vektor</label>
                <label class="option"><input type="radio" name="q1" value="B"> Skalar</label></div>
            
            <div class="card" data-q="2"><h3>Soal 2</h3><p>Satuan SI untuk suhu adalah...</p>
                <label class="option"><input type="radio" name="q2" value="A"> Kelvin</label>
                <label class="option"><input type="radio" name="q2" value="B"> Celsius</label></div>

            <div class="card" data-q="3"><h3>Soal 3</h3><p>Hukum I Newton disebut hukum...</p>
                <label class="option"><input type="radio" name="q3" value="A"> Inersia</label>
                <label class="option"><input type="radio" name="q3" value="B"> Aksi-Reaksi</label></div>

            <div class="card" data-q="4"><h3>Soal 4</h3><p>Dimensi dari panjang adalah...</p>
                <label class="option"><input type="radio" name="q4" value="A"> [L]</label>
                <label class="option"><input type="radio" name="q4" value="B"> [M]</label></div>

            <div class="card" data-q="5"><h3>Soal 5</h3><p>Alat ukur massa adalah...</p>
                <label class="option"><input type="radio" name="q5" value="A"> Neraca</label>
                <label class="option"><input type="radio" name="q5" value="B"> Jangka Sorong</label></div>

            <div class="card" data-q="6"><h3>Soal 6</h3><p>Gaya gravitasi ditemukan oleh...</p>
                <label class="option"><input type="radio" name="q6" value="A"> Newton</label>
                <label class="option"><input type="radio" name="q6" value="B"> Einstein</label></div>

            <div class="card" data-q="7"><h3>Soal 7</h3><p>Satuan daya adalah...</p>
                <label class="option"><input type="radio" name="q7" value="A"> Watt</label>
                <label class="option"><input type="radio" name="q7" value="B"> Joule</label></div>

            <div class="card" data-q="8"><h3>Soal 8</h3><p>Energi kinetik rumusnya...</p>
                <label class="option"><input type="radio" name="q8" value="A"> 1/2 mv²</label>
                <label class="option"><input type="radio" name="q8" value="B"> mgh</label></div>

            <div class="card" data-q="9"><h3>Soal 9</h3><p>Satuan gaya adalah...</p>
                <label class="option"><input type="radio" name="q9" value="A"> Newton</label>
                <label class="option"><input type="radio" name="q9" value="B"> Pascal</label></div>

            <div class="card" data-q="10"><h3>Soal 10</h3><p>Perubahan posisi disebut...</p>
                <label class="option"><input type="radio" name="q10" value="A"> Jarak</label>
                <label class="option"><input type="radio" name="q10" value="B"> Perpindahan</label></div>

            <div class="card" data-q="11"><h3>Soal 11</h3><p>Tekanan rumusnya...</p>
                <label class="option"><input type="radio" name="q11" value="A"> P = F/A</label>
                <label class="option"><input type="radio" name="q11" value="B"> P = m.g</label></div>

            <div class="card" data-q="12"><h3>Soal 12</h3><p>Bunyi merambat paling cepat di...</p>
                <label class="option"><input type="radio" name="q12" value="A"> Benda Padat</label>
                <label class="option"><input type="radio" name="q12" value="B"> Udara</label></div>

            <div class="card" data-q="13"><h3>Soal 13</h3><p>Cepat rambat cahaya adalah...</p>
                <label class="option"><input type="radio" name="q13" value="A"> 3x10^8 m/s</label>
                <label class="option"><input type="radio" name="q13" value="B"> 340 m/s</label></div>

            <div class="card" data-q="14"><h3>Soal 14</h3><p>Hukum Ohm adalah...</p>
                <label class="option"><input type="radio" name="q14" value="A"> V = I.R</label>
                <label class="option"><input type="radio" name="q14" value="B"> P = V.I</label></div>

            <div class="card" data-q="15"><h3>Soal 15</h3><p>Benda jatuh bebas v0-nya adalah...</p>
                <label class="option"><input type="radio" name="q15" value="A"> Nol</label>
                <label class="option"><input type="radio" name="q15" value="B"> 10 m/s</label></div>
        </div>

        <div class="nav-btns">
            <button class="btn-prev" id="prevBtn" onclick="changeQuestion(-1)" disabled>Back</button>
            <button class="btn-next" id="nextBtn" onclick="changeQuestion(1)">Next</button>
        </div>
        <button class="btn-submit" id="submitBtn" onclick="submitExam()">KIRIM JAWABAN (WA)</button>
    </div>

    <script>
        const KEY = "110423";
        const NOMOR_WA = "085715349712"; // GANTI DENGAN NOMOR WA LO
        let currentQ = 1;
        let totalQ = 15; 
        let timeLeft = 30 * 60;

        // Timer
        setInterval(() => {
            let m = Math.floor(timeLeft / 60);
            let s = timeLeft % 60;
            document.getElementById('timer').innerText = `${m}:${s < 10 ? '0' : ''}${s}`;
            if (timeLeft <= 0) submitExam();
            timeLeft--;
        }, 1000);

        function changeQuestion(step) {
            document.querySelector(`.card[data-q="${currentQ}"]`).classList.remove('active');
            currentQ += step;
            document.querySelector(`.card[data-q="${currentQ}"]`).classList.add('active');
            document.getElementById('prevBtn').disabled = (currentQ === 1);
            document.getElementById('nextBtn').style.display = (currentQ === totalQ) ? 'none' : 'block';
            document.getElementById('submitBtn').style.display = (currentQ === totalQ) ? 'block' : 'none';
        }

        document.addEventListener("visibilitychange", () => {
            if (document.hidden && currentQ <= totalQ) {
                localStorage.setItem("lock", "true");
                showLock();
            }
        });

        function showLock() {
            document.getElementById('lock-screen').style.display = 'block';
            document.getElementById('main-content').style.display = 'none';
        }

        function unlock() {
            if (document.getElementById('passInput').value === KEY) {
                localStorage.removeItem("lock");
                document.getElementById('lock-screen').style.display = 'none';
                document.getElementById('main-content').style.display = 'block';
            } else { alert("Salah!"); }
        }

        function submitExam() {
            let msg = "HASIL UJIAN FISIKA:%0A";
            for(let i=1; i<=totalQ; i++){
                let ans = document.querySelector(`input[name="q${i}"]:checked`)?.value || "-";
                msg += `No ${i}: ${ans}%0A`;
            }
            window.location.href = `https://wa.me/${NOMOR_WA}?text=${msg}`;
        }

        window.onload = () => { if(localStorage.getItem("lock")) showLock(); };
    </script>
</body>
</html>
