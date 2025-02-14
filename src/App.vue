<script setup>
import { ref, onMounted } from 'vue';
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import Service from './components/Service.vue';
import Experience from './components/Experience.vue';
import Certifications from './components/Certifications.vue';
import Skills from './components/Skills.vue';
import Portfolio from './components/Portfolio.vue';
import Footer from './components/Footer.vue';

// State to track loading
const isLoading = ref(true);

// Simulate loading effect
onMounted(() => {
  setTimeout(() => {
    isLoading.value = false; // Hide loader after 2 seconds
  }, 2000);
});
</script>

<template>
  <!-- Fullscreen Loader -->
  <div v-if="isLoading" class="loader-wrapper">
    <div class="loader"></div>
  </div>

  <!-- Main Website Content -->
  <div v-else>
    <Header />
    <Hero />
    <Service />
    <Skills />
    <Portfolio />
    <Experience />
    <Certifications />
    <Footer />
  </div>
</template>

<style scoped>
/* Fullscreen Loader Styles */
.loader-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: #FFA;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
}

/* Custom Loader */
.loader {
  display: inline-grid;
}
.loader:before,
.loader:after {
  content: "";
  height: 27px;
  aspect-ratio: 5;
  --c: #000 90deg, #0000 0;
  background:
    conic-gradient(from 135deg at top, var(--c)),
    conic-gradient(from -45deg at bottom, var(--c)) 12.5% 100%;
  background-size: 20% 50%;
  background-repeat: repeat-x;
  clip-path: inset(0 100% 0 0);
  animation: l9 1s infinite linear;
}
.loader:after {
  scale: -1 1;
}
@keyframes l9 {
  90%, to { clip-path: inset(0); }
}
</style>
