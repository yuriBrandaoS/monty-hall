<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">Quantas portas? </label>
        <input type="text" id="portsAmount" size="3"
          v-model.number="portsAmount">
      </div>
      <div v-if="!started">
        <label for="selectedPort">Qual a porta é premiada? </label>
        <input type="text" id="selectedPort" size="3"
          v-model.number="selectedPort">
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
        <Door :hasGift="i === selectedPort" :number="i"/>
      </div>
    </div>

  </div>
</template>

<script>
import Door from './components/Door'
export default {
  name: 'App',
  data() {
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null,
    };
  },
  components: {
    Door,
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}

body {
  color: #FFF;
  background: #2193b0; /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #2193b0, #6dd5ed); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #2193b0, #6dd5ed); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
  
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid transparent;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form .form input .form button {
  margin-bottom: 10px;
  font-size: 2rem;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
