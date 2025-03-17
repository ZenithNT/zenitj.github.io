# zenitj.github.io  
<!DOCTYPE html>
<html lang="zh-TW">
<head>  
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>轉盤小遊戲</title>
    <style>  
        body {  
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f0f0f0;  
        }
        .wheel-container {  
            position: relative;
        }
        #wheel {  
            width: 400px;
            height: 400px;
            border-radius: 50%;
            border: 10px solid #333;
            position: relative;
            overflow: hidden;
            transition: transform 4s cubic-bezier(0.17, 0.67, 0.83, 0.67);
        }
        .slice {
            position: absolute;
            width: 50%;
            height: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #333;
            font-size: 18px;
            transform-origin: 100% 100%;
        }
        .slice:nth-child(1) { background-color: #FFC0CB; transform: rotate(0deg); }
        .slice:nth-child(2) { background-color: #ADD8E6; transform: rotate(45deg); }
        .slice:nth-child(3) { background-color: #90EE90; transform: rotate(90deg); }
        .slice:nth-child(4) { background-color: #FFD700; transform: rotate(135deg); }
        .slice:nth-child(5) { background-color: #FFA07A; transform: rotate(180deg); }
        .slice:nth-child(6) { background-color: #E6E6FA; transform: rotate(225deg); }
        .slice:nth-child(7) { background-color: #FFDAB9; transform: rotate(270deg); }
        .slice:nth-child(8) { background-color: #87CEEB; transform: rotate(315deg); }
        .pointer {
            position: absolute;
            top: -10px;
            left: 50%;
            width: 0;
            height: 0;
            border-left: 20px solid transparent;
            border-right: 20px solid transparent;
            border-bottom: 40px solid red;
            transform: translateX(-50%);
        }
        #spin {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
        #result {
            margin-top: 20px;
            font-size: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="wheel-container">
        <div class="pointer"></div>
        <div id="wheel">
            <div class="slice">NT1000</div>
            <div class="slice">NT1000</div>
            <div class="slice">NT1000</div>
            <div class="slice">NT1000</div>
            <div class="slice">NT2000</div>
            <div class="slice">NT2000</div>
            <div class="slice">NT2000</div>
            <div class="slice">NT5000</div>
            <div class="slice">NT10000</div>
            <div class="slice">謝謝惠顧</div>
        </div>  
    </div>  
    <button id="spin">旋轉轉盤</button>
    <div id="result"></div>

    <script>
        const wheel = document.getElementById('wheel');
        const spinButton = document.getElementById('spin');
        const resultDisplay = document.getElementById('result');
        const activities = ['NT1000', 'NT1000', 'NT1000', 'NT1000', 'NT2000', 'NT2000', 'NT2000', 'NT5000', 'NT10000', '謝謝惠顧'];
        let currentRotation = 0;

        spinButton.addEventListener('click', () => {
            const randomDegree = Math.floor(Math.random() * 360) + 720; // 確保至少旋轉兩圈
            currentRotation += randomDegree;
            wheel.style.transform = `rotate(${currentRotation}deg)`;
            
            setTimeout(() => {
                const finalDegree = currentRotation % 360;
                const index = Math.floor(((360 - finalDegree + 18) % 360) / 36);
                resultDisplay.textContent = `恭喜你獲得: ${activities[index]}`;
            }, 4000);
        });
    </script>
</body>  
</html>  

