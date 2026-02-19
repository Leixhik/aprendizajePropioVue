<script setup>
import { ref } from "vue";
import ApplauseCount from "./components/ApplauseCount.vue";

// const totalAplausos = ref(0);
const categorias = ref([
  { id: 1, nombre: "Diseño", puntos: 0 },
  { id: 2, nombre: "Lógica", puntos: 0 },
  { id: 3, nombre: "Esfuerzo", puntos: 0 },
]);

</script>

<template>
  <div v-for="categoria in categorias" :key="categoria.id">
    <h1>
      Cantidad de aplausos en"{{ categoria.nombre }}": {{ categoria.puntos }}
    </h1>
  <ApplauseCount :puntos="categoria.puntos" @aumentar="categoria.puntos++" />
  </div>
</template>