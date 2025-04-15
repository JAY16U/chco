<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Scratch Coupon for Jay</title>
  <style>
    body {
      background: #f2f2f2;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .card-container {
      position: relative;
      width: 300px;
      height: 200px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
      overflow: hidden;
      text-align: center;
      padding: 20px;
    }

    .prize-text {
      font-size: 20px;
      font-weight: bold;
      color: #333;
      padding-top: 60px;
    }

    #scratchCanvas {
      position: absolute;
      top: 0;
      left: 0;
      width: 300px;
      height: 200px;
      cursor: crosshair;
    }

    .terms {
      font-size: 12px;
      margin-top: 10px;
      color: #666;
    }
  </style>
</head>
<body>

<div class="card-container">
  <div class="prize-text">
    🎉 You won an Amul Dark Chocolate! 🍫
  </div>
  <canvas id="scratchCanvas"></canvas>
  <div class="terms">
    <h1>This gift is only for Kunal sir Not transferable. 😄</h1>
  </div>
</div>

<script>
  const canvas = document.getElementById('scratchCanvas');
  const ctx = canvas.getContext('2d');
  let isDrawing = false;

  function resizeCanvas() {
    canvas.width = 300;
    canvas.height = 200;
    ctx.fillStyle = '#ccc';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
  }

  resizeCanvas();

  canvas.addEventListener('mousedown', function(e) {
    isDrawing = true;
    scratch(e);
  });

  canvas.addEventListener('mouseup', () => isDrawing = false);
  canvas.addEventListener('mouseleave', () => isDrawing = false);
  canvas.addEventListener('mousemove', scratch);

  function scratch(e) {
    if (!isDrawing) return;
    const rect = canvas.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    ctx.globalCompositeOperation = 'destination-out';
    ctx.beginPath();
    ctx.arc(x, y, 20, 0, Math.PI * 2, false);
    ctx.fill();
  }
</script>

</body>
</html>
