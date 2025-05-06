<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
<title>Smart Laser System Demo</title>
<style>
  /* Reset & basics */
  * {
    box-sizing: border-box;
    touch-action: manipulation;
  }
  body, html {
    margin: 0; padding: 0; height: 100%;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
    color: #e0e0e0;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  #app {
    position: relative;
    background: #121b25;
    width: 350px;
    height: 600px;
    border-radius: 15px;
    box-shadow: 0 0 20px 5px rgba(255, 0, 0, 0.6);
    user-select: none;
  }
  /* Laser emitter */
  #laser-emitter {
    position: absolute;
    width: 50px;
    height: 50px;
    background: radial-gradient(circle at center, #ff0000, #660000);
    border-radius: 50%;
    bottom: 40px;
    left: 50%;
    transform: translateX(-50%);
    box-shadow:
      0 0 10px 5px #ff0000,
      inset 0 0 15px 3px #ff5555;
    cursor: grab;
    touch-action: none;
  }
  #laser-emitter:active {
    cursor: grabbing;
  }
  /* Laser beam */
  #laser-beam {
    position: absolute;
    width: 4px;
    background: linear-gradient(180deg, #ff0000, #ff5050 80%, transparent);
    transform-origin: top center;
    bottom: 65px; /* slightly above emitter center */
    left: 50%;
    transform: translateX(-50%) rotate(0deg);
    pointer-events: none;
    box-shadow:
      0 0 20px 2px #ff4444,
      0 0 40px 8px #ff0000;
  }
  /* Target */
  #target {
    position: absolute;
    width: 70px;
    height: 70px;
    border-radius: 50%;
    background: radial-gradient(circle at center, #004400, #003300);
    border: 3px solid #007700;
    box-shadow:
      0 0 8px 3px #00cc00;
    top: 80px;
    left: calc(50% + 60px);
    transition: background 0.3s, box-shadow 0.3s, border-color 0.3s;
  }
  #target.locked {
    background: radial-gradient(circle at center, #00ff0077, #00aa0044);
    border-color: #00ff00;
    box-shadow:
      0 0 15px 6px #33ff33;
  }
  /* Info Text */
  #info {
    position: absolute;
    width: 100%;
    text-align: center;
    bottom: 10px;
    font-weight: 600;
    font-size: 1.2rem;
  }
  /* Control buttons for mobile */
  #controls {
    position: absolute;
    bottom: 110px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 15px;
  }
  .btn {
    background: #222;
    border: none;
    color: #ff4444;
    font-size: 1.5rem;
    border-radius: 6px;
    padding: 10px 14px;
    user-select: none;
    box-shadow: 0 0 8px #ff5555;
    transition: background 0.2s, color 0.2s;
    cursor: pointer;
    min-width: 44px;
    min-height: 44px;
  }
  .btn:hover, .btn:focus {
    background: #ff4444;
    color: #222;
    outline: none;
  }
  /* Responsive tweaks */
  @media (max-width: 400px) {
    #app {
      width: 90vw;
      height: 600px;
    }
    #target {
      width: 60px;
      height: 60px;
      left: calc(50% + 50px);
      top: 80px;
    }
    #laser-emitter {
      width: 45px;
      height: 45px;
      bottom: 40px;
    }
  }
</style>
</head>
<body>
  <div id="app" role="main" aria-label="Smart Laser System Simulator">
    <div id="laser-emitter" tabindex="0" aria-label="Laser emitter" role="slider" aria-valuemin="0" aria-valuemax="350" aria-valuenow="175"></div>
    <div id="laser-beam"></div>
    <div id="target" aria-label="Target"></div>
    <div id="controls" aria-label="Laser emitter movement controls">
      <button id="left-btn" class="btn" aria-label="Move laser emitter left">&larr;</button>
      <button id="right-btn" class="btn" aria-label="Move laser emitter right">&rarr;</button>
    </div>
    <div id="info" aria-live="polite" aria-atomic="true">Align the laser emitter to hit the target</div>
  </div>
<script>
  (function(){
    const app = document.getElementById('app');
    const emitter = document.getElementById('laser-emitter');
    const beam = document.getElementById('laser-beam');
    const target = document.getElementById('target');
    const info = document.getElementById('info');
    const leftBtn = document.getElementById('left-btn');
    const rightBtn = document.getElementById('right-btn');

  })();
</script>
</body>
</html>
</content>
</create_file>

