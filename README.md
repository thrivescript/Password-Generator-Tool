# Password-Generator-Tool

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Password Generator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
      background: #f4f4f4;
      color: #333;
    }
    .container {
      max-width: 400px;
      margin: auto;
      padding: 20px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    input[type="number"] {
      width: 60px;
      padding: 5px;
      margin-left: 5px;
    }
    label {
      display: block;
      margin: 8px 0;
    }
    button {
      margin-top: 15px;
      padding: 10px 16px;
      font-size: 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background-color: #007bff;
      color: white;
      transition: 0.3s;
    }
    button:hover {
      background-color: #0056b3;
    }
    #result {
      margin-top: 15px;
      padding: 10px;
      background: #eee;
      font-size: 18px;
      border-radius: 5px;
      word-break: break-all;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Password Generator</h2>
    <label>
      Length: 
      <input type="number" id="length" value="12" min="4" max="50">
    </label>
    <label><input type="checkbox" id="uppercase" checked> Include Uppercase</label>
    <label><input type="checkbox" id="lowercase" checked> Include Lowercase</label>
    <label><input type="checkbox" id="numbers" checked> Include Numbers</label>
    <label><input type="checkbox" id="symbols"> Include Symbols</label>
    <button onclick="generatePassword()">Generate Password</button>
    <div id="result">Your password will appear here</div>
  </div>

  <script>
    function generatePassword() {
      const length = document.getElementById('length').value;
      const includeUppercase = document.getElementById('uppercase').checked;
      const includeLowercase = document.getElementById('lowercase').checked;
      const includeNumbers = document.getElementById('numbers').checked;
      const includeSymbols = document.getElementById('symbols').checked;

      const upper = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
      const lower = 'abcdefghijklmnopqrstuvwxyz';
      const numbers = '0123456789';
      const symbols = '!@#$%^&*()_+~`|}{[]\\:;?><,./-=';
      
      let allChars = '';
      if (includeUppercase) allChars += upper;
      if (includeLowercase) allChars += lower;
      if (includeNumbers) allChars += numbers;
      if (includeSymbols) allChars += symbols;

      if (allChars === '') {
        document.getElementById('result').textContent = 'Please select at least one option.';
        return;
      }

      let password = '';
      for (let i = 0; i < length; i++) {
        const randomIndex = Math.floor(Math.random() * allChars.length);
        password += allChars[randomIndex];
      }

      document.getElementById('result').textContent = password;
    }
  </script>
</body>
</html>
