<template>
  <p></p>
  <label for="nombre">Nombre {{ muestraTipo }}</label>
  <input id="nombre" type="text" />
  <p></p>
  <label for="nombre">Apellido {{ muestraTipo }}</label>
  <input id="nombre" type="text" />
  <p></p>
  <label for="nombre">Correo {{ muestraTipo }}</label>
  <input id="nombre" type="text" />
  <p></p>
</template>

<script>
export default {
  name: "Contador123",
  props: {
    tipo: String,
  },
  data() {
    return {};
  },
  methods: {},
  computed: {
    muestraTipo() {
      return this.tipo || "Tipo Vacio";
    },
  },
};
</script>

<style>
label {
  display: block;
}
</style>