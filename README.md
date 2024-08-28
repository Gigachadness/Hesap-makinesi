<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hedefe Ulaş</title>
    <style>
        body { display: flex; justify-content: center; align-items: center; height: 100vh; background: #000; margin: 0; }
        canvas { background: #000; border: 1px solid #fff; }
    </style>
</head>
<body>
    <canvas id="game" width="600" height="400"></canvas>
    <script>
        const canvas = document.getElementById('game');
        const ctx = canvas.getContext('2d');

        const player = { x: 50, y: 50, size: 20 };
        const target = { x: Math.random() * canvas.width, y: Math.random() * canvas.height, size: 20 };

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#00f';
            ctx.beginPath();
            ctx.arc(player.x, player.y, player.size, 0, Math.PI * 2);
            ctx.fill();

            ctx.fillStyle = '#f00';
            ctx.beginPath();
            ctx.arc(target.x, target.y, target.size, 0, Math.PI * 2);
            ctx.fill();
        }

        function update() {
            if (Math.abs(player.x - target.x) < player.size + target.size &&
                Math.abs(player.y - target.y) < player.size + target.size) {
                target.x = Math.random() * canvas.width;
                target.y = Math.random() * canvas.height;
            }
        }

        function gameLoop() {
            draw();
            update();
            requestAnimationFrame(gameLoop);
        }

        document.addEventListener('mousemove', e => {
            const rect = canvas.getBoundingClientRect();
            player.x = e.clientX - rect.left;
            player.y = e.clientY - rect.top;
        });

        gameLoop();
    </script>
</body>
</html>
