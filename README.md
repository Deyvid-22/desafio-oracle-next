## Link do projeto https://deyvid-22.github.io/oracle-challenge-decoder/

<div align="center">
  
  ![image](https://github.com/Deyvid-22/oracle-challenge-decoder/assets/140274792/efab8ac8-5384-48dd-a840-94b54b243b63)
  ![image](https://github.com/Deyvid-22/oracle-challenge-decoder/assets/140274792/625ed42b-1f65-4c7d-8171-17c4bbc87ee8)
  ![image](https://github.com/Deyvid-22/oracle-challenge-decoder/assets/140274792/e70676c5-9299-4711-ad8e-1565619b2322)
  
</div>

# Criptografia e Descriptografia de Texto

Este é um projeto simples em JavaScript para criptografar e descriptografar texto substituindo vogais por palavras específicas e vice-versa. O projeto foi desenvolvido como parte de um desafio e inclui funcionalidades básicas como interação com o DOM e cópia do resultado para a área de transferência.

## Funcionalidades

- **Criptografar:** Substitui vogais por palavras específicas definidas em um objeto.
- **Descriptografar:** Reverte a operação de criptografia.
- **Cópia para Área de Transferência:** Permite copiar o resultado final para a área de transferência.

## Estrutura do Projeto

O projeto é estruturado nos seguintes arquivos principais:

- **index.html:** Arquivo HTML que contém a estrutura básica da página web, incluindo os elementos de entrada de texto e botões para interação.
- **script.js:** Arquivo JavaScript responsável por implementar a lógica de criptografia, descriptografia e interação com o DOM. Ele também contém funções auxiliares para manipulação de classes CSS e cópia de texto para a área de transferência.

## Como Usar

1. **Criptografar:** Insira um texto na caixa de texto e clique no botão "Criptografar". As vogais serão substituídas pelas palavras correspondentes.
2. **Descriptografar:** Para reverter o texto criptografado, insira o texto criptografado na caixa de texto e clique no botão "Descriptografar".
3. **Cópia para Área de Transferência:** Após obter o texto desejado, clique no botão "Copiar Resultado" para copiá-lo para a área de transferência.

## Exemplo de Código

```javascript
document.querySelector(".criptografar").addEventListener("click", () => {
    const vogalParaCripto = {'e':'enter', 'i': 'imes', 'a': 'ai', 'o': 'ober', 'u': 'ufat'};
    const regex = /(a|e|i|o|u)/g;
    
    let text = document.querySelector("textarea").value;
    let result = decode(text, vogalParaCripto, regex);
    
    addClass(".card-container", ".display-result");
    addText(result);
});

document.querySelector(".descriptografar").addEventListener("click", () => {
    const criptoParaVogal = {enter: 'e', imes: 'i', ai: 'a', ober: 'o', ufat: 'u'};
    const regex = /(enter|imes|ai|ober|ufat)/g;
    
    let text = document.querySelector("textarea").value;
    let result = decode(text, criptoParaVogal, regex);
    
    addClass(".card-container", ".display-result");
    addText(result);
});

document.querySelector(".copy").addEventListener("click", () => {
    addClass(".display-result", ".card-container");
    copy();
});

function decode(text, fun, regex) {
    let textoDescriptografado = text.replace(regex, (match) => fun[match]);
    return textoDescriptografado;
}

function addClass(add, remove) {
    document.querySelector(add).classList.add("display");
    document.querySelector(remove).classList.remove("display");
}

function addText(text) {
    if (!text) return alert("Preencha os campos necessários.");
    document.querySelector("textarea").value = "";
    document.querySelector(".display-result > p").innerHTML = text;
}

function copy() {
    let text = document.querySelector(".display-result > p").textContent;
    navigator.clipboard.writeText(text);
}
