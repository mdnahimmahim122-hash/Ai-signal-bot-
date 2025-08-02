<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI Signal Bot</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #0f0f0f;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background: #1c1c1c;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0, 255, 180, 0.4);
      text-align: center;
      width: 90%;
      max-width: 400px;
    }
    h1 {
      color: #00ffcc;
      margin-bottom: 20px;
    }
    .signal {
      font-size: 48px;
      margin: 20px 0;
      font-weight: bold;
    }
    .timer {
      font-size: 24px;
      color: #ffd700;
      margin-top: 10px;
    }
    button {
      padding: 12px 25px;
      background-color: #00cc66;
      border: none;
      border-radius: 10px;
      color: white;
      font-size: 18px;
      margin-top: 25px;
      cursor: pointer;
    }
    button:hover {
      background-color: #00aa55;
    }
    footer {
      margin-top: 30px;
      font-size: 12px;
      color: #777;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>🔥 AI Signal Bot 🔥</h1>
    <div class="signal" id="signal">--</div>
    <div class="timer" id="timer">Press Start</div>
    <button onclick="startSignal()">Start Signal</button>
    <footer>Signal updates every 60 seconds</footer>
  </div>

  <script>
    let timeLeft = 60;
    let timerInterval;

    function getRandomSignal() {
      return Math.random() > 0.5 ? "📈 UP" : "📉 DOWN";
    }

    function startSignal() {
      const signalEl = document.getElementById('signal');
      const timerEl = document.getElementById('timer');

      signalEl.innerText = getRandomSignal();
      timeLeft = 60;
      timerEl.innerText = `${timeLeft}s`;

      clearInterval(timerInterval);
      timerInterval = setInterval(() => {
        timeLeft--;
        timerEl.innerText = `${timeLeft}s`;

        if (timeLeft <= 0) {
          signalEl.innerText = getRandomSignal();
          timeLeft = 60;
        }
      }, 1000);
    }
  </script>
</body>
</html>
