<script setup lang="ts">
import UnderWaterLayout from '@/layouts/UnderWaterLayout.vue';
import { onMounted } from 'vue';
import $ from 'jquery';
import 'jquery.ripples';  // Importa el plugin de ripples

// Aplica el efecto ripples cuando el componente se monte
onMounted(() => {
  $(".full-landing-image").ripples({
    resolution: 256,
    perturbance: 0.01,
  });
});
</script>

<template>
  <div class="full-landing-image"></div>
    <UnderWaterLayout/>


</template>

<style scoped>
body {
  margin: 0;
  padding: 0;
}

.full-landing-image {
  width: 100%;
  height: 100vh;
  background: url('https://i.postimg.cc/J07vSC9q/hero-background.jpg') no-repeat center;
  background-size: cover;
}
</style>
