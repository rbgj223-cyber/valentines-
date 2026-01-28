<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Summer ❤️</title>

  <style>
    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #ff6fa5, #ff9acb);
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }

    .container {
      background: white;
      padding: 30px 25px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 15px 35px rgba(0,0,0,0.2);
      max-width: 90%;
      z-index: 2;
    }

    h1 {
      color: #ff3b7f;
      font-size: 2rem;
      margin-bottom: 20px;
    }

    .buttons {
      position: relative;
      height: 90px;
    }

    button {
      padding: 15px 25px;
      font-size: 1rem;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: transform 0.15s ease;
    }

    #yes {
      background: #ff3b7f;
      color: white;
      margin-right: 15px;
    }

    #no {
      background: #eee;
      position: absolute;
      left: 120px;
    }

    #message {
      margin-top: 20px;
      font-size: 1.2rem;
      color: #ff3b7f;
    }

    .heart {
      position: absolute;
      bottom: -20px;
      color: rgba(255, 255, 255, 0.8);
      animation: floatUp linear forwards;
      pointer-events: none;
    }

    @keyframes floatUp {
      to {
        transform: translateY(-110vh);
        opacity: 0;
      }
    }

    .confetti {
      position: absolute;
      width: 8px;
      height: 8px;
      background: red;
      animation: fall linear forwards;
      pointer-events: none;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(720deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Summer, will you be my Valentine? ❤️</h1>

    <div class="buttons">
      <button id="yes">Yes 💖</button>
      <button id="no">No 🙃</button>
    </div>

    <div id="message"></div>
  </div>

  <script>
    const yesBtn = document.getElementById("yes");
    const noBtn = document.getElementById("no");
    const message = document.getElementById("message");

    yesBtn.addEventListener("click", () => {
      message.innerText = "YAY!! 💕 I’m so happy, Summer 😍";
      launchConfetti();
    });

    function moveNo() {
      const container = document.querySelector(".container");
      const rect = container.getBoundingClientRect();

      const x = Math.random() * (rect.width - noBtn.offsetWidth);
      const y = Math.random() * (rect.height - noBtn.offsetHeight);

      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    }

    noBtn.addEventListener("mouseover", moveNo);
    noBtn.addEventListener("touchstart", moveNo);

    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.innerText = "❤️";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = Math.random() * 20 + 15 + "px";
      heart.style.animationDuration = Math.random() * 3 + 4 + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 7000);
    }

    setInterval(createHeart, 300);

    function launchConfetti() {
      for (let i = 0; i < 120; i++) {
        const confetti = document.createElement("div");
        confetti.classList.add("confetti");

        const colors = ["#ff3b7f", "#ff9acb", "#ffd1dc", "#fff"];
        confetti.style.background =
          colors[Math.floor(Math.random() * colors.length)];

        confetti.style.left = Math.random() * 100 + "vw";
        confetti.style.top = "-10px";
        confetti.style.animationDuration =
          Math.random() * 3 + 2 + "s";

        document.body.appendChild(confetti);
        setTimeout(() => confetti.remove(), 5000);
      }
    }
  </script>

</body>
</html>
