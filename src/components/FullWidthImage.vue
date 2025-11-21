<script setup lang="ts">
const props = defineProps<{
  imagePath: string
  alt?: string
}>()
</script>

<template>
  <section class="full-width-image-section full-width-section">
    <img :src="props.imagePath" :alt="props.alt || 'Full width image'" class="full-width-image" />
  </section>
</template>

<style scoped>
.full-width-image-section {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  margin-top: var(--spacing-section-margin-top);
}

.full-width-image {
  width: 100%;
  height: auto;
  display: block;
  object-fit: cover;
}
</style>

