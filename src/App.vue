<script setup>
import { ref, computed } from "vue";
import ApplauseCount from "./components/ApplauseCount.vue";

// const totalAplausos = ref(0);
const categorias = ref([
  { id: 1, nombre: "Diseño", puntos: 0 },
  { id: 2, nombre: "Lógica", puntos: 0 },
  { id: 3, nombre: "Esfuerzo", puntos: 0 },
]);

const sumaTotal = computed(() => {
  // 1. Usamos .value porque es un ref
  // 2. El 'acc' (acumulador) empieza en 0
  // 3. 'cat' es el objeto actual (ej: {nombre: 'Diseño', puntos: 5})
  return categorias.value.reduce((acc, cat) => {
    return acc + cat.puntos
  }, 0); // 0 es el valor inicial
});

function incrementarPuntos(categoria){
  categoria.puntos++
}

</script>

<template>
  <div v-for="categoria in categorias" :key="categoria.id">
    <h1>
      Cantidad de aplausos en"{{ categoria.nombre }}": {{ categoria.puntos }}
    </h1>
    <ApplauseCount :puntos="categoria.puntos" @aumentar="incrementarPuntos(categoria)" />
  </div>

  <h2>Cantidad Total de Puntos: {{ sumaTotal }}</h2>
</template>