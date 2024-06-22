<template>
  <div class="container mt-3">
    <div class="jumbotron">
      <h1>NT2 Parcial</h1>
      <br>
      <Transformador />
      <hr>
      <p>Respuestas: 1:C - 2:C - 3:A </p>
    </div>
  </div>
</template>

<script>

import Transformador from './componentes/Transformador.vue'

export default {
  name: 'App',
  components: {
    Transformador
  }
}
</script>

<style>
  hr {
    color: black;
  }

  .jumbotron {
    padding-top: 20px;
    padding-bottom: 20px;
  }
</style>
