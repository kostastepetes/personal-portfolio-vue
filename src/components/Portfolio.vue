<template>
    <section class="portfolio" id="portfolio" aria-labelledby="portfolio-label">
      <div class="title-wrapper container">
        <div>
          <p class="section-subtitle" id="portfolio-label">My Work</p>
          <h2 class="h2 section-title">Portfolio</h2>
        </div>
        <p class="section-text">
          A wide range of projects in the web, from company/portfolio websites, to frontend libraries and Web Apps/SAAS.
        </p>
      </div>
  
      <div class="slider" ref="slider">
        <ul class="slider-container">
          <li class="slider-item" v-for="(item, index) in portfolioItems" :key="index">
            <div class="portfolio-card img-holder" :style="{ '--width': item.width + 'px', '--height': item.height + 'px' }">
              <img :src="item.image" :alt="item.title" :width="item.width" :height="item.height" loading="lazy" class="img-cover" />
              <div class="card-content">
                <h3 class="h3 card-title">{{ item.title }}</h3>
                <p class="card-text">{{ item.description }}</p>
              </div>
              <a href="#" class="layer-link"></a>
            </div>
          </li>
        </ul>
  
        <div class="slider-controls">
          <button class="slider-control prev" @click="prevSlide" aria-label="Slide to previous item">
            <div class="line"></div>
            <div class="arrow"></div>
          </button>
          <button class="slider-control next" @click="nextSlide" aria-label="Slide to next item">
            <div class="line"></div>
            <div class="arrow"></div>
          </button>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: "PortfolioSection",
    setup() {
      // Portfolio items data
      const portfolioItems = ref([
        { title: 'Creative Juice', description: '🥤 Creative Juice is an online platform that connects creative people and allows them to exchange knowledge and ideas online or face-to-face over coffee. Made with Vite + Vue 3 + Supabase + Bootstrap 5 + GSAP.', image: '/assets/images/portfolio-1.jpg', width: 600, height: 600 },
        { title: 'sqky | CSS Library', description: '✨ sqky is a "squeaky clean" CSS library for elegant and efficient UIs made with SASS', image: '../src/assets/images/portfolio-2.jpg', width: 600, height: 600 },
        { title: 'grab.js', description: '🤝 A small (1.8 kB) and comprehensive AJAX Library.', image: '../src/assets/images/portfolio-3.jpg', width: 600, height: 600 },
        { title: 'Sheltered | Secure Video/Chat Hybrid App', description: '🎦 Sheltered is a hybrid application which allows pairs of users to securely and privately set-up and make video calls and chat over the internet. No registration or authorization is required. Developed as part of my University Thesis using web technologies like JavaScript, HTML5, and CSS and frameworks like React.js, Vue.js, Node.js, Express.js, TailwindCSS, Bootstrap as well as the Ionic framework (Capacitor). Associated with University Of Patras & Became a Paper at INTED2023🎓', image: '../src/assets/images/portfolio-4.jpg', width: 600, height: 600 },
        { title: 'Web Personalization - UI Campaign Commercial Projects', description: '🛒 Frontend Web Development work, Personalized Web Campaigns, Email Templates and Landing Pages on DolceGabbana, Brunello Cucinelli, Ducati, Lavazza, ItaliaOnline, PPC/ΔΕΗ, Nexi Bank, Autotorino, LTA & DeLonghi official websites. Associated with Deloitte Greece 🟢', image: '../src/assets/images/portfolio-5.jpg', width: 600, height: 600 },
        { title: 'HAR Analyzer', description: '🧙‍♂️ MERN stack website (MongoDB + Express + React + NodeJS) that operates as a Crowdsourcing platform and allows its users to upload, analyze and process their HAR Files (HTTP Archives)', image: '../src/assets/images/portfolio-6.jpg', width: 600, height: 600 },
        { title: 'Psychologist Website', description: '👨‍⚕️ Website for a Psychologist office. Made in Vue.js and TailwindCSS and handled the entire design + development process', image: '../src/assets/images/portfolio-7.jpg', width: 600, height: 600 },
        { title: 'Civil Engineering Firm Website', description: '👷‍♂️ Website for a Civil Engineering Firm. Handled the entire design + development process', image: '../src/assets/images/portfolio-8.jpg', width: 600, height: 600 },
        { title: '3D Printing Company Website', description: '🚀 Website for a 3D Printing Company. Handled the entire design + development process. Made in Vue.js, Bulma & GSAP', image: '../src/assets/images/portfolio-9.jpg', width: 600, height: 600 },
        { title: 'Design Resources & Theory Website', description: '📝 Crowdsourced collection of design resources and theory materials for design enthusiasts and professionals alike. Made with Nuxt.js and used Notion as a CMS via the vue-notion library.', image: '../src/assets/images/portfolio-10.jpg', width: 600, height: 600 },
        { title: 'Personal Dashboard', description: '📅 Personal Dashboard with Notes, Calendar, Favorite Links, Kanban Board, Pomodoro Timer and Spotify Playlist that you can re-arrange them with drag-and-drop. Made with Vite + Vue 3 + Pinia + particles.js + vuedraggable', image: '../src/assets/images/portfolio-11.jpg', width: 600, height: 600 },
      ]);
  
      // Slider functionality
      const slider = ref(null);
      const currentSlide = ref(0);
  
      // Move to next slide
      const nextSlide = () => {
        if (currentSlide.value < portfolioItems.value.length - 1) {
          currentSlide.value++;
        } else {
          currentSlide.value = 0; // loop back to the first slide
        }
        updateSliderPosition();
      };
  
      // Move to previous slide
      const prevSlide = () => {
        if (currentSlide.value > 0) {
          currentSlide.value--;
        } else {
          currentSlide.value = portfolioItems.value.length - 1; // loop to last slide
        }
        updateSliderPosition();
      };
  
      // Update slider container position based on current slide
      const updateSliderPosition = () => {
        const container = slider.value.querySelector('.slider-container');
        const slideWidth = slider.value.querySelector('.slider-item').offsetWidth;
        container.style.transform = `translateX(-${currentSlide.value * slideWidth}px)`;
      };
  
      return {
        portfolioItems,
        nextSlide,
        prevSlide,
        slider
      };
    }
  };
  </script>
  
  <style scoped>
  /* Add styles here */
  </style>
  