<template>
  <div class="page-root">
    <TheNavbar />
    <main>
      <HeroSection />
      <LogoCarousel />
    </main>
  </div>
</template>

<script setup>
// Auto-imported by Nuxt — no import statements needed for components in /components
useSeoMeta({
  title: 'LOOO – Revolutionize Your Content Creation Process',
  description: 'AI-powered content creation platform.',
})
</script>

<style scoped>
.page-root {
  min-height: 100vh;
  background: var(--bg-deep);
}
</style>