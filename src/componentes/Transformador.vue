<template>
  <section class="src-componentes-formulario">
    <div class="jombotron">
      <h3>Transformador de Texto</h3>
        <div class="form-group">
          <input type="text" v-model="textoEntrada" id="textoEntrada" />
        </div>
        <div v-if="textoEntrada">
          <p><strong>Cantidad de caracteres:</strong> {{ cantidadCaracteres }}</p>
          <ol>
            <li>{{ textoCodificado }} <strong> (Codificado)</strong> </li>
            <li>{{ textoMayusculas }} <strong> (Mayúscula)</strong> </li>
            <li>{{ textoMinusculas }} <strong> (Minúscula)</strong> </li>
            <li>{{ textoIntercaladoInicioMayus }} <strong>(Mayúscula / Minúscula)</strong> </li>
            <li>{{ textoIntercaladoInicioMinus }} <strong>(Minúscula / Mayúscula)</strong> </li>
          </ol>
        </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'src-componentes-formulario',
  data() {
    return {
      textoEntrada: ''
    };
  },
  methods: {
    alternarMayusculas(texto, empezarConMayuscula) {
      return texto.split('').map((char, index) => 
        index % 2 === 0 ? 
        (empezarConMayuscula ? char.toUpperCase() : char.toLowerCase()) : 
        (empezarConMayuscula ? char.toLowerCase() : char.toUpperCase())
      ).join('');
    }
  },
  computed: {
    textoCodificado() {
      const mapa = { 'a': 'u', 'e': 'o', 'i': 'i', 'o': 'e', 'u': 'a' };
      return this.textoEntrada.toLowerCase().replace(/[aeiou]/g, char => mapa[char]);
    },
    textoMayusculas() {
      return this.textoEntrada.toUpperCase();
    },
    textoMinusculas() {
      return this.textoEntrada.toLowerCase();
    },
    textoIntercaladoInicioMayus() {
      return this.alternarMayusculas(this.textoEntrada, true);
    },
    textoIntercaladoInicioMinus() {
      return this.alternarMayusculas(this.textoEntrada, false);
    },
    cantidadCaracteres() {
      return this.textoEntrada.length;
    }
  }
};

</script>

<style scoped lang="css">

  .jumbotron {
    background-color: blue;
    color: white;
  }

  form {
    margin-bottom: 20px;
  }

  h3 {
    color: purple;
  }
</style>