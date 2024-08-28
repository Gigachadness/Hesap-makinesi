<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hesap Makinesi</title>
    <style>
        body { font-family: Arial, sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; background-color: #f4f4f4; }
        .calculator { border: 1px solid #ccc; border-radius: 10px; overflow: hidden; background-color: #fff; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
        .display { background-color: #222; color: #fff; padding: 20px; font-size: 2em; text-align: right; }
        .buttons { display: grid; grid-template-columns: repeat(4, 1fr); }
        .button { padding: 20px; font-size: 1.5em; border: 1px solid #ccc; cursor: pointer; text-align: center; background-color: #f9f9f9; }
        .button:hover { background-color: #f0f0f0; }
        .button.operator { background-color: #f4a460; color: white; }
        .button.operator:hover { background-color: #e59560; }
        .button.double { grid-column: span 2; }
        .footer { text-align: center; margin-top: 10px; font-size: 0.9em; color: #777; }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="button double" onclick="clearDisplay()">C</button>
            <button class="button operator" onclick="appendToDisplay('/')">/</button>
            <button class="button operator" onclick="appendToDisplay('*')">*</button>
            <button class="button operator" onclick="appendToDisplay('-')">-</button>
            <button class="button operator" onclick="appendToDisplay('+')">+</button>
            <button class="button double" onclick="calculateResult()">=</button>
            <button class="button" onclick="appendToDisplay('7')">7</button>
            <button class="button" onclick="appendToDisplay('8')">8</button>
            <button class="button" onclick="appendToDisplay('9')">9</button>
            <button class="button" onclick="appendToDisplay('4')">4</button>
            <button class="button" onclick="appendToDisplay('5')">5</button>
            <button class="button" onclick="appendToDisplay('6')">6</button>
            <button class="button" onclick="appendToDisplay('1')">1</button>
            <button class="button" onclick="appendToDisplay('2')">2</button>
            <button class="button" onclick="appendToDisplay('3')">3</button>
            <button class="button double" onclick="appendToDisplay('0')">0</button>
        </div>
    </div>
    <div class="footer">Matematik bilmeyen betalar için yapılmıştır</div>

    <script>
        function clearDisplay() {
            document.getElementById('display').textContent = '0';
        }

        function appendToDisplay(value) {
            const display = document.getElementById('display');
            if (display.textContent === '0') {
                display.textContent = value;
            } else {
                display.textContent += value;
            }
        }

        function calculateResult() {
            const display = document.getElementById('display');
            try {
                display.textContent = eval(display.textContent) || '0';
            } catch (e) {
                display.textContent = 'Error';
            }
        }
    </script>
</body>
</html>
