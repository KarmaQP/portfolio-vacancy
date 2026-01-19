<template>
  <section id="skills" class="section skills">
    <div class="card">
      <h2 class="section-title">MY SKILLS</h2>
      <div class="skills-grid">
        <div class="skills-list">
          <div class="skill" v-for="skill in skills" :key="skill.name">
            <span>{{ skill.name }}</span>
            <div class="bar">
              <div class="fill" :style="{ width: skill.value + '%' }"></div>
            </div>
          </div>
        </div>
        <div class="skills-visual">
          <img src="../assets/skills.jpg" alt="My skills" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';

const skills = [
  { name: 'HTML / CSS', value: 75 },
  { name: 'JS', value: 85 },
  { name: 'Vue', value: 80 },
  { name: 'Django', value: 75 },
  { name: 'TypeScript', value: 40 },
  { name: 'Frontend', value: 80 },
  { name: 'Backend', value: 70 },
];

onMounted(() => {
  gsap.from('.skills h2', {
    opacity: 0,
    y: 20,
    duration: 0.6,
    stagger: 0.15,
    ease: 'power2.out',
  });

  gsap.from('.skills .skills-visual', {
    opacity: 0,
    y: 20,
    duration: 0.6,
    stagger: 0.15,
    ease: 'power2.out',
  });

  gsap.from('.skills .skill', {
    opacity: 0,
    y: 20,
    stagger: 0.2,
    duration: 0.6,
  });

  gsap.from('.skills .fill', {
    width: 0,
    duration: 1,
    stagger: 0.2,
    ease: 'power2.out',
  });
});
</script>

<style scoped>
.card {
  background: rgba(255, 255, 255, 0.04);
  border-radius: 24px;
  padding: 32px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.02);
}

.skills-grid {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 32px;
}

.skills-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.skill span {
  display: block;
  margin-bottom: 8px;
  font-size: 14px;
}

.bar {
  height: 8px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 8px;
  overflow: hidden;
}

.fill {
  height: 100%;
  border-radius: 8px;
  background: linear-gradient(90deg, #ff4fd8, #8b6cff);
}

.skills-visual {
  overflow: hidden;
  flex-shrink: 0;
  width: 420px;
}

.skills-visual img {
  max-width: 100%;
  height: auto;
  display: block;
  object-fit: cover;
}
</style>
