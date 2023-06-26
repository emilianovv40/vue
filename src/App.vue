<script setup>
import HelloWorld from './components/HelloWorld.vue'

//For
const names = ['C++', 'Python', 'Java', 'Vue', 'Ruby']

// importar la BaseInput para Componentes
import BaseInput from './BaseInput.vue'

//Alerta de Valores
const saveValue = value => {
  alert(value)
}

//Para Mostrar y Ocultar los Valores
const hideItem = () => {
  const p = document.querySelector('p')
  p.style.display = 'none'
}
const showItem = () => {
  const p = document.querySelector('p')
  p.style.display = 'block'
}

//Valores para directivas
import { ref } from 'vue'

const vRed = {
  mounted: (el, { value }) => {
    el.style.color = value || 'red'
  },
  updated: (el, { value }) => {
    el.style.color = value || 'red'
  },
}
const color = ref('blue')

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  </header>

  <!--Clase V-for-->
  <div>
  <h1>Ejemplo v-for</h1>
  <li v-for="(n, key) in names" :key="key">
    {{ `${key} -> ${n}` }}
  </li>
  </div>

  <!--Componentes-->
  <div>
    <h1>Ejemplo Componentes</h1>
  <BaseInput @update="saveValue"/>
  </div>

  <!--clase V-if-->
  <div>
    <h1>Prueba v-if</h1>
  <p>
    Texto de que quiero ocultar o mostrar
  </p>
  <button @click="showItem">
    mostrar texto
  </button>
  <button @click="hideItem">
    ocultar texto
  </button>
  </div>

  <!--Directivas-->

  <div>
    <h1>Ejemplo Directivas</h1>
    <p v-red="color">
    Rojo
  </p>
  <button @click="color = 'red'">
    Cambiar a rojo
  </button>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
