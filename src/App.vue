<script setup>
import { ref } from "vue";
import ApplauseCount from './components/ApplauseCount.vue';

const totalAplausos = ref(0)
</script>

<template>
  <h1>Total de Aplausos: {{ totalAplausos }}</h1>
  <ApplauseCount
    :puntos="totalAplausos"
    @aumentar="totalAplausos++" />
</template>
