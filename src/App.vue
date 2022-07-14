<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!--<HelloWorld msg="Wenas to Your Vue.js App"/>-->
  <!--<Calculadora/>-->
  <!--v-bind evalua el contenido como js-->
  <Contador2 titulo="Titulo 1" v-bind:inicio="valorInicio" />
  <Contador2 titulo="Titulo 3" v-bind:inicio="6" />
  <DatosBasios v-bind:tipo="tipo"/>
  <h1></h1>
  <h1></h1>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Contador from "./components/Contador.vue";
import Contador2 from "./components/Contador2.vue";
import DatosBasios from "./components/DatosBasicos.vue"
import Calculadora from "./components/Calculadora.vue";

export default {
  name: "App",
  data() {
    return {
      valorInicio: 27,
      tipo: 'Estudiante'
    };
  },
  components: {
    Contador,
    Contador2,
    Calculadora,
    DatosBasios
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
