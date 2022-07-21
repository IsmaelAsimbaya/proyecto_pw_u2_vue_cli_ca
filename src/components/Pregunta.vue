<template>
  <img v-if="imagen" v-bind:src="imagen" alt="no encontrado" />
  <div class="bg-oscuro"></div>
  <div class="pregunta-container">
    <input v-model="pregunta" type="text" placeholder="Preguuuntamee..." />
    <p>Recuerda terminar con un signo de pregunta (?)</p>

    <div v-if="preguntaValida">
      <h2>{{ pregunta }}</h2>
      <h1>{{ respuesta }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pregunta",
  data() {
    return {
      pregunta: "Seré millonario ?",
      respuesta: null,
      imagen: null,
      preguntaValida: false,
    };
  },
  methods: {
    //cuando se llama al API se debe tenr una palabra reservada al inicio
    async obtenerRespuesta() {
      this.respuesta = "Pensando.";
      this.respuesta = "Pensando..";
      const { answer, image } = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      this.respuesta = "Pensando...";

      console.log("Respuesta");
      console.log(answer);
      console.log(image);
      this.respuesta = answer;
      this.imagen = image;
    },
    async consultaCovid() {
      const data = await fetch(
        "https://api.covidtracking.com/v1/us/current.json"
      ).then((r) => r.json());
      const { negative } = data[0];
      console.log(negative);
    },
    async animeGif() {
      const { url } = await fetch(
        "https://api.satou-chan.xyz/api/endpoint/happy"
      ).then((r) => r.json());
      console.log(url);
      this.imagen = url;
    },



  },
  watch: {
    //permite observar los cambios
    pregunta(valor, oldValue) {
      console.log("Actual: " + valor);
      console.log("Anterior: " + oldValue);
      console.log(valor.includes("?"));

      if (!valor.includes("?")) return;
      this.preguntaValida = true;
      console.log("Si Incluye");
      //Llamar y consultar al API
      this.obtenerRespuesta();
      this.consultaCovid();
      this.animeGif();
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