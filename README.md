<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Engineering Unit Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f4f4f9;
        }
        h1 {
            color: #333;
        }
        .converter {
            margin: 20px 0;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input, select, button {
            margin-bottom: 10px;
            padding: 8px;
            font-size: 1rem;
            width: 100%;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
  

    <div class="converter">
        <label for="value">Enter value:</label>
        <input type="number" id="value" placeholder="Enter value">

        <label for="from-unit">Convert from:</label>
        <select id="from-unit">
            <optgroup label="Length">
                <option value="m">Meters (m)</option>
                <option value="ft">Feet (ft)</option>
                <option value="cm">Centimeters (cm)</option>
                <option value="mm">Millimeters (mm)</option>
            </optgroup>
            <optgroup label="Mass">
                <option value="kg">Kilograms (kg)</option>
                <option value="lb">Pounds (lb)</option>
                <option value="g">Grams (g)</option>
                <option value="mg">Milligrams (mg)</option>
            </optgroup>
            <optgroup label="Temperature">
                <option value="C">Celsius (C)</option>
                <option value="F">Fahrenheit (F)</option>
                <option value="K">Kelvin (K)</option>
            </optgroup>
        </select>

        <label for="to-unit">Convert to:</label>
        <select id="to-unit">
            <optgroup label="Length">
                <option value="m">Meters (m)</option>
                <option value="ft">Feet (ft)</option>
                <option value="cm">Centimeters (cm)</option>
                <option value="mm">Millimeters (mm)</option>
            </optgroup>
            <optgroup label="Mass">
                <option value="kg">Kilograms (kg)</option>
                <option value="lb">Pounds (lb)</option>
                <option value="g">Grams (g)</option>
                <option value="mg">Milligrams (mg)</option>
            </optgroup>
            <optgroup label="Temperature">
                <option value="C">Celsius (C)</option>
                <option value="F">Fahrenheit (F)</option>
                <option value="K">Kelvin (K)</option>
            </optgroup>
        </select>

        <button onclick="convertUnit()">Convert</button>
        <div id="result" class="result"></div>
    </div>

    <script>
        function convertUnit() {
            const value = parseFloat(document.getElementById('value').value);
            const fromUnit = document.getElementById('from-unit').value;
            const toUnit = document.getElementById('to-unit').value;

            if (isNaN(value)) {
                document.getElementById('result').textContent = "Please enter a valid number.";
                return;
            }

            let result;

            // Length conversions
            if (fromUnit === 'm' && toUnit === 'ft') result = value * 3.28084;
            else if (fromUnit === 'ft' && toUnit === 'm') result = value / 3.28084;
            else if (fromUnit === 'm' && toUnit === 'cm') result = value * 100;
            else if (fromUnit === 'cm' && toUnit === 'm') result = value / 100;
            else if (fromUnit === 'm' && toUnit === 'mm') result = value * 1000;
            else if (fromUnit === 'mm' && toUnit === 'm') result = value / 1000;
            else if (fromUnit === 'cm' && toUnit === 'mm') result = value * 10;
            else if (fromUnit === 'mm' && toUnit === 'cm') result = value / 10;
            else if (fromUnit === 'ft' && toUnit === 'cm') result = value * 30.48;
            else if (fromUnit === 'cm' && toUnit === 'ft') result = value / 30.48;

            // Mass conversions
            else if (fromUnit === 'kg' && toUnit === 'lb') result = value * 2.20462;
            else if (fromUnit === 'lb' && toUnit === 'kg') result = value / 2.20462;
            else if (fromUnit === 'kg' && toUnit === 'g') result = value * 1000;
            else if (fromUnit === 'g' && toUnit === 'kg') result = value / 1000;
            else if (fromUnit === 'g' && toUnit === 'mg') result = value * 1000;
            else if (fromUnit === 'mg' && toUnit === 'g') result = value / 1000;

            // Temperature conversions
            else if (fromUnit === 'C' && toUnit === 'F') result = (value * 9 / 5) + 32;
            else if (fromUnit === 'F' && toUnit === 'C') result = (value - 32) * 5 / 9;
            else if (fromUnit === 'C' && toUnit === 'K') result = value + 273.15;
            else if (fromUnit === 'K' && toUnit === 'C') result = value - 273.15;
            else if (fromUnit === 'F' && toUnit === 'K') result = ((value - 32) * 5 / 9) + 273.15;
            else if (fromUnit === 'K' && toUnit === 'F') result = ((value - 273.15) * 9 / 5) + 32;

            // Unsupported conversion
            else result = 'Conversion not supported.';

            document.getElementById('result').textContent = `Converted Value: ${result}`;
        }
    </script>
</body>
</html>
