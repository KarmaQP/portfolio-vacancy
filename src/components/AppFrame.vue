<template>
  <div class="app-frame">
    <slot />
  </div>
</template>

<style scoped>
.app-frame {
  max-width: 1100px;
  margin: 60px auto;
  padding: 32px;

  border-radius: 20px;
  background: rgba(40, 25, 80, 0.85);
  backdrop-filter: blur(16px);

  box-shadow: 0 0 0 1px rgba(255, 255, 255, 0.08),
    0 20px 60px rgba(0, 0, 0, 0.6);
}
</style>
