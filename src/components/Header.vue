<template>
    <header :class="['header', { active: isHeaderActive }]">
      <div class="container">
        <a href="#" class="logo">
          <img src="..\assets\images\logo.png" width="40" height="20" alt="KT Logo" />
        </a>
  
        <button
          class="nav-toggle-btn"
          :class="{ active: isNavOpen }"
          @click="toggleNavbar"
          aria-label="Toggle menu"
        >
          <span class="line line-1"></span>
          <span class="line line-2"></span>
        </button>
  
        <nav class="navbar" :class="{ active: isNavOpen }">
          <ul class="navbar-list">
            <li><a href="#" class="navbar-link">Home</a></li>
            <li><a href="#services" class="navbar-link">Services</a></li>
            <li><a href="#skills" class="navbar-link">Skills</a></li>
            <li><a href="#portfolio" class="navbar-link">Portfolio</a></li>
            <li><a href="#experience" class="navbar-link">Experience</a></li>
            <li><a href="#certifications" class="navbar-link">Certifications</a></li>
            <li><a href="#footer" class="navbar-link">Contact</a></li>
          </ul>
        </nav>
  
        <div
          class="overlay"
          v-if="isNavOpen"
          @click="toggleNavbar"
        ></div>
      </div>
    </header>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';
  
  // Reactive state for navbar and header
  const isNavOpen = ref(false);
  const isHeaderActive = ref(false);
  
  // Toggle function for navbar
  const toggleNavbar = () => {
    isNavOpen.value = !isNavOpen.value;
    document.body.classList.toggle("nav-active", isNavOpen.value);
  };
  
  // Scroll event to activate header on scroll
  const handleScroll = () => {
    isHeaderActive.value = window.scrollY >= 100;
  };
  
  // Setup the scroll event listener
  onMounted(() => {
    window.addEventListener("scroll", handleScroll);
  });
  
  // Cleanup the scroll event listener on unmount
  onUnmounted(() => {
    window.removeEventListener("scroll", handleScroll);
  });
  </script>
  
  <style scoped>

  </style>
  