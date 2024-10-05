<template>
    <div class="layer layer-1 flex items-center justify-center">
      <h1 class="title">Mi Planeta</h1> <!-- Usar la clase 'title' aquí -->
    </div>
    <div class="layer layer-2"></div>
    <div class="layer layer-3"></div>
    <div class="layer layer-4"></div>
    <div class="layer layer-5"></div>
  </template>
  
  <script setup lang="ts">
  import { defineComponent } from 'vue';
  
  defineComponent({});
  </script>
  
  <style scoped>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400..900&family=Teko:wght@300..700&display=swap');  
  .layer {
    height: 100vh; /* Cada layer ocupa toda la altura de la ventana */
    width: 100%; /* Cada layer ocupa todo el ancho de la ventana */
    position: relative; /* Se asegura de que cada layer se apile correctamente */
  }
  
  /* Gradientes para representar diferentes niveles del océano con transiciones más suaves */
  .layer-1 {
    background: linear-gradient(to bottom, rgba(173, 216, 230, 0.9), rgba(0, 204, 255, 0.8)); /* Azul claro */
  }
  
  .layer-2 {
    background: linear-gradient(to bottom, rgba(0, 204, 255, 0.8), rgba(0, 153, 255, 0.9)); /* Azul más profundo */
  }
  
  .layer-3 {
    background: linear-gradient(to bottom, rgba(0, 153, 255, 0.9), rgba(0, 102, 204, 0.7)); /* Azul intenso */
  }
  
  .layer-4 {
    background: linear-gradient(to bottom, rgba(0, 102, 204, 0.7), rgba(0, 51, 153, 0.8)); /* Azul oscuro */
  }
  
  .layer-5 {
    background: linear-gradient(to bottom, rgba(0, 51, 153, 0.8), rgba(0, 0, 102, 0.9)); /* Azul marino */
  }
  
  /* Estilo para el título */
  .title {
    font-family: 'Orbitron', sans-serif; /* Aplica la fuente Teko solo al título */
    font-weight: 700; /* Ajusta el peso de la fuente */
    color: white; /* Color blanco para el texto */
    text-align: center; /* Centra el texto */
    font-size: 6rem; /* Tamaño del texto */
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5); /* Sombra para darle más profundidad */
  }
  </style>
  