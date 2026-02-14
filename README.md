# 🚀 [Dentalmovilr4]

Con mi aplicación resolver lo problema que mi laboratorio me presenta en la hora de entrega un trabajo.

## 🛠️ Tecnologías utilizadas
* **Lenguaje:** Python / JavaScript / Java
* **Framework:** React / Django / Spring Boot
* **Base de Datos:** PostgreSQL / MongoDB
* **Otras:** Docker, AWS, Tailwind CSS

## ✨ Características principales
* ✅ Característica 1: Descripción rápida.
* ✅ Característica 2: Descripción rápida.
* ✅ Característica 3: Descripción rápida.

## 📸 Demo (Opcional)
![Texto alternativo de la imagen](enlace-a-tu-captura-de-pantalla.png)
> *Tip: Si no tienes una imagen, puedes poner un GIF del funcionamiento.*

## 🚀 Instalación y uso

1. **Clona el repositorio:**
   ```bash
   git clone [https://github.com/tu-usuario/nombre-del-repo.git](https://github.com/tu-usuario/nombre-del-repo.git)

# git init

git add .

git commit -m "Mi primer guardado de la app"


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pong Game</title>
    <style>
        body { 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            margin: 0; 
            background-color: black; 
        }
        canvas { 
            border: 1px solid white; 
        }
        #score { 
            color: white; 
            font-size: 24px; 
            position: absolute; 
            top: 20px; 
        }
    </style>
</head>
<body>
    <div id="score">0 : 0</div>
    <canvas id="pong" width="800" height="400"></canvas>

    <script>
        const canvas = document.getElementById("pong");
        const ctx = canvas.getContext("2d");
        const paddleWidth = 10, paddleHeight = 100;
        let playerPaddle = { x: 0, y: canvas.height / 2 - paddleHeight / 2, width: paddleWidth, height: paddleHeight };
        let computerPaddle = { x: canvas.width - paddleWidth, y: canvas.height / 2 - paddleHeight / 2, width: paddleWidth, height: paddleHeight };
        let ball = { x: canvas.width / 2, y: canvas.height / 2, radius: 10, speed: 5, velocityX: 5, velocityY: 5 };
        let playerScore = 0, computerScore = 0;

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";
            ctx.fillRect(playerPaddle.x, playerPaddle.y, playerPaddle.width, playerPaddle.height);
            ctx.fillRect(computerPaddle.x, computerPaddle.y, computerPaddle.width, computerPaddle.height);
            ctx.beginPath();
            ctx.arc(ball.x, ball.y, ball.radius, 0, Math.PI * 2, false);
            ctx.fill();
            ctx.fillText(playerScore + " : " + computerScore, canvas.width / 2 - 30, 30);
        }

        function update() {
            ball.x += ball.velocityX;
            ball.y += ball.velocityY;
            if (ball.y + ball.radius > canvas.height || ball.y - ball.radius < 0) ball.velocityY = -ball.velocityY;
            if (ball.x - ball.radius < 0) {
                computerScore++;
                resetBall();
            } else if (ball.x + ball.radius > canvas.width) {
                playerScore++;
                resetBall();
            }
            if (ball.x - ball.radius < playerPaddle.x + playerPaddle.width && ball.y > playerPaddle.y && ball.y < playerPaddle.y + playerPaddle.height) {
                ball.velocityX = -ball.velocityX;
            }
            if (ball.x + ball.radius > computerPaddle.x && ball.y > computerPaddle.y && ball.y < computerPaddle.y + computerPaddle.height) {
                ball.velocityX = -ball.velocityX;
            }
            computerPaddle.y += (ball.y - (computerPaddle.y + computerPaddle.height / 2)) * 0.09;
        }

        function resetBall() {
            ball.x = canvas.width / 2;
            ball.y = canvas.height / 2;
            ball.velocityX = -ball.velocityX;
        }

        function gameLoop() {
            draw();
            update();
            requestAnimationFrame(gameLoop);
        }

        window.addEventListener('mousemove', (event) => {
            let rect = canvas.getBoundingClientRect();
            playerPaddle.y = event.clientY - rect.top - playerPaddle.height / 2;
        });
        window.addEventListener('keydown', (event) => {
            if (event.key === "ArrowUp" && playerPaddle.y > 0) {
                playerPaddle.y -= 20;
            } else if (event.key === "ArrowDown" && playerPaddle.y < canvas.height - playerPaddle.height) {
                playerPaddle.y += 20;
            }
        });

        gameLoop();
    </script>
