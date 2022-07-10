<template>
  <h2>Calculadora</h2>
  <label for="n1">n1.</label>
  <input id="n1" type="text" v-model="n1" />
  <p></p>
  <label for="n2">n2.</label>
  <input id="n2" type="text" v-model="n2" />
  <p></p>
  <div>
    <button v-on:click="sumar">+</button>
    <button v-on:click="restar">-</button>
    <button v-on:click="multiplicar">*</button>
    <button v-on:click="dividir">/</button>
  </div>
  <p></p>
  <label>{{ obtenerOp }}</label>
  <label>{{ obtenerResultado }}</label>
</template>

<script>
export default {
  name: "Calculadora",
  data() {
    return {
      n1: '',
      n2: '',
      res: '',
      op: 'R:'
    };
  },
  methods: {
    sumar() {
      this.op = '+ R:'
      return (this.res = parseFloat(this.n1) + parseFloat(this.n2));
    },
    restar() {
      this.op = '- R:'
      return (this.res = parseFloat(this.n1) - parseFloat(this.n2));
    },
    multiplicar() {
      this.op = '* R:'
      return (this.res = parseFloat(this.n1) * parseFloat(this.n2));
    },
    dividir() {
      this.op = '/ R:'
      return (this.res = parseFloat(this.n1) / parseFloat(this.n2));
    },
  },
  computed: {
    obtenerResultado() {
      return this.res;
    },
    obtenerOp(){
      return this.op;
    }
  },
};
</script>

<style>
</style>