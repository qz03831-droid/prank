<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Untuk Kamu</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      text-align: center;
      height: 100vh;
      overflow: hidden;
      color: white;

      /* 🌅 BACKGROUND SUNSET */
      background: linear-gradient(to top, #ff7e5f, #feb47b, #ffcc70);
    }

    .card {
      position: absolute;
      top: 30%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(0,0,0,0.3);
      padding: 30px;
      border-radius: 20px;
      backdrop-filter: blur(10px);
    }

    button {
      position: absolute;
      padding: 12px 25px;
      border: none;
      border-radius: 10px;
      background: white;
      color: #ff4b5c;
      font-size: 16px;
      cursor: pointer;
    }

    #nextBtn {
      display: none;
      position: static;
      margin-top: 20px;
    }

    #memeBtn {
      display: none;
      position: static;
      margin-top: 20px;
    }

    img {
      max-width: 300px;
      display: none;
      margin-top: 20px;
      border-radius: 15px;
    }
  </style>
</head>
<body>

<div class="card" id="text">
  <h1>Hai Rustappen Fans</h1>
  <p>Aku mau kasih sesuatu untuk kamu</p>
</div>

<button id="btn">Klik aku</button>

<div style="position:absolute; top:60%; left:50%; transform:translateX(-50%); text-align:center;">
  <button id="nextBtn">Lanjut 👉</button>
  <button id="memeBtn">Lihat sesuatu</button>
  <br>
  <img id="meme" src="meme.jpg">
</div>

<audio id="laughSound" src="https://www.myinstants.com/media/sounds/evil-laugh.mp3"></audio>

<script>
  const btn = document.getElementById("btn");
  const text = document.getElementById("text");
  const nextBtn = document.getElementById("nextBtn");
  const memeBtn = document.getElementById("memeBtn");
  const meme = document.getElementById("meme");
  const laugh = document.getElementById("laughSound");

  let clickCount = 0;
  let gameActive = true;
  let messageIndex = 0;

  const messages = [
    "Teruntuk Fans Max yang bersedih wkwk",
    "ini Tak Kasih sesuatu buatmu",
    "Siap ya..."
  ];

  btn.style.top = "70%";
  btn.style.left = "50%";


  // hitung klik
  btn.addEventListener("click", () => {
    clickCount++;

    if (clickCount >= 7) { // lebih cepat masuk biar ga capek
      gameActive = false;
      btn.style.display = "none";
      nextBtn.style.display = "inline-block";
      text.innerHTML = `<h1>${messages[0]}</h1>`;
      messageIndex = 1;
    }
  });

  // tombol lanjut manual
  nextBtn.addEventListener("click", () => {
    if (messageIndex < messages.length) {
      text.innerHTML = `<h1>${messages[messageIndex]}</h1>`;
      messageIndex++;
    } else {
      nextBtn.style.display = "none";
      memeBtn.style.display = "inline-block";
    }
  });

  // tombol terakhir
  memeBtn.addEventListener("click", () => {
    document.body.style.background = "black";
    text.innerHTML = "<h1>Bunga Untukmu wkwk</h1>";
    meme.style.display = "block";
    laugh.play();
  });
</script>

</body>
</html>
