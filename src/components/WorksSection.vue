<template>
  <section id="portfolio" class="section works">
    <div class="card">
      <h2 class="section-title">MY WORKS</h2>

      <div class="works-grid">
        <div
          class="work-card"
          v-for="work in works"
          :key="work.id"
          @click="openWork(work)"
        >
          <div class="work-title">{{ work.title }}</div>
        </div>
      </div>
    </div>
    <WorkModal
      v-if="isModalOpen"
      :work="activeWork"
      @close="closeModal"
    ></WorkModal>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import gsap from 'gsap';
import WorkModal from './WorkModal.vue';

const works = [
  {
    id: '102lab',
    title: '102LAB',
    description:
      '102LAB — экспериментальный веб-проект, созданный для оптимизации работы инженеров-геодезистов. Приложение обрабатывает и анализирует данные, автоматически формируя выводы и визуализации. Веб-интерфейс предоставляет пользователю гибкие и динамичные инструменты для управления объектами и процессами, находящимися в работе.',
    images: [
      new URL('@/assets/works/102lab1.png', import.meta.url).href,
      new URL('@/assets/works/102lab2.png', import.meta.url).href,
    ],
  },
  {
    id: 'terrageo',
    title: 'TERRAGEO',
    description:
      'Terrageo — командный проект, разработанный совместно с инженерами в рамках IT-чемпионата нефтяной отрасли в направлении «Разработка MVP» (профессиональный трек). Приложение предоставляет пользователю доступ к глобальной карте мира с возможностью добавления точек размещения термокос — инженерных скважин, оснащённых датчиками. В установленное время термокосы передают на платформу данные температурных измерений грунта. Полученная информация позволяет проводить комплексную оценку состояния вечномерзлых грунтов в северных регионах. Помимо визуализации данных в виде графиков и аналитических выводов, система обеспечивает гибкое переключение между термокосами и датчиками, а также прогнозирование температуры вечномерзлых грунтов на срок до 50 лет вперёд. С помощью изополей и интерфейса, приложение дает возможность детально рассмотреть значение температур в определенный участок времени.',
    images: [
      new URL('@/assets/works/Terrageo1.png', import.meta.url).href,
      new URL('@/assets/works/Terrageo2.png', import.meta.url).href,
    ],
  },
  {
    id: 'geotech',
    title: 'ГЕОТЕХНИКА',
    description:
      'ГЕОТЕХНИКА — веб-приложение для детального анализа расчётных схем в области геотехнических задач. Платформа позволяет решать различные типы задач — от линейной упругости до нелинейного анализа. Пользователь задаёт свойства линий (стенки, перекрытия и другие конструктивные элементы), характеристики материалов для полигонов (различные типы грунтов), а также расчётные этапы с помощью динамически расширяемых таблиц хранения данных. В результате система отображает различные сценарии расчётов, наглядно демонстрируя влияние выбранных свойств и параметров на окружающую среду, например, в области котлованов, тоннелей и других инженерных сооружений.',
    images: [
      new URL('@/assets/works/102labfem1.png', import.meta.url).href,
      new URL('@/assets/works/102labfem2.png', import.meta.url).href,
    ],
  },
];

onMounted(() => {
  gsap.from('.works .work-card', {
    opacity: 0,
    y: 40,
    stagger: 0.2,
    duration: 0.8,
    ease: 'power2.out',
  });
});

const activeWork = ref(null);
const isModalOpen = ref(false);

function openWork(work) {
  activeWork.value = work;
  isModalOpen.value = true;
}

function closeModal() {
  isModalOpen.value = false;
  activeWork.value = null;
}
</script>

<style scoped>
.works {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

/* Grid */
.works-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

/* Card */
.work-card {
  background: rgba(0, 0, 0, 0.15);
  border: 1px solid rgba(255, 255, 255, 0.18);
  border-radius: 16px;
  padding: 28px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  transition: border-color 0.3s, box-shadow 0.3s;
  cursor: pointer;
  /* transition: transform 0.3s ease, box-shadow 0.3s ease; */
}

/* Hover (очень мягко) */
.work-card:hover {
  border-color: rgba(255, 140, 255, 0.6);
  box-shadow: 0 0 0 1px rgba(255, 140, 255, 0.25);
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.45), 0 0 30px rgba(255, 95, 215, 0.2);
}

.work-card::before {
  content: '';
  position: absolute;
  inset: -1px;
  border-radius: inherit;
  background: linear-gradient(
    120deg,
    transparent,
    rgba(255, 95, 215, 0.6),
    rgba(139, 108, 255, 0.6),
    transparent
  );
  opacity: 0;
  transition: opacity 0.35s ease;
}

.work-card:hover::before {
  opacity: 1;
}

/* Title */
.work-title {
  text-align: center;
  font-size: 24px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-weight: 600;
  opacity: 0.85;
  text-shadow: 0 0 12px rgba(255, 122, 217, 0.75),
    0 0 28px rgba(159, 139, 255, 0.65);
}

/* Mobile */
@media (max-width: 900px) {
  .works-grid {
    grid-template-columns: 1fr;
  }
}
</style>
