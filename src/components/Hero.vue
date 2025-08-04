<template>
  <section class="hero">
    <h1 class="hero-title">Jose Corea Cruz</h1>
    <p class="hero-subtitle">Contemporary & Timeless Designs</p>
  </section>
</template>

<script>
import { onMounted } from 'vue'
import { gsap } from 'gsap'

export default {
  setup() {
    onMounted(() => {
      gsap.from('.hero-title', { y: 50, opacity: 0, duration: 1 })
      gsap.from('.hero-subtitle', { y: 20, opacity: 0, delay: 0.5, duration: 1 })
    })
  }
}
</script>

<style scoped>
.hero-title {
  font-size: 4rem;
  margin-bottom: 0.5rem;
}
.hero-subtitle {
  font-size: 1.5rem;
  opacity: 0.8;
}
</style>
