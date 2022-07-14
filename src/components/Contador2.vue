<template>
  <!--//HTML-->
  <h2>{{ muestraTitulo }}</h2>
  <p>{{ numero }} <sup>2</sup> = {{ obtenerCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup> = {{ obtenerCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup> = {{ obtenerCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup> = {{ obtenerCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup> = {{ obtenerCuadradoComputado }}</p>

  <div>
    <button v-on:click="incrementar">+1</button>
    <button v-on:click="decrementar">-1</button>
  </div>
</template>

<script>
export default {
  name: "Contador123",
  props: {
    //segunda forma, declarar implicitamente el tipo de dato
    titulo: String,
    inicio: {
      type: Number,
      required: false,
      default: 100,
      validator(value){
        //validacion que retorne un true o false
        return value > 0
      }
    }
  },
  data() {
    return {
      numero: this.inicio,
    };
  },
  methods: {
    obtenerCuadrado() {
      console.log("Entro al calculo cuadrado");
      return this.numero * this.numero;
    },
    incrementar() {
      //return this.numero++
      return this.numero = this.numero + 1;
    },
    decrementar() {
      return this.numero--;
    },
  },
  computed: {
    obtenerCuadradoComputado() {
      console.log("Entro al calculo computado");
      return this.numero * this.numero;
    },
    muestraTitulo() {
      return this.titulo || "Titulo Vacio";
    },
  },
};
</script>

<style>
button {
  background-color: #64bb87;
  border-radius: 5px;
  color: white;
  margin: 0 5px;
  cursor: pointer;
}

button:hover {
  background-color: #5aa;
  transition: 0.3s ease-in-out;
}
</style>