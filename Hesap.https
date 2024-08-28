<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hesap Makinesi</title>
    <style>
        body { font-family: Arial, sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; background-color: #f4f4f4; }
        .calculator { border-radius: 10px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); background: #fff; padding: 20px; width: 300px; }
        .display { background: #000; color: #fff; border: none; border-radius: 5px; padding: 10px; font-size: 1.5em; text-align: right; width: 100%; margin-bottom: 10px; }
        .button { font-size: 1.2em; width: 23%; padding: 15px; border: none; border-radius: 5px; margin: 5px; cursor: pointer; }
        .button.operator { background: #007bff; color: #fff; }
        .button.operator:hover { background: #0056b3; }
        .button.double { width: 48%; }
        .button.zero { width: 48%; }
        .footer { text-align: center; margin-top: 20px; font-size: 0.9em; color: #777; }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" class="display" id="display" readonly>
        <div>
            <button class="button" onclick="appendNumber('7')">7</button>
            <button class="button" onclick="appendNumber('8')">8</button>
            <button class="button" onclick="appendNumber('9')">9</button>
            <button class="button operator" onclick="setOperation('/')">/</button>
        </div>
        <div>
            <button class="button" onclick="appendNumber('4')">4</button>
            <button class="button" onclick="appendNumber('5')">5</button>
            <button class="button" onclick="appendNumber('6')">6</button>
            <button class="button operator" onclick="setOperation('*')">*</button>
        </div>
        <div>
            <button class="button" onclick="appendNumber('1')">1</button>
            <button class="button" onclick="appendNumber('2')">2</button>
            <button class="button" onclick="appendNumber('3')">3</button>
            <button class="button operator" onclick="setOperation('-')">-</button>
        </div>
        <div>
            <button class="button zero" onclick="appendNumber('0')">0</button>
            <button class="button" onclick="appendNumber('.')">.</button>
            <button class="button double operator" onclick="calculateResult()">=</button>
            <button class="button operator" onclick="setOperation('+')">+</button>
        </div>
        <div class="footer">Matematik bilmeyen betalar için yapılmıştır</div>
    </div>

    <script>
        let currentInput = '';
        let currentOperation = null;
        let operand1 = null;

        function appendNumber(number) {
            currentInput += number;
            document.getElementById('display').value = currentInput;
        }

        function setOperation(operation) {
            if (currentInput === '' && operation === '-') {
                currentInput = '-';
                document.getElementById('display').value = currentInput;
                return;
            }
            if (currentOperation !== null) {
                calculateResult();
            }
            operand1 = parseFloat(currentInput);
            currentOperation = operation;
            currentInput = '';
        }

        function calculateResult() {
            if (currentOperation === null || currentInput === '') return;
            let operand2 = parseFloat(currentInput);
            let result;
            switch (currentOperation) {
                case '+':
                    result = operand1 + operand2;
                    break;
                case '-':
                    result = operand1 - operand2;
                    break;
                case '*':
                    result = operand1 * operand2;
                    break;
                case '/':
                    result = operand1 / operand2;
                    break;
                default:
                    return;
            }
            currentInput = result.toString();
            currentOperation = null;
            operand1 = null;
            document.getElementById('display').value = currentInput;
        }
    </script>
</body>
</html>
