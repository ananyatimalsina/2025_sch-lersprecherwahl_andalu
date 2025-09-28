<template>
  <div class="timeline-card-absolute">
    <div class="timeline-bar-container">
      <div class="timeline-title">{{ title }}</div>
      <div class="timeline-bar">
        <span class="timeline-dot"></span>
      </div>
    </div>
    <div class="timeline-card">
      <h2>{{ heading }}</h2>
      <div class="timeline-card-content">
        <slot>{{ description }}</slot>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  heading: String,
  description: String
})
</script>

<style scoped>
.timeline-card-absolute {
  position: absolute;
  width: 100vw;
  left: 0;
  top: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  pointer-events: none; /* Prevent stacking card from catching click */
}

.timeline-bar-container {
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 1rem;
  margin-bottom: 2rem;
  position: relative;
}

.timeline-title {
  color: #fff;
  font-size: 1rem;
  font-family: 'DM Serif Display', serif;
  font-weight: 600;
  margin-bottom: 0.7rem;
  text-align: center;
}

.timeline-bar {
  width: 80vw;
  max-width: 900px;
  height: 4px;
  background: #fff;
  border-radius: 2px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.timeline-dot {
  width: 18px;
  height: 18px;
  background: #fff;
  border-radius: 50%;
  border: 0;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.timeline-card {
  min-width: 420px;
  max-width: 700px;
  min-height: 400px;
  background: #18181a;
  border-radius: 1.5rem;
  color: #fff;
  padding: 2.8rem 2.1rem;
  margin-bottom: 2.5rem;
  font-family: 'DM Serif Display', serif;
  box-shadow: none;
  border: 1px solid #222;
  pointer-events: auto; /* Only the card can receive pointer events */
  z-index: 2;
}
.timeline-card h2 {
  font-size: 2.3rem;
  font-weight: bold;
  color: #fff;
  margin-bottom: 1.3rem;
  letter-spacing: -0.01em;
}
.timeline-card-content {
  font-size: 1.23rem;
  color: #fafaff;
  line-height: 1.7;
  font-family: 'Inter', sans-serif;
  max-height: 440px;
  overflow-y: auto;
}
</style>
