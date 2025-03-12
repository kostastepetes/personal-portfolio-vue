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
            <img 
              :src="item.image" 
              :alt="item.title" 
              :width="item.width" 
              :height="item.height" 
              loading="lazy" 
              class="img-cover" 
            />
            <div class="card-content">
              <h3 class="h3 card-title">{{ item.title }}</h3>
              <p class="card-text">{{ item.description }}</p>
            </div>
            <a :href="item.url" target="_blank" rel="noopener noreferrer" class="layer-link"></a>
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
    const portfolioItems = ref([
      { 
        title: 'Creative Juice', 
        description: '🥤 Creative Juice is an online platform that connects creative people and allows them to exchange knowledge and ideas online or face-to-face over coffee. Made with Vite + Vue 3 + Supabase + Bootstrap 5 + GSAP.', 
        image: new URL('../assets/images/portfolio-1.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://creative-juice-app.vercel.app/'
      },
      { 
        title: 'sqky | CSS Library', 
        description: '✨ sqky is a "squeaky clean" CSS library for elegant and efficient UIs made with SASS.', 
        image: new URL('../assets/images/portfolio-2.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://github.com/kostastepetes/sqky-css-library'
      },
      { 
        title: 'grab.js', 
        description: '🤝 A small (1.8 kB) and comprehensive AJAX Library.', 
        image: new URL('../assets/images/portfolio-3.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://grab-js.netlify.app/' 
      },
      { 
        title: 'HarmoniaSuite', 
        description: '📊 CRM System for small businesses. Features include Contacts, Leads, Deals, Tasks, Campaigns, Calendar and Notes. Made in Vue 3 (Composition API) + Pinia.js + TailwindCSS.', 
        image: new URL('../assets/images/portfolio-14.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://small-business-crm.netlify.app/'
      },
      { 
        title: 'Sheltered | Secure Video/Chat Hybrid App', 
        description: '🎦 Sheltered is a hybrid application which allows pairs of users to securely and privately set up and make video calls and chat over the internet. Developed as part of my University Thesis using web technologies.', 
        image: new URL('../assets/images/portfolio-4.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://library.iated.org/view/TEPETES2023SHE' 
      },
      { 
        title: 'Web Personalization - UI Campaign Commercial Projects', 
        description: '🛒 Frontend Web Development work for clients like DolceGabbana, Ducati, Lavazza, and more. Associated with Deloitte Greece.', 
        image: new URL('../assets/images/portfolio-5.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://www.deloittedigital.com/ch/en/insights/2023/SFMC-Full-Stack-Partner.html' 
      },
      { 
        title: 'HAR Analyzer', 
        description: '🧙‍♂️ MERN stack website that operates as a crowdsourcing platform to upload, analyze, and process HAR files (HTTP Archives).', 
        image: new URL('../assets/images/portfolio-6.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://github.com/kostastepetes/HAR-Analyzer-Website-MERN' 
      },
      { 
        title: 'Luxury Transfers & Tours Booking Website', 
        description: '🚌 Luxury Transportation & Athens Tours Company website. Made in Vue.js 3, TailwindCSS and GSAP.', 
        image: new URL('../assets/images/portfolio-15.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://agtransfers.gr/' 
      },
      { 
        title: 'Island Tour Booking Website', 
        description: '🚙 Off-Road Tour Booking website for the island of Crete made in Vue.js 3, TailwindCSS and PagesCMS.', 
        image: new URL('../assets/images/portfolio-13.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://thecretanpathfinders.gr/' 
      },
      { 
        title: 'Island Transfer Booking Website', 
        description: '🚖 Transportation Company Booking website for tourists in Paros. Made in Vue.js 3, TailwindCSS.', 
        image: new URL('../assets/images/portfolio-12.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://expresstransferparos.com/' 
      },
      { 
        title: 'Psychologist Website', 
        description: '👨‍⚕️ A website for a psychologist’s office, designed and developed using Vue.js and TailwindCSS.', 
        image: new URL('../assets/images/portfolio-7.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://jasonsinos.netlify.app/' 
      },
      { 
        title: 'Civil Engineering Firm Website', 
        description: '👷‍♂️ A website designed and developed for a civil engineering firm.', 
        image: new URL('../assets/images/portfolio-8.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://www.tepetes-panagiotopoulou.com/' 
      },
      { 
        title: '3D Printing Company Website', 
        description: '🚀 A website designed and developed for a 3D printing company. Built with Vue.js, Bulma, and GSAP.', 
        image: new URL('../assets/images/portfolio-9.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://infinitevectors.netlify.app/' 
      },
      { 
        title: 'Design Resources & Theory Website', 
        description: '📝 A crowdsourced collection of design resources and theory materials. Built with Nuxt.js and integrated with Notion as a CMS.', 
        image: new URL('../assets/images/portfolio-10.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://design-cheatsheet.vercel.app/' 
      },
      { 
        title: 'Personal Dashboard', 
        description: '📅 A personal dashboard featuring Notes, Calendar, Favorite Links, Kanban Board, and more. Made with Vite + Vue 3 + Pinia.', 
        image: new URL('../assets/images/portfolio-11.jpg', import.meta.url).href, 
        width: 600, 
        height: 600,
        url: 'https://dashboardmy.netlify.app/' 
      }
    ]);

    const slider = ref(null);
    const currentSlide = ref(0);

    const nextSlide = () => {
      if (currentSlide.value < portfolioItems.value.length - 1) {
        currentSlide.value++;
      } else {
        currentSlide.value = 0; // Loop to the first slide
      }
      updateSliderPosition();
    };

    const prevSlide = () => {
      if (currentSlide.value > 0) {
        currentSlide.value--;
      } else {
        currentSlide.value = portfolioItems.value.length - 1; // Loop to the last slide
      }
      updateSliderPosition();
    };

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
  
