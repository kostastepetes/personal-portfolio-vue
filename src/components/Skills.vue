<template>
    <section class="section skills" id="skills" aria-label="our skills">
      <div class="container">
        <p class="section-subtitle">Creative on the web</p>
        <h2 class="h2 section-title">I Develop & Create Digital Projects.</h2>
        
        <div class="skills-wrapper">
          <div>
            <p class="section-text">
              I am a creative front-end developer with strong expertise in modern web technologies and design principles. My skill set includes HTML, CSS, and JavaScript, complemented by extensive experience with frameworks like Vue.js, Nuxt.js, and state management using Pinia. I am proficient in SASS, Bootstrap, TailwindCSS, and Bulma, allowing me to create responsive and visually appealing user interfaces. With a solid foundation in GSAP for animations and Git for version control, I ensure efficient workflows and dynamic web experiences.
            </p>
            <p class="section-text">
              Additionally, I bring knowledge of SQL databases like MySQL and PostgreSQL, alongside Supabase integration, to create data-driven applications. My passion for UI/UX design drives me to craft intuitive and engaging digital products.
            </p>
            <a href="#" class="btn has-before">ktepetes9@gmail.com</a>
          </div>
  
          <div>
            <ul class="skills-list">
              <li v-for="(skill, index) in skills" :key="index">
                <div class="progress-wrapper">
                  <p class="progress-label">{{ skill.name }}</p>
                  <data class="progress-value" :value="skill.value">{{ skill.value }}%</data>
                </div>
                <div class="progress-bg">
                  <div class="progress" :style="{ width: skill.value + '%' }"></div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "SkillsSection",
    data() {
      return {
        skills: [
          { name: "HTML/CSS/JS", value: 95 },
          { name: "Vue.js/Nuxt.js/Pinia", value: 90 },
          { name: "SASS/Bootstrap/TailwindCSS/Bulma", value: 95 },
          { name: "GSAP", value: 85 },
          { name: "Git", value: 85 },
          { name: "SQL (MySQL, PostgreSQL), Supabase", value: 75 },
          { name: "UI/UX Design", value: 85 },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  /* Add your styles here */
  </style>
  