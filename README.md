<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>爱心点击特效</title>
    <style>
        body {
            margin: 0;
            background-color: #ffe6e6;
            overflow: hidden;
            text-align: center;
            font-family: Arial, sans-serif;
        }
        .message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
            font-weight: bold;
            color: red;
            display: none;
        }
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            transform: rotate(-45deg);
            position: absolute;
            animation: fadeOut 1s ease-in-out forwards;
        }
        .heart::before, .heart::after {
            content: "";
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
            position: absolute;
        }
        .heart::before {
            top: -10px;
            left: 0;
        }
        .heart::after {
            left: 10px;
            top: 0;
        }
        @keyframes fadeOut {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-50px) scale(1.5); opacity: 0; }
        }
    </style>
</head>
<body onclick="showHeart(event)">

    <div class="message" id="message">我爱你 王淑萍宝宝 ❤️</div>

    <script>
        function showHeart(event) {
            const heart = document.createElement("div");
            heart.className = "heart";
            heart.style.left = event.clientX + "px";
            heart.style.top = event.clientY + "px";
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 1000);

            const message = document.getElementById("message");
            message.style.display = "block";

            setTimeout(() => {
                message.style.display = "none";
            }, 2000);
        }
    </script>

</body>
</html>
