<!-- eslint-disable vue/multi-word-component-names -->
<template>
      <div class="container">
        <div class="info">
          <h1>Exemplo 1 - Mostrando informações na tela</h1>
          <p>Nome: {{ nome }}</p>
          <p>Idade: {{ idade }} anos</p>
          <hr />
          <p>Para completar 50 anos faltam: {{ 50 - idade }} anos</p>
          <p>O nome tem {{ nome.length }} caracteres</p>
          <p>O nome invertido é: {{ inverter(nome) }}</p>
          <hr />
          <p>Exemplo de saudação usando função</p>
          <p>{{ saudacao() }}</p>
        </div>
        <div class="contador">
          <h1 class="valorContador">{{ contador }}</h1>
          <div class="container-contador">
            <button class="botaoContador" @click="contador++">+</button>
            <button class="botaoContador" @click="contador--">-</button>
            <button class="botaoContador ajusteIcon" @click="contador = 0">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
  
                <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2z"/>
                <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466"/>
                </svg>
            </button>
          </div>
          <h2 :class="contador <= 10 ? 'menorQueDez' : 'maiorQueDez'">{{ (contador <= 10) ? "Valor do contador menor ou igual a 10" : "Valor do contador maior que 10" }}</h2>
        </div>
      </div>
</template>

<script setup>
import { ref } from 'vue'
const nome = 'João Victor'
const idade = 16
const contador = ref(0)

function inverter(texto) {
  return texto.toUpperCase().split('').reverse().join('')
}

function saudacao() {
  return `Olá, ${nome}!`
}
</script>

<style scoped>
.container-pai {
    display: flex;
    align-items: center;
    height: 100vh;
}
.container {
  display: flex;
  justify-content: space-between;
}
.info {
  background-color: rgba(35, 12, 22, 1);
  padding: 20px 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
}

.contador {
    display: grid;
    grid-template-rows: 40% 30% 30%;  
    width: 300px;  
    background-color: rgba(35, 12, 22, 1);
    padding: 20px 30px;
    color: rgb(183, 210, 219);
    border-radius: 10px;
}
.container-contador {
    display: flex;
    justify-content: center;
    gap: 30px;
}

.valorContador {
    text-align: center;
    font-size: 2em;
}

.botaoContador {
    width: 50px;
    height: 50px;
    background: transparent;
    border: 1px solid #FDFDFD;
    border-radius: 5px;
    outline: none;
    color: #FDFDFD;
    font-size: 2rem;
    cursor: pointer;
}

h1 {
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}

.menorQueDez {
    font-size: 1.5rem;
    text-align: center;
    color: green;
}

.maiorQueDez {
    font-size: 1.5rem;
    text-align: center;
    color: blue;
}
</style>