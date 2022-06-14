# CalculadoraIMC
Código do projeto de Calculadora IMC em HTML/CSS e JS


<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="shortcut icon" href="Calcuico.ico" type="image/x-icon">
    <title>Calculadora IMC</title>
    <style>
        body{
            font-family: Trebuchet MS;
            background: linear-gradient(to right, #ABBD9B, #2B3D1B);
            text-align: center;
            color: #fff;
        }
        .conteiner{
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
            width: 50%;
            background-color: rgb(0, 0, 0, 0.5);
            padding: 1em;
            border-radius: 10px;   
        }
        button{
            background-color: #315e31;
            color: rgb(255, 255, 255);
            border: none;
            padding: 1em;
            border-radius: 10px;
            box-shadow: 1px 1px 6px rgb(0, 0, 0);
            cursor: pointer;
        }
        button:hover{
            background-color: #538a53;
        }
        .final-step,
        .second-step{
            display: none;
        }
        input{
            padding: 5px;
            border-radius: 5px;
            border: none;
            outline: none;
        }
        #resultado{
            font-size: 25px;
        }
    </style>
</head>
<body>
    <h1>HM Calculator</h1>
    <div class="conteiner">
        <div class="first-step">
            <p>Clique no botão para calcular seu IMC</p>
            <button onclick="go(1,2)">Iniciar</button>
        </div>
        <div class="second-step">
            <h3>Calculadora IMC</h3>
            <hr>
            <label for="peso">Digite seu peso:</label>
            <input type="number" placeholder="Seu peso" id="peso">
            <br><br>
            <label for="altura">Digite sua altura</label>
            <input type="number" placeholder="Sua altura" id="altura">
            <br><br>
            <button onclick="validate()">Calcular</button>
        </div>
        <div class="final-step">
            <h3>Resultado!</h3>
            <p></p>
            <p id="resultado"></p>
            <button onclick="go(3,2)">Calcular Novamente</button>
            <button onclick="go(3,1)">Finalizar</button>
        </div>
    </div>
</body>
<script>
    const firstDiv = document.querySelector('.first-step');
    const secondDiv = document.querySelector('.second-step');
    const finalDiv = document.querySelector('.final-step');


    function go(currentStep,nextStep)
    {
        let dNone, dBlock;
        if (currentStep == 1)
        {
            dNone = firstDiv;
        }
        else if (currentStep == 2)
        {
            dNone = secondDiv;
        }
        else
        {
            dNone = finalDiv;
        }
        
        dNone.style.display = 'none';
        
        if(nextStep == 1)
        {
            dBlock = firstDiv;
        }
        else if(nextStep == 2)
        {
            dBlock = secondDiv;
        }
        else
        {
            dBlock = finalDiv;
        }
        dBlock.style.display = 'block';
    }
    
    function validate()
    {
        const peso = document.getElementById('peso')
        const altura = document.getElementById('altura')
        peso.style.border = 'none';
        altura.style.border = 'none';
        if(!peso.value || !altura.value)
        {
            if(!peso.value && !altura.value)
            {
                peso.style.border = '1px solid red'
                altura.style.border = '1px solid red'
            }
            else if(!peso.value)
            {
                peso.style.border = '1px solid red'
            }
            else
            {
                altura.style.border = '1px solid red'
            }
        }
        else
        {
            let imc = peso.value / (altura.value * altura.value)
            const result = document.getElementById('resultado');
            const resultimc = document.getElementById('imc')
            if(imc < 18.5)
            {
                console.log('Magreza | Abaixo do peso');
                result.style.color = '#6f6f72'
                result.innerHTML = 'Magreza | Abaixo do peso'
            }
            else if (imc >= 18.55 && imc < 24.9)
            {
                console.log('Peso Ideal | Mantenha nessa peso');
                result.style.color = '#538a53'
                result.innerHTML = 'Peso Ideal | Mantenha-se nessa peso'
            }
            else if (imc >= 25 && imc <29.9)
            {
                console.log('Levemente acima do peso | Sobrepeso')
                result.style.color = '#c2a91a'
                result.innerHTML = 'Levemente acima do peso | Sobrepeso'
            }
            else if (imc >= 30 && imc < 34.9)
            {
                console.log('Obesidade | Grau I')
                result.style.color = '#c7760c'
                result.innerHTML = 'Obesidade | Grau I'
            }
            else if (imc >= 35 && imc < 39.9)
            {
                console.log('Obesidade Severa | Grau II')
                result.style.color = '#993c06'
                result.innerHTML = 'Obesidade Severa | Grau II'
            }
            else 
            {
                console.log('Obesidade mórbida | Grau III')
                result.style.color = '#c70c0c'
                result.innerHTML = 'Obesidade mórbida | Grau III'
            }
            go(2,3)
        }
    }
</script>
</html>
