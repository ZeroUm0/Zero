# Zero
Teste de codigos
Gerador de senhas 

Html Code:
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Gerador de senha</title>

    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <main class="container-input">
        <span>Tamanho <span id="valor"> caracteres</span>
        <input id="slider" class="slider" type="range" min="5" max="25" value="15"/>

        <button id="button" class="button-cta" onclick="generatePassword()">Gerar senha</button>
    </main>

    <div id="container-password" class="container-password hide">
        <span class="title"> Sua senha foi gerada:</span>
        <span id="password" class="password"></span>
        <span class="tooltip">Clique na senha para copiar. 👆</span>
    </div>
    <script src="script.js"></script>
  </body>
</html>

Css Code:
* {
  font-family: sans-serif;
  width: 100%;
  margin: 0 auto;
  box-sizing: border-box;
}

body {
  background-color: #18181b;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.container-input {
  max-width: 480px;
  margin: 14px 0;
}
.container-input span {
  color: white;
  font-size: 22px;
}
.slider {
  -webkit-appearance: none;
  width: 100%;
  border-radius: 5px;
  background-color: #dfdfdf;
  height: 18px;
  outline: none;
  margin-top: 8px;
}
.button-cta {
  height: 40px;
  background-color: #3eb72b;
  border: 0;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 40px;
  color: white;
  font-weight: bold;
  font-size: 20px;
}
.container-password {
  max-width: 480px;
  margin: 14px 0;
  display: flex;
  align-items: center;
  flex-direction: column;
  cursor: pointer;
}
.title {
  text-align: center;
  color: white;
  font-size: 28px;
  margin-top: 24px;
  margin-bottom: 8px;
}

.password {
  height: 60px;
  background-color: rgba(0, 0, 0, 0.4);
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  border: 1px solid #313131;
  transition: transform 0.5s;
}

.password:hover {
  transform: scale(1.05);
}

.tooltip {
  color: white;
  position: relative;
  top: 20px;
  padding: 6px 8px;
  background: rgb(15, 15, 15);
  text-align: center;
  font-size: 16px;
  border-radius: 6px;
  visibility: hidden;
  opacity: 0;
  transition: all 0.5s ease-in-out;
}

.hide {
  display: none;
}

.container-password:hover .tooltip {
  visibility: visible;
  bottom: 50px;
  opacity: 1;
}

JavaScript Code:
let sliderElement = document.querySelector("#slider");
let buttonElement = document.querySelector("#button");

let sizePassword = document.querySelector("#valor");
let password = document.querySelector("#password");

let containerPassword = document.querySelector("#container-password");

let charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!";
let novaSenha = "";

sizePassword.innerHTML = sliderElement.value;

slider.oninput = function () {
  sizePassword.innerHTML = this.value;
};

function generatePassword() {
  let pass = "";
  for (let i = 0, n = charset.length; i < sliderElement.value; ++i) {
    pass += charset.charAt(Math.floor(Math.random() * n));
  }

  console.log(pass);
  containerPassword.classList.remove("hide");
  password.innerHTML = pass;
  novaSenha = pass;
}

function copyPassword() {
  alert("Senha copiada com sucesso!");
  navigator.clipboard.writeText(novaSenha);
}
