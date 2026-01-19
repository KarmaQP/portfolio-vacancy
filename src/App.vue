<template>
  <AppFrame>
    <AppNav />
    <AboutSection />
    <SkillsSection />
    <WorksSection />
    <ContactSection />
  </AppFrame>
</template>

<script setup>
import AppFrame from './components/AppFrame.vue';
import AppNav from './components/AppNav.vue';
import AboutSection from './components/AboutSection.vue';
import SkillsSection from './components/SkillsSection.vue';
import WorksSection from './components/WorksSection.vue';
import ContactSection from './components/ContactSection.vue';
import { onMounted } from 'vue';

onMounted(() => {
  window.addEventListener('mousemove', (e) => {
    document.documentElement.style.setProperty('--mouse-x', `${e.clientX}px`);
    document.documentElement.style.setProperty('--mouse-y', `${e.clientY}px`);
  });

  document.querySelectorAll('.card').forEach((card) => {
    card.addEventListener('mousemove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;

      card.style.setProperty('--mx', `${x}px`);
      card.style.setProperty('--my', `${y}px`);
    });
  });
});
</script>
