<template>
    <div class="ocean-view" ref="oceanView">
      <div class="layer layer-1" :style="{ opacity: opacityValues[0] }"></div>
      <div class="layer layer-2" :style="{ opacity: opacityValues[1] }"></div>
      <div class="layer layer-3" :style="{ opacity: opacityValues[2] }"></div>
      <div class="layer layer-4" :style="{ opacity: opacityValues[3] }"></div>
      <div class="layer layer-5" :style="{ opacity: opacityValues[4] }"></div>
      <div class="scroll-indicator">Desplázate hacia abajo</div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  
  const opacityValues = ref([0.2, 0.4, 0.6, 0.8, 1]); // Opacidad de las capas
  const oceanView = ref<HTMLElement | null>(null);
  
  const handleScroll = () => {
    if (oceanView.value) {
      const scrollTop = oceanView.value.scrollTop;
      const maxScroll = oceanView.value.scrollHeight - oceanView.value.clientHeight;
  
      const newOpacityValues = opacityValues.value.map((value, index) => {
        // Calcula nueva opacidad basada en el desplazamiento
        return Math.max(0, value - (scrollTop / maxScroll) * (index + 1));
      });
  
      opacityValues.value = newOpacityValues;
    }
  };
  
  onMounted(() => {
    // Agregar un listener de desplazamiento al contenedor
    if (oceanView.value) {
      oceanView.value.addEventListener('scroll', handleScroll);
      // Se asegura que se desplaza al iniciar
      oceanView.value.scrollTop = 0;
    }
  });
  
  onBeforeUnmount(() => {
    // Limpiar el listener de desplazamiento al desmontar
    if (oceanView.value) {
      oceanView.value.removeEventListener('scroll', handleScroll);
    }
  });
  </script>
  
  <style scoped>
  .ocean-view {
    position: relative;
    height: 100vh; /* Ocupa toda la altura de la ventana */
    overflow-y: scroll; /* Permite el desplazamiento vertical */
    overflow-x: hidden; /* Oculta el desbordamiento horizontal */
  }
  
  .layer {
    position: relative; /* Cambiado a relativo para que cada layer ocupe su espacio */
    width: 100%;
    height: 100vh; /* Cada layer ocupa toda la altura de la ventana */
    transition: opacity 0.5s ease; /* Suaviza la transición de opacidad */
  }
  
  .layer-1 {
    background-color: rgba(0, 153, 255, 0.2); /* Capa más clara */
  }
  
  .layer-2 {
    background-color: rgba(0, 153, 255, 0.4);
  }
  
  .layer-3 {
    background-color: rgba(0, 153, 255, 0.6);
  }
  
  .layer-4 {
    background-color: rgba(0, 153, 255, 0.8);
  }
  
  .layer-5 {
    background-color: rgba(0, 153, 255, 1); /* Capa más oscura */
  }
  
  .scroll-indicator {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    color: white;
    font-size: 18px;
    background-color: rgba(0, 0, 0, 0.5);
    padding: 10px;
    border-radius: 5px;
  }
  </style>
  