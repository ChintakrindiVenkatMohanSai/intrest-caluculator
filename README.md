<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Interest Calculator</title>
<style>
  :root {
    --bg: linear-gradient(135deg, #1e3c72, #2a5298);
    --calc-bg: #ffffff10;
    --btn-bg: #0d1b2a;
    --btn-hover: #00ffcc;
    --text-color: #00ffcc;
    --input-bg: #000;
  }
  body.dark {
    --bg: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
    --calc-bg: #00000050;
    --btn-bg: #1b263b;
    --btn-hover: #00ffcc;
    --text-color: #00ffcc;
    --input-bg: #111;
  }
  body {
    margin:0;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
    background: var(--bg);
    font-family: 'Poppins', sans-serif;
    transition: background 0.5s;
  }
  .calculator {
    background: var(--calc-bg);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 25px;
    width: 350px;
    box-shadow: 0 8px 25px rgba(0,0,0,0.3);
  }
  h2 {
    text-align:center;
    color: var(--text-color);
    margin-bottom: 20px;
  }
  input {
    width: 100%;
    padding: 12px;
    margin-bottom: 12px;
    border-radius: 10px;
    border: none;
    background: var(--input-bg);
    color: var(--text-color);
    font-size: 1rem;
    outline: none;
  }
  .buttons {
    display:flex;
    justify-content:space-between;
    margin-bottom: 12px;
  }
  button {
    padding: 12px 18px;
    border-radius: 10px;
    border: none;
    background: var(--btn-bg);
    color: #fff;
    cursor: pointer;
    transition: transform 0.1s, background 0.3s;
    flex:1;
    margin: 0 4px;
  }
  button:hover {
    background: var(--btn-hover);
    color: #000;
    transform: scale(1.05);
  }
  .result {
    text-align:center;
    color: var(--text-color);
    font-weight:700;
    margin-top: 12px;
  }
  .theme-toggle {
    display:flex;
    justify-content:center;
    margin-bottom: 12px;
  }
  .theme-toggle button {
    padding: 8px 16px;
    border-radius:50px;
    border:none;
    background: var(--btn-bg);
    color:#fff;
    cursor:pointer;
  }
  .theme-toggle button:hover { background: var(--btn-hover); color:#000; }
</style>
</head>
<body>
  <div class="calculator">
    <div class="theme-toggle">
      <button onclick="toggleTheme()">🌙 Dark / ☀️ Light</button>
    </div>
    <h2>Interest Calculator</h2>
    <input type="number" id="principal" placeholder="Principal (₹)">
    <input type="number" id="rate" placeholder="Rate (%)">
    <input type="number" id="time" placeholder="Time (years)">
    <div class="buttons">
      <button onclick="calculateSI()">Simple Interest</button>
      <button onclick="calculateCI()">Compound Interest</button>
    </div>
    <div class="result" id="result">Result: ₹0</div>
  </div>
<script>
const resultEl = document.getElementById('result');
function calculateSI(){
  const P = parseFloat(document.getElementById('principal').value);
  const R = parseFloat(document.getElementById('rate').value);
  const T = parseFloat(document.getElementById('time').value);
  if(isNaN(P)||isNaN(R)||isNaN(T)){ resultEl.textContent = 'Please enter valid values'; return; }
  const SI = (P*R*T)/100;
  resultEl.textContent = `Simple Interest: ₹${SI.toFixed(2)}`;
}
function calculateCI(){
  const P = parseFloat(document.getElementById('principal').value);
  const R = parseFloat(document.getElementById('rate').value)/100;
  const T = parseFloat(document.getElementById('time').value);
  if(isNaN(P)||isNaN(R)||isNaN(T)){ resultEl.textContent = 'Please enter valid values'; return; }
  const CI = P * (Math.pow(1+R,T)) - P;
  resultEl.textContent = `Compound Interest: ₹${CI.toFixed(2)}`;
}
function toggleTheme(){
  document.body.classList.toggle('dark');
}
</script>
</body>
</html>
