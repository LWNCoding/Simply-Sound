<script setup lang="ts">
defineProps<{
  name?: string
}>()
</script>

<template>
  <header class="banner">
    <h1 class="banner-title">{{ name || 'Simply Sound' }}</h1>
  </header>
</template>

<style scoped>
.banner {
  width: 100%;
  background: var(--color-bg-white);
  color: var(--color-white);
  padding: var(--spacing-nav-padding-vertical) var(--spacing-text-gap);
  text-align: center;
}

.banner-title {
  margin: 0;
  color: var(--color-text-primary);
  letter-spacing: 0.05em;
  font-size: var(--font-size-title-large);
  font-weight: var(--font-weight-normal);
}

@media (max-width: 100%) {
  .banner {
    padding: var(--spacing-content-medium) var(--spacing-text-gap);
  }

  .banner-title {
    font-size: var(--font-size-title-small);
  }
}
</style>

