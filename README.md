
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
    <title>Semangat belajar Nurhaida ! </title>
    <style>
      /* Reset and base */
      * {
        box-sizing: border-box;
      }
      body {
        margin: 0;
        padding: 0;
        background: linear-gradient(135deg, #667eea, #764ba2);
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        color: #f0f0f0;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        max-height: 600px;
        max-width: 350px;
        margin-left: auto;
        margin-right: auto;
        user-select: none;
      }
    
      h1 {
        font-size: 2rem;
        margin-bottom: 10px;
        letter-spacing: 0.05em;
      }
    
      #timer {
        font-size: 4rem;
        font-weight: 700;
        letter-spacing: 0.2em;
        padding: 20px 40px;
        background: rgba(255,255,255,0.1);
        border-radius: 15px;
        box-shadow: 0 8px 20px rgba(0,0,0,0.3);
        user-select: text;
        min-width: 280px;
        text-align: center;
      }
    
      #controls {
        margin-top: 25px;
        display: flex;
        gap: 20px;
      }
      button {
        background: #f0f0f0;
        color: #5a4a8f;
        font-weight: 600;
        border: none;
        border-radius: 10px;
        padding: 12px 24px;
        font-size: 1rem;
        cursor: pointer;
        box-shadow: 0 4px 8px rgba(0,0,0,0.15);
        transition: background-color 0.3s ease, color 0.3s ease;
        flex: 1;
        min-width: 100px;
      }
      button:hover {
        background: #5a4a8f;
        color: #f0f0f0;
      }
      button:active {
        transform: scale(0.95);
      }
    
      /* Mobile optimization */
      @media (max-width: 400px) {
        #timer {
          font-size: 3rem;
          padding: 15px 30px;
          min-width: 240px;
        }
        button {
          padding: 10px 16px;
          font-size: 0.9rem;
          min-width: 90px;
        }
        h1 {
          font-size: 1.5rem;
        }
      }
    </style>
    </head>
    <body>
      <h1>Practice makes perfect</h1>
      <div id="timer">00:00:00</div>
      <div id="controls">
        <button id="startBtn">Start</button>
        <button id="resetBtn" disabled>Reset</button>
        <button id="pauseBtn" disabled>Pause</button>
      </div>
    
    <script>
      let secondsElapsed = 0;
      let timerInterval = null;
    
      const timerDisplay = document.getElementById('timer');
      const startBtn = document.getElementById('startBtn');
      const resetBtn = document.getElementById('resetBtn');
    
      function formatTime(sec) {
        const hrs = Math.floor(sec / 3600);
        const mins = Math.floor((sec % 3600) / 60);
        const seconds = sec % 60;
        return [hrs, mins, seconds]
          .map(v => v.toString().padStart(2, '0'))
          .join(':');
      }
    
      function updateTimer() {
        secondsElapsed++;
        timerDisplay.textContent = formatTime(secondsElapsed);
      }
    
      startBtn.addEventListener('click', () => {
        if (timerInterval) {
          // Already running
          return;
        }
        timerInterval = setInterval(updateTimer, 1000);
        startBtn.disabled = true;
        resetBtn.disabled = false;
        pauseBtn.disabled = false;
      });

      pauseBtn.addEventListener  ('click', () => {
          if (timerInterval) {
            clearInterval(timerInterval);
            timerInterval = null;
            pauseBtn.textContent = 'Resume';
          } else {
            timerInterval = setInterval(updateTimer, 1000);
            pauseBtn.textContent = 'Pause';
          }
        });

      resetBtn.addEventListener('click', () => {
        clearInterval(timerInterval);
        timerInterval = null;
        secondsElapsed = 0;
        timerDisplay.textContent = '00:00:00';
        startBtn.disabled = false;
        resetBtn.disabled = true;

       
      });
    </script>
    </body>
    </html>
    
