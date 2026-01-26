<script setup>
import ecualizador from "./views/ecualizador.vue"
import pletina from "./views/pletina.vue";
</script>

<template>
  <div id="contenedor-padre">
    <pletina />
    <ecualizador />
  </div>
</template>

<style scoped>
#contenedor-padre {
  margin-top: 10%;
  display: flex;
  justify-content: center;
}
</style>
