<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>小猫表白</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f8ff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            flex-direction: column;
        }
        .btn {
            background-color: #ff69b4;
            color: white;
            border: none;
            padding: 15px 30px;
            margin: 10px;
            font-size: 20px;
            cursor: pointer;
            border-radius: 10px;
            transition: transform 0.2s;
        }
        .btn:hover {
            background-color: #ff1493;
        }
        .btn:active {
            transform: scale(0.95);
        }
        .message {
            font-size: 24px;
            margin-top: 20px;
            text-align: center;
        }
        .message p {
            margin: 10px;
        }
    </style>
</head>
<body>
    <div class="message">
        <p>你想成为我的恋人吗？</p>
    </div>
    <button class="btn" id="yesBtn">可以</button>
    <button class="btn" id="noBtn">不可以</button>

    <script>
        let noBtnClicked = 0;
        let intervalId;

        // 处理点击"可以"按钮的逻辑
        document.getElementById('yesBtn').addEventListener('click', function() {
            clearInterval(intervalId); // 停止放大
            document.querySelector('.message').innerHTML = '<p>我们是恋人啦！</p>';
            document.getElementById('yesBtn').style.display = 'none';
            document.getElementById('noBtn').style.display = 'none';
        });

        // 处理点击"不可以"按钮的逻辑
        document.getElementById('noBtn').addEventListener('click', function() {
            noBtnClicked++;
            // 开启不断放大的效果
            if (!intervalId) {
                intervalId = setInterval(function() {
                    const currentScale = 1 + noBtnClicked * 0.1;
                    document.getElementById('yesBtn').style.transform = `scale(${currentScale})`;
                    noBtnClicked++;
                }, 300); // 每300ms放大一次
            }
            document.querySelector('.message').innerHTML = '<p>你在考虑一下...</p>';
        });
    </script>
</body>
</html>
