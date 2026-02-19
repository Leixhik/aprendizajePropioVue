<script setup>
import { computed } from 'vue'

  // Declarar que recibire 'puntos'
  const props = defineProps({
    puntos: {
      type: Number,
      required: true,
      // default: 0 -- Opcional en este caso, pues es redundante.
    }
  })
  // Declarar que voy a avisar con 'aumentar'
  const emit = defineEmits(['aumentar'])

  function manejarClick(){
    // Aqui lanzare ese aviso.
    // usare la funcion emit('nombre-del-evento')
    emit('aumentar')
  }



  const claseBoton = computed(() => {
    if (props.puntos > 10) {
      return 'gold-button'
    } else {
      return 'normal-button'
    }
  })

</script>

<template>
  <button
    :class="claseBoton"
    @click="manejarClick"
  >Aplauso</button>
  <h1>Llevas {{ props.puntos }} aplausos</h1>
</template>

<style scoped>
  .normal-button{
    background-color: green;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    cursor: pointer;
  }
  .gold-button{
    background-color: gold;
    border: none;
    color: black;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    cursor: pointer;
  }

</style>