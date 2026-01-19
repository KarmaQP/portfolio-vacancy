<template>
  <Teleport to="body">
    <div class="modal-overlay" @click.self="close">
      <div class="modal">
        <button class="modal-close" @click="close">✕</button>
        <h3>{{ work.title }}</h3>
        <p>{{ work.description }}</p>
        <div class="modal-images">
          <img v-for="(img, i) in work.images" :key="i" :src="img" />
        </div>
      </div>
    </div>
  </Teleport>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
  work: Object,
});

const emit = defineEmits(['close']);

function close() {
  emit('close');
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  inset: 0;

  background: rgba(5, 5, 20, 0.8);
  backdrop-filter: blur(8px);

  display: flex;
  align-items: center;
  justify-content: center;

  z-index: 99999;
}

.modal {
  width: 900px;
  max-width: 90vw;
  max-height: 90vh;
  overflow-y: auto;

  padding: 32px;
  border-radius: 24px;

  background: linear-gradient(180deg, #2b1b5a, #1a1038);

  position: relative;
  box-shadow: 0 0 0 1px rgba(255, 255, 255, 0.08),
    0 40px 120px rgba(0, 0, 0, 0.8);
}

.modal-title {
  margin-bottom: 12px;
  font-size: 28px;
}

.modal-description {
  margin-bottom: 24px;
  opacity: 0.85;
}

.modal-images {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.modal-images img {
  width: 100%;
  height: 260px;
  object-fit: cover;
  border-radius: 14px;
  aspect-ratio: 16 / 9;
}

.modal-close {
  position: absolute;
  top: 16px;
  right: 16px;

  background: none;
  border: none;

  color: white;
  font-size: 22px;
  cursor: pointer;
  opacity: 0.7;
}

.modal-close:hover {
  opacity: 1;
}
</style>
