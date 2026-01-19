<template>
  <header class="nav-wrapper">
    <div class="logo">MAX'S PORTFOLIO</div>
    <nav class="nav">
      <a
        v-for="item in navItems"
        :key="item.id"
        :href="'#' + item.id"
        @click="onClick(item.id)"
      >
        {{ item.label }}
      </a>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const navItems = [
  { id: 'about', label: 'ABOUT' },
  { id: 'skills', label: 'SKILLS' },
  { id: 'portfolio', label: 'PORTFOLIO' },
  { id: 'contact', label: 'CONTACT' },
];

const activeSection = ref('about');

function onClick(id) {
  activeSection.value = id;
}

function onScroll() {
  const sections = navItems.map((i) => document.getElementById(i.id));

  const scrollY = window.scrollY + 120;

  sections.forEach((section) => {
    if (!section) return;

    const top = section.offsetTop;
    const height = section.offsetHeight;

    if (scrollY >= top && scrollY < top + height) {
      activeSection.value = section.id;
    }
  });
}

onMounted(() => {
  window.addEventListener('scroll', onScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', onScroll);
});
</script>

<style scoped>
.nav-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 28px 24px 18px;
  position: relative;
}

/* LOGO */
.logo {
  font-size: clamp(28px, 6vw, 48px);
  letter-spacing: 0.25em;
  text-align: center;
  margin-bottom: 32px;
  text-transform: uppercase;

  background: linear-gradient(90deg, #ff7ad9, #9f8bff);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;

  text-shadow: 0 0 12px rgba(255, 122, 217, 0.45),
    0 0 28px rgba(159, 139, 255, 0.35);
}

.nav {
  display: flex;
  justify-content: center;
  gap: 40px;

  padding: 18px 24px;
  margin-bottom: 40px;

  border-bottom: 1px solid rgba(255, 255, 255, 0.15);

  position: relative;
}

.nav a {
  font-size: 15px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.75);
  text-decoration: none;
  position: relative;
  padding: 8px 4px;
  transition: color 0.3s ease;
}

.nav a:hover {
  color: #fff;
  text-shadow: 0 0 12px rgba(255, 95, 215, 0.8);
}

.nav a:hover::after {
  opacity: 1;
  transform: scaleX(1);
}

.nav a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -6px;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, #ff5fd7, #8b6cff);
  opacity: 0;
  transition: opacity 0.3s;
  height: 3px;
  border-radius: 2px;
  transition: opacity 0.3s ease, transform 0.3s ease;
  transform: scaleX(0);
  transform-origin: center;
}

.nav::after {
  content: '';
  position: absolute;
  bottom: -16px;
  left: 50%;
  transform: translateX(-50%);
  width: 80%;
  height: 1px;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.25),
    transparent
  );
}

.nav a.active {
  color: #fff;
}

.nav a.active::after {
  opacity: 1;
}
</style>
