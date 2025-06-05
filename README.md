<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Mini Jogo de Apostas</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background: #121212;
      font-family: Arial, sans-serif;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background: #1e1e1e;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 0 15px rgba(0,0,0,0.5);
      text-align: center;
    }
    h1 { margin-bottom: 20px; }
    input, select {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: none;
      border-radius: 8px;
      font-size: 16px;
    }
    button {
      width: 100%;
      padding: 15px;
      background: #e50914;
      color: #fff;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background: #c40812;
    }
    .result {
      margin-top: 20px;
      font-size: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>

<div class="container">
  <h1>Jogo de Apostas</h1>
  <label>Valor da Aposta (R$):</label>
  <input type="number" id="betAmount" placeholder="Digite o valor" min="1">
  
  <label>Escolha:</label>
  <select id="betChoice">
    <option value="Par">Par</option>
    <option value="Ímpar">Ímpar</option>
  </select>
  
  <button id="placeBet">Apostar</button>
  
  <div class="result" id="result"></div>
</div>

<script>
  const placeBetBtn = document.getElementById('placeBet');
  const betAmount = document.getElementById('betAmount');
  const betChoice = document.getElementById('betChoice');
  const resultDiv = document.getElementById('result');

  placeBetBtn.addEventListener('click', () => {
    const amount = parseFloat(betAmount.value);
    const choice = betChoice.value;

    if (!amount || amount <= 0) {
      resultDiv.textContent = "Insira um valor válido!";
      resultDiv.style.color = "yellow";
      return;
    }

    // Simula número aleatório entre 1 e 10
    const number = Math.floor(Math.random() * 10) + 1;
    const resultType = number % 2 === 0 ? "Par" : "Ímpar";

    if (choice === resultType) {
      const winnings = amount * 1.9; // Exemplo: retorno de 1.9x
      resultDiv.textContent = `Você GANHOU R$${winnings.toFixed(2)}! Número sorteado: ${number}`;
      resultDiv.style.color = "lime";
    } else {
      resultDiv.textContent = `Você PERDEU R$${amount}. Número sorteado: ${number}`;
      resultDiv.style.color = "red";
    }
  });
</script>

</body>
</html>
