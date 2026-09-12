<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Happy Birthday ❤️</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      overflow: hidden;
      font-family: Arial, sans-serif;

      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;

      background:
        radial-gradient(circle at top, #b45cff, transparent 45%),
        linear-gradient(135deg, #4b0082, #7b1fa2, #9c27b0);

      color: white;
    }

    .card {
      width: 90%;
      max-width: 430px;
      padding: 35px 22px;
      border-radius: 28px;

      background: rgba(255, 255, 255, 0.13);
      backdrop-filter: blur(12px);

      box-shadow: 0 20px 60px rgba(0, 0, 0, 0.35);

      position: relative;
      z-index: 2;
    }

    h1 {
      margin: 0 0 15px;

      font-size: clamp(42px, 12vw, 68px);

      text-shadow:
        0 4px 15px rgba(0, 0, 0, 0.35);
    }

    .arrow {
      font-size: 42px;
      margin: 10px 0;

      animation: bounce 1s infinite;
    }

    .question {
      font-size: 21px;
      line-height: 1.6;
      margin: 15px 0 22px;
    }

    button {
      border: none;
      border-radius: 50px;

      padding: 14px 30px;

      margin: 7px;

      font-size: 18px;
      font-weight: bold;

      cursor: pointer;

      transition: transform 0.2s;
    }

    #yes {
      background: white;
      color: #7b1fa2;

      box-shadow: 0 5px 20px rgba(0,0,0,0.2);
    }

    #yes:hover {
      transform: scale(1.08);
    }

    #no {
      background: #eeeeee;
      color: #555;

      position: relative;
    }

    #message {
      display: none;

      margin-top: 20px;

      font-size: 23px;
      font-weight: bold;

      line-height: 1.6;
    }

    .shayari {
      margin-top: 15px;

      font-size: 18px;
      font-weight: normal;

      line-height: 1.8;
    }

    .heart {
      position: fixed;

      top: -50px;

      pointer-events: none;

      z-index: 10;

      animation: fall linear forwards;
    }

    @keyframes bounce {
      0%, 100% {
        transform: translateY(0);
      }

      50% {
        transform: translateY(12px);
      }
    }

    @keyframes fall {
      from {
        transform:
          translateY(-50px)
          rotate(0deg);

        opacity: 1;
      }

      to {
        transform:
          translateY(110vh)
          rotate(360deg);

        opacity: 0;
      }
    }
  </style>
</head>

<body>

  <div class="card">

    <!-- Birthday -->
    <h1>Happy Birthday ❤️</h1>

    <div class="arrow">
      ⬇️
    </div>

    <!-- Question -->
    <div class="question">

      अगर तुम मुझसे प्यार करती हो... ❤️
      <br>

      तो नीचे बताओ...

    </div>

    <button id="yes">
      YES ❤️
    </button>

    <button id="no">
      NO 😜
    </button>

    <!-- Message after YES -->
    <div id="message">

      मैं भी तुमसे बहुत प्यार करता हूँ,
      <br>

      <strong>बेइंतहा प्यार करता हूँ। ❤️</strong>

      <div class="shayari">

        तुम मेरी ज़िंदगी की वो खूबसूरत कहानी हो,
        <br>

        जिसे मैं हर जन्म में दोबारा लिखना चाहूँगा। ❤️

        <br><br>

        Happy Birthday, My Love! 🎂❤️

      </div>

    </div>

  </div>


  <script>

    const yesButton = document.getElementById("yes");
    const noButton = document.getElementById("no");
    const message = document.getElementById("message");


    // -----------------------------
    // NO BUTTON - RUNS AWAY
    // -----------------------------

    function moveNoButton() {

      const padding = 20;

      const maxX =
        window.innerWidth -
        noButton.offsetWidth -
        padding;

      const maxY =
        window.innerHeight -
        noButton.offsetHeight -
        padding;

      const randomX =
        Math.max(
          padding,
          Math.random() * maxX
        );

      const randomY =
        Math.max(
          padding,
          Math.random() * maxY
        );

      noButton.style.position = "fixed";

      noButton.style.left =
        randomX + "px";

      noButton.style.top =
        randomY + "px";
    }


    // Computer
    noButton.addEventListener(
      "mouseenter",
      moveNoButton
    );


    // Mobile
    noButton.addEventListener(
      "touchstart",
      function(event) {

        event.preventDefault();

        moveNoButton();

      }
    );


    // If somehow clicked
    noButton.addEventListener(
      "click",
      function(event) {

        event.preventDefault();

        moveNoButton();

      }
    );


    // -----------------------------
    // YES BUTTON
    // -----------------------------

    yesButton.addEventListener(
      "click",
      function() {

        // Show love message
        message.style.display = "block";

        // Hide buttons
        yesButton.style.display = "none";
        noButton.style.display = "none";


        // Start heart rain
        for (
          let i = 0;
          i < 120;
          i++
        ) {

          setTimeout(
            createHeart,
            i * 40
          );

        }

      }
    );


    // -----------------------------
    // CREATE HEART
    // -----------------------------

    function createHeart() {

      const heart =
        document.createElement("div");

      heart.className = "heart";

      const hearts = [
        "❤️",
        "💖",
        "💕",
        "💗",
        "💜",
        "💘",
        "💝"
      ];

      heart.textContent =
        hearts[
          Math.floor(
            Math.random() *
            hearts.length
          )
        ];


      // Random position
      heart.style.left =
        Math.random() * 100 + "vw";


      // Random size
      heart.style.fontSize =
        (18 + Math.random() * 28) + "px";


      // Random falling speed
      heart.style.animationDuration =
        (2.5 + Math.random() * 3) + "s";


      document.body.appendChild(
        heart
      );


      // Remove after animation
      setTimeout(
        function() {

          heart.remove();

        },
        6000
      );

    }

  </script>

</body>
</html>#
