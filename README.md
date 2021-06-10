

# Advinha-um-numero


1 modelo da  página 

![image](https://user-images.githubusercontent.com/72118415/121478634-9e6f2800-c99f-11eb-99a5-6b8a04d8c57e.png)


2- modelo melhorado 

![image](https://user-images.githubusercontent.com/72118415/121478831-ce1e3000-c99f-11eb-8b1d-111de18e59a4.png)


3- modelo final

![image](https://user-images.githubusercontent.com/72118415/121478918-e4c48700-c99f-11eb-9c64-545dfa776a63.png)




html

<html>

<head>
    <title>
        Jogo adivinhe o número
    </title>
  
    
  <h1>Jogo adivinhe o número </h1>
  </head>
  <body>
    
   <p>Nós selecionamos um número aleatório entre 1 e 100. Veja se consegue adivinhar em 10 chances ou menos. Nós lhe diremos se seu palpite foi muito alto ou muito baixo. </p> 
    
    <div class="form">
      <label for="campoPalpite">Digite seu palpite: </label> <input type="text" id="campoPalpite" class="campoPalpite">
      <input type="submit" value="Enviar palpite" class="envioPalpite">
      </div>
    
      <div class="resultadoParas">
        <p class="palpites"></p>
        <p class="ultimoResultado"></p>
        <p class="baixoOuAlto"></p>
        </div>
    



    
       
   
</body>    
    
  
   </html>
   
   
   
   
   
   
   
   
   css
   
   
   html{
  font-family: sans-serif;
}


body{
  background-color: #800080;
  color: whitesmoke;
  text-shadow: black 0.1em 0.1em 0.2em;
  font-size: 20px;
  font-weight: bold;
  font-weight: 700;
  align-items: center;
  width: 50%;
  max-width: 600px;
  min-width: 480px;
  margin: 0 auto;
  background-image: url('https://vocesabia.com/wp-content/uploads/2020/02/digits-4014181_640.jpg');
  
  

.lastResult {
  color: White;
  padding: 3px;
}
  
  
  .form{
    color: white;
  align-items: center;
  width: 50%;
  max-width: 600px;
  min-width: 480px;
  margin: 0 auto;
  }
  
  @media (max-height: 500px) {
    body {
      min-height:800px;
    }
    
    
    
    
    j   s



var numeroAleatorio= Math.floor(Math.random() * 100) + 1;

var palpites = document.querySelector('.palpites');
var ultimoResultado = document.querySelector('.ultimoResultado');
var baixoOuAlto = document.querySelector('.baixoOuAlto');

var envioPalpite = document.querySelector('.envioPalpite');
var campoPalpite = document.querySelector('.campoPalpite');

var contagemPalpites = 1;
var botaoReinicio;
campoPalpite.focus();
function conferirPalpite() {
  var palpiteUsuario = Number(campoPalpite.value);
  if (contagemPalpites === 1) {
    palpites.textContent = 'Palpites anteriores: ';
  }
  palpites.textContent += palpiteUsuario + ' ';

  if (palpiteUsuario === numeroAleatorio) {
    ultimoResultado.textContent = 'Parabéns! Você acertou!';
    ultimoResultado.style.backgroundColor = 'green';
    baixoOuAlto.textContent = '';
    configFimDeJogo();
  } else if (contagemPalpites === 10) {
    ultimoResultado.textContent = '!!!FIM DE JOGO!!!';
    baixoOuAlto.textContent = '';
    configFimDeJogo();
  } else {
    ultimoResultado.textContent = 'Errado!';
    ultimoResultado.style.backgroundColor = 'red';
    if(palpiteUsuario < numeroAleatorio) {
      baixoOuAlto.textContent = 'Seu palpite está muito baixo!';
    } else if(palpiteUsuario > numeroAleatorio) {
      baixoOuAlto.textContent = 'Seu palpite está muito alto!';
    }
  }

  contagemPalpites++;
  campoPalpite.value = '';
  campoPalpite.focus();
}

envioPalpite.addEventListener('click', conferirPalpite);
function configFimDeJogo() {
  campoPalpite.disabled = true;
  envioPalpite.disabled = true;
  botaoReinicio = document.createElement('button');
  botaoReinicio.textContent = 'Iniciar novo jogo';
  document.body.appendChild(botaoReinicio);
  botaoReinicio.addEventListener('click', reiniciarJogo);
}

function reiniciarJogo() {
  contagemPalpites = 1;

  var reiniciarParas = document.querySelectorAll('.resultadoParas p');
  for (var i = 0 ; i < reiniciarParas.length ; i++) {
    reiniciarParas[i].textContent = '';
  }

  botaoReinicio.parentNode.removeChild(botaoReinicio);

  campoPalpite.disabled = false;
  envioPalpite.disabled = false;
  campoPalpite.value = '';
  campoPalpite.focus();

  ultimoResultado.style.backgroundColor = 'white';

  numeroAleatorio = Math.floor(Math.random() * 100) + 1;
}
