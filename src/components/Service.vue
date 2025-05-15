<template>
    <section class="service" id="services" aria-labelledby="service-label">
      <div class="container">
        <div class="title-wrapper">
          <div>
            <p class="section-subtitle">
              Services That I Provide
            </p>
  
            <h2 class="h2 section-title" id="service-label">Services</h2>
          </div>
  
          <p class="section-text">
            I am an experienced in web development, eCommerce solutions, and custom website design, with a proven track record of delivering high-performing, user-friendly digital experiences. My expertise spans SEO marketing strategies that drive traffic and enhance online visibility, as well as developing and optimizing enterprise software within ecosystems like Adobe, Salesforce, and WordPress.
          </p>
        </div>
  
        <div class="slider" ref="slider" @wheel="handleWheel">
          <ul class="slider-container service-list" ref="sliderContainer">
            <!-- Repeat this block for each service item -->
            <li class="slider-item" v-for="(service, index) in services" :key="index">
              <div class="service-card">
                <div class="card-icon">
                  <ion-icon :name="service.icon"></ion-icon>
                </div>
  
                <h3 class="h3 card-title">{{ service.title }}</h3>
  
                <p class="card-text">
                  {{ service.description }}
                </p>
  
                <span class="text-lg card-number">{{ service.number }}</span>
  
                <a href="#" class="layer-link" :aria-label="'More about my ' + service.title + ' service'"></a>
              </div>
            </li>
          </ul>
  
          <div class="slider-controls">
            <button class="slider-control prev" @click="slidePrev" aria-label="Slide to previous item">
              <div class="line"></div>
              <div class="arrow"></div>
            </button>
  
            <button class="slider-control next" @click="slideNext" aria-label="Slide to next item">
              <div class="line"></div>
              <div class="arrow"></div>
            </button>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';
  
  // Reactive state for slider
  const slider = ref(null);
  const sliderContainer = ref(null);
  const currentSlidePos = ref(0);
  const totalSliderVisibleItems = ref(3);
  const totalSlidableItems = ref(0);
  
  // Services data
  const services = [
    { icon: 'desktop-outline', title: 'Web Development', description: 'Websites, Web Apps/SaaS', number: '01' },
    { icon: 'basket-outline', title: 'eCommerce', description: 'Woocommerce, Shopify', number: '02' },
    { icon: 'podium-outline', title: 'Web Design', description: 'Figma, Framer', number: '03' },
    { icon: 'color-filter-outline', title: 'Enterprise Software', description: 'Adobe, Salesforce & Wordpress Ecosystem', number: '04' },
    { icon: 'megaphone-outline', title: 'SEO Marketing', description: 'Web Performance, Content, Keywords, Links, Sitemap', number: '05' },
  ];
  
  // Slider move logic
  const moveSliderItem = () => {
    const children = sliderContainer.value.children;
    sliderContainer.value.style.transform = `translateX(-${children[currentSlidePos.value].offsetLeft}px)`;
  };
  
  const slideNext = () => {
    const slideEnd = currentSlidePos.value >= totalSlidableItems.value;
    currentSlidePos.value = slideEnd ? 0 : currentSlidePos.value + 1;
    moveSliderItem();
  };
  
  const slidePrev = () => {
    currentSlidePos.value = currentSlidePos.value <= 0 ? totalSlidableItems.value : currentSlidePos.value - 1;
    moveSliderItem();
  };
  
  // Handle mouse wheel with shift key for sliding
  const handleWheel = (event) => {
    if (event.shiftKey) {
      if (event.deltaY > 0) slideNext();
      if (event.deltaY < 0) slidePrev();
    }
  };
  
  // Update the slider dimensions on window resize
  const updateSliderDimensions = () => {
    const totalVisibleItems = Number(getComputedStyle(slider.value).getPropertyValue('--slider-items'));
    totalSliderVisibleItems.value = totalVisibleItems;
    totalSlidableItems.value = sliderContainer.value.childElementCount - totalSliderVisibleItems.value;
    moveSliderItem();
  };
  
  onMounted(() => {
    totalSlidableItems.value = sliderContainer.value.childElementCount - totalSliderVisibleItems.value;
    moveSliderItem();
    window.addEventListener('resize', updateSliderDimensions);
  });
  
  onUnmounted(() => {
    window.removeEventListener('resize', updateSliderDimensions);
  });
  </script>
  
<style></style>
  
