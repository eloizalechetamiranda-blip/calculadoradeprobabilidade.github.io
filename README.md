<!DOCTYPE html>

<html lang="pt-BR"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Calculadora de Probabilidade</title>

<style> * { box-sizing: border-box; } body { margin: 0; min-height: 100vh; display: flex; justify-content: center; align-items: center; background: #172554; font-family: Arial, sans-serif; padding: 20px; } .container { background: white; width: 100%; max-width: 420px; padding: 30px; border-radius: 15px; text-align: center; box-shadow: 0 10px 30px rgba(0,0,0,0.3); } h1 { color: #172554; font-size: 25px; } .descricao { color: #555; margin-bottom: 25px; } label { display: block; text-align: left; margin-top: 15px; font-weight: bold; color: #333; } input { display: block; width: 100%; height: 48px; padding: 12px; margin-top: 7px; border: 2px solid #ddd; border-radius: 8px; font-size: 17px; background: white; color: #222; outline: none; } input:focus { border-color: #2563eb; } button { display: block; width: 100%; height: 50px; margin-top: 25px; background: #2563eb; color: white; border: none; border-radius: 8px; font-size: 17px; font-weight: bold; cursor: pointer; } button:hover { background: #1d4ed8; } #resultado { display: none; margin-top: 25px; padding: 20px; background: #dcfce7; border-radius: 10px; color: #166534; } #erro { color: #dc2626; margin-top: 15px; font-weight: bold; } .valor { font-size: 25px; font-weight: bold; margin-top: 10px; } .limpar { background: #64748b; margin-top: 10px; } </style>

</head>

<body>

<div class="container">

<h1>Calculadora de Probabilidade</h1>

<p class="descricao">
    Descubra a probabilidade de um acontecimento.
</p>

<label for="favoraveis">Casos favoráveis:</label>

<input
    type="number"
    id="favoraveis"
    placeholder="Exemplo: 5"
    min="0"
    step="1"
>

<label for="possiveis">Casos possíveis:</label>

<input
    type="number"
    id="possiveis"
    placeholder="Exemplo: 10"
    min="1"
    step="1"
>

<button type="button" id="calcular">
    CALCULAR PROBABILIDADE
</button>

<div id="erro" role="alert"></div>

<div id="resultado" aria-live="polite">
    <h3>Resultado do cálculo</h3>

    <p>Probabilidade:</p>
    <div class="valor" id="probabilidade"></div>

    <p>Porcentagem:</p>
    <div class="valor" id="porcentagem"></div>
</div>

<button type="button" class="limpar" id="limpar">
    LIMPAR CAMPOS
</button>


</div>

<script> document.addEventListener("DOMContentLoaded", function() { const campoFavoraveis = document.getElementById("favoraveis"); const campoPossiveis = document.getElementById("possiveis"); const botaoCalcular = document.getElementById("calcular"); const botaoLimpar = document.getElementById("limpar"); const resultado = document.getElementById("resultado"); const erro = document.getElementById("erro"); botaoCalcular.addEventListener("click", function() { erro.textContent = ""; resultado.style.display = "none"; const valorFavoraveis = campoFavoraveis.value.trim(); const valorPossiveis = campoPossiveis.value.trim(); if (valorFavoraveis === "" || valorPossiveis === "") { erro.textContent = "Preencha os dois campos!"; return; } const favoraveis = Number(valorFavoraveis); const possiveis = Number(valorPossiveis); if (!Number.isSafeInteger(favoraveis) || !Number.isSafeInteger(possiveis)) { erro.textContent = "Digite apenas números inteiros válidos!"; return; } if (possiveis <= 0) { erro.textContent = "Os casos possíveis devem ser maiores que zero!"; return; } if (favoraveis < 0 || favoraveis > possiveis) { erro.textContent = "Os casos favoráveis devem estar entre zero e o total de casos possíveis!"; return; } const prob = favoraveis / possiveis; const porcentagem = prob * 100; document.getElementById("probabilidade").textContent = prob.toFixed(4); document.getElementById("porcentagem").textContent = porcentagem.toFixed(2) + "%"; resultado.style.display = "block"; }); botaoLimpar.addEventListener("click", function() { campoFavoraveis.value = ""; campoPossiveis.value = ""; erro.textContent = ""; resultado.style.display = "none"; campoFavoraveis.focus(); }); }); </script>

</body> </html>
