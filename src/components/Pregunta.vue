<template>
  <img src="https://via.placeholder.com/250" alt="no encontrado" />
  <div class="bg-oscuro"></div>
  <div class="pregunta-container">
    <input v-model="pregunta" type="text" placeholder="Preguuuntamee..." />
    <p>Recuerda terminar con un signo de pregunta (?)</p>
    <h2>{{ pregunta }}</h2>
    <h1>Si, No, ...Pensando</h1>
  </div>
</template>

<script>
export default {
  name: "Pregunta",
  data() {
    return {
      pregunta: "Seré millonario ?",
    };
  },
  methods: {
    //cuando se llama al API se debe tenr una palabra reservada al inicio
    async obtenerRespuesta() {
      const data = await fetch('https://yesno.wtf/api').then(
        (r) => r.json()
      );
      console.log('Respuesta');
      console.log(data);
    },
  },
  watch: {
    //permite observar los cambios
    pregunta(valor, oldValue) {
      console.log("Actual: " + valor);
      console.log("Anterior: " + oldValue);
      console.log(valor.includes("?"));

      if (!valor.includes("?")) return;

      console.log("Si Incluye");
      //Llamar y consultar al API
      this.obtenerRespuesta()
    },
  },
};
</script>

<style scoped>
img,
.bg-oscuro {
  height: 100vh;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
  left: 0px;
}

.bg-oscuro {
  background-color: rgba(0, 0, 0, 0.4);
}
.pregunta-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}

input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 20px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>