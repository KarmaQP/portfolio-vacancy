<template>
  <section id="about" class="section about">
    <div class="card">
      <h2 class="section-title">ABOUT ME</h2>
      <div class="about-grid">
        <div class="about-text">
          <p>
            Я — fullstack web-разработчик с уклоном в создание сложных,
            интерактивных веб-приложений и систем анализа данных. Быстро
            адаптируюсь к новым задачам и рабочей среде, довожу проекты до
            завершения и постоянно развиваю свои навыки.
          </p>
          <p>
            Мне важно быть частью команды, вносить реальный вклад в продукт и
            расти вместе с проектом. Помимо коммерческой разработки, в свободное
            время работаю над личными проектами — от игр для ПК и мобильных
            платформ до полнофункциональных веб-сервисов.
          </p>
          <p>
            Финалист Российской энергетической недели в рамках IT-чемпионата
            нефтяной отрасли (направление «Разработка MVP»). В составе команды
            ТерраГеоКонтроль занял 3 место в профессиональном треке, выступая в
            роли Fullstack web developer.
          </p>
          <p>
            В последнее время работал как самозанятый, разрабатывая
            веб-приложение для инженеров-геотехников, ориентированное на анализ
            нелинейных задач в методе конечных элементов.
          </p>
        </div>
        <div class="about-image">
          <img src="../assets/max.png" alt="Maxim's photo" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';

onMounted(() => {
  gsap.from('.about .card > *', {
    opacity: 0,
    y: 20,
    duration: 0.6,
    stagger: 0.15,
    ease: 'power2.out',
  });

  gsap.from('.section', {
    scrollTrigger: {
      trigger: '.section',
      start: 'top 80%',
    },
    y: 40,
    opacity: 0,
    duration: 1,
    ease: 'power2.out',
  });
});
</script>

<style scoped>
/* CARD */
.card {
  background: rgba(255, 255, 255, 0.04);
  border-radius: 24px;
  padding: 32px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.02);
}

.section-title {
  margin-bottom: 24px;
  letter-spacing: 2px;
}

.about-grid {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 32px;
}

.about-text {
  display: flex;
  flex-direction: column;
  gap: 8px;
  line-height: 1.6;
}

.about-image {
  border-radius: 18px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.08);
  flex-shrink: 0;
  width: 320px;
  height: 420px;
}

.about-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}
</style>
