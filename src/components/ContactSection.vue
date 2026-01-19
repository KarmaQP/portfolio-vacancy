<template>
  <section id="contact" class="section contact">
    <div class="card">
      <h2 class="section-title">CONTACT</h2>

      <div class="contact-list">
        <a
          href="mailto:quiteplacedev@gmail.com"
          target="_blank"
          class="contact-item"
          >Email</a
        >
        <a
          href="https://github.com/KarmaQP"
          target="_blank"
          class="contact-item"
          >GitHub</a
        >
        <a href="https://t.me/sunlirick" target="_blank" class="contact-item"
          >Telegram</a
        >
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

/* Contacts row */
.contact-list {
  display: flex;
  gap: 48px;
}

/* Item */
.contact-item {
  font-size: 13px;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.75);
  text-decoration: none;
  position: relative;
  padding-bottom: 6px;
  transition: color 0.3s ease;
}

/* Hover */
.contact-item::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, #ff5fd7, #8b6cff);
  opacity: 0;
  transition: opacity 0.3s;
}

.contact-item:hover {
  color: #fff;
  text-shadow: 0 0 12px rgba(255, 95, 215, 0.8);
}

.contact-item:hover::after {
  opacity: 1;
  transform: scaleX(1);
}

.contact-item::after {
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

/* Mobile */
@media (max-width: 600px) {
  .contact-list {
    flex-direction: column;
    gap: 20px;
  }
}
</style>
