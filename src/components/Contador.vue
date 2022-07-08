<template>
  <!--//HTML-->
  <h2>Contador</h2>
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
  data() {
    return {
      numero: 5,
    };
  },
  methods: {
    obtenerCuadrado() {
      console.log("Entro al calculo cuadrado");
      return this.numero * this.numero;
    },
    incrementar(){
        return this.numero++
    },
    decrementar(){
        return this.numero--
    }
  },
  computed: {
    obtenerCuadradoComputado() {
      console.log("Entro al calculo computado");
      return this.numero * this.numero;
    },
  },
};
</script>

<style>
button{
    background-color: #64BB87;
    border-radius: 5px;
    color: white;
    margin: 0 5px;
    cursor: pointer; 
}

button:hover{
    background-color: #5aa;
    transition: 0.3s ease-in-out;
}
</style>