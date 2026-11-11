<!DOCTYPE html>

<html lang="pt-BR"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Calculadora de Probabilidade</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #141e30, #243b55);
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        margin: 0;
    }

    .container {
        background: white;
        padding: 35px;
        border-radius: 15px;
        width: 90%;
        max-width: 400px;
        box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        text-align: center;
    }

    h1 {
        color: #243b55;
        font-size: 25px;
    }

    p {
        color: #555;
    }

    input {
        width: 100%;
        padding: 12px;
        margin: 10px 0;
        box-sizing: border-box;
        border: 1px solid #ccc;
        border-radius: 8px;
        font-size: 16px;
    }

    button {
        width: 100%;
        padding: 13px;
        background: #243b55;
        color: white;
        border: none;
        border-radius: 8px;
        font-size: 16px;
        cursor: pointer;
        margin-top: 10px;
    }

    button:hover {
        background: #141e30;
    }

    #resultado {
        margin-top: 20px;
        font-size: 18px;
        font-weight: bold;
        color: #243b55;
    }

    #erro {
        color: red;
        margin-top: 15px;
    }
</style>


</head>

<body>

<div class="container">

    <h1>Calculadora de Probabilidade</h1>

    <p>Digite os valores para calcular a probabilidade.</p>

    <input
        type="number"
        id="favoraveis"
        placeholder="Casos favoráveis"
        min="0"
        step="1"
    >

    <input
        type="number"
        id="possiveis"
        placeholder="Casos possíveis"
        min="1"
        step="1"
    >

    <button onclick="calcular()">Calcular Probabilidade</button>

    <div id="erro"></div>
    <div id="resultado"></div>

</div>

<script>
    function calcular() {

        const favoraveis = document.getElementById("favoraveis").value;
        const possiveis = document.getElementById("possiveis").value;

        const erro = document.getElementById("erro");
        const resultado = document.getElementById("resultado");

        erro.innerHTML = "";
        resultado.innerHTML = "";

        if (favoraveis === "" || possiveis === "") {
            erro.innerHTML = "Preencha todos os campos!";
            return;
        }

        const f = Number(favoraveis);
        const p = Number(possiveis);

        if (!Number.isSafeInteger(f) || !Number.isSafeInteger(p)) {
            erro.innerHTML = "Digite apenas números inteiros válidos.";
            return;
        }

        if (p <= 0) {
            erro.innerHTML = "Os casos possíveis devem ser maiores que zero.";
            return;
        }

        if (f < 0 || f > p) {
            erro.innerHTML = "Os casos favoráveis devem estar entre zero e o total de casos possíveis.";
            return;
        }

        const probabilidade = f / p;
        const porcentagem = probabilidade * 100;

        resultado.innerHTML =
            "Probabilidade: " + probabilidade.toFixed(4) +
            "<br><br>" +
            "Porcentagem: " + porcentagem.toFixed(2) + "%";
    }
</script>


</body> </html>
