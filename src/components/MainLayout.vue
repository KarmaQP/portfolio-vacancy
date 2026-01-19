<template>
  <div class="main-panel">
    <NavBar />

    <AboutSection />
    <SkillsSection />
    <PortfolioSection />
    <ContactSection />
  </div>
</template>

<script setup>
import NavBar from './AppNav.vue';
import AboutSection from './AboutSection.vue';
import SkillsSection from './SkillsSection.vue';
import PortfolioSection from './WorksSection.vue';
import ContactSection from './ContactSection.vue';
</script>

<style scoped>
.main-panel {
  max-width: 1100px;
  background: linear-gradient(180deg, #2a1d5f, #140b2e);
  border: 2px solid rgba(255, 255, 255, 0.15);
  border-radius: 14px;
  padding: 32px;
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.6);
}
</style>
