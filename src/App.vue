<script setup>
import { reactive } from 'vue'


const estado = reactive({
  primeiroValor: 0,
  segundoValor: 0,
  operacao: 'somar',
  total: 0,
})

function somar() {
  estado.total = Number(estado.primeiroValor) + Number(estado.segundoValor)
}

function subtrair() {
  estado.total = Number(estado.primeiroValor) - Number(estado.segundoValor)
}

function multiplicar() {
  estado.total = Number(estado.primeiroValor) * Number(estado.segundoValor)
}

function dividir() {
  estado.total = Number(estado.primeiroValor) / Number(estado.segundoValor)
}

function calcular() {
  if (estado.operacao === 'somar') {
    somar()
  }

  if (estado.operacao === 'subtrair') {
    subtrair()
  }

  if (estado.operacao === 'multiplicar') {
    multiplicar()
  }

  if (estado.operacao === 'dividir') {
    dividir()
  }
}

</script>

<template>

<div class="conteudo">
  <div class="calculadora">
<header>
  <h1>Calculadora dos Junimos</h1>
</header>
  

<section class="campo-preenchimento" id="campo-preenchimento">

  <div class="inserir" id="inserir">

  <label for="primeironumero">Primeiro valor</label>
  <input class="campo" @keyup="evento => {
  estado.primeiroValor = evento.target.value
  calcular()
}">
  </div>

<div class="operacao" id="operacao">
  <select v-model="estado.operacao">
  <option value="somar">+</option>
  <option value="subtrair">-</option>
  <option value="multiplicar">*</option>
  <option value="dividir">/</option>
</select>
</div>

<div class="inserir">
  <input class="campo" @keyup="evento => {
    estado.segundoValor = evento.target.value
    calcular()
  }">
  <label for="segundonumero">Segundo Valor</label>
  
</div>
</section>

<span>{{ estado.total }}</span>
  </div>
</div>
</template>

<style scoped>


* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "VT323", monospace;
  font-weight: 400;
}

.conteudo {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  width: 100%;
  background: linear-gradient(135deg, #151556, #026ACD, #4FC3F5, #76FBE0);
}

.calculadora {
  background-color: #f1ad64e8;
  border-radius: 5px;
    border-radius: 5px;
  border-color: #D77705;
  border-style: solid;
border-width: 6px;  
}


h1 {
  font-family: "Press Start 2P", system-ui;
    font-weight: 400;
justify-content: center;
  width: 100%;
  padding: 50px;
  display: flex;
 color: #C99317;
  letter-spacing: 2px;
  font-size: 2.5rem;
  font-weight: 700;
}
.campo-preenchimento {
justify-content: center;
  width: 100%;
  padding: 20px;
  display:flex;
}

.inserir {
  display: flex;
  align-items: center;
  color: #723119;
  font-size: 25px;
}


.campo {
  border-color: #D77705;
  border-style: solid;
border-width: 3px;  
  background-color: #F1AE64;
  color: #723119;
  text-align: center;
  font-size: 35px;
  padding: 5px;
  width: 50px;
  height: 50px;
  border-radius: 3px;
}

select {
  color: aliceblue;
  font-size: 35px;
  align-items: center;
  margin-right: 30px;
  margin-left: 30px;
  justify-content: center;
  display: flex;
  width: 50px;
  height: 50px;
  background-color: #C99317;
  border-radius: 3px;
  border-color: #D77705;
  border-style: solid;
border-width: 3px;  
cursor: pointer;
}

span {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #723119;
  color: aliceblue;
  font-size: 35px;
}

label {
  font-family: "VT323", monospace;
  font-weight: 400;
  margin-right: 8px;
  margin-left: 8px;
  text-align: center;
  justify-content: center;
  align-content: center;

}

@media (max-width: 600px) {
  .calculadora {
    width: 90%;
    margin: 0 20px;
  }

  h1 {
    font-size: 1.4rem;
    padding: 25px 15px;
    letter-spacing: 1px;
    text-align: center;
  }

  .campo-preenchimento {
    flex-direction: column;
    gap: 15px;
    padding: 15px;
  }

  .inserir {
    flex-direction: column;
    font-size: 18px;
  }

  .campo {
    width: 60px;
    height: 60px;
    font-size: 28px;
  }

  select {
    width: 60px;
    height: 60px;
    font-size: 28px;
    margin: auto;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  label {
    margin: 0;
    font-size: 18px;
  }

  span {
    font-size: 28px;
    padding: 15px;
  }
}
</style>
