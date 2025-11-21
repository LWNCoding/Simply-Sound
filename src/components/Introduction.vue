<script setup lang="ts">
const props = defineProps<{
  title?: string
  text: string
  imagePath?: string
  imageAlt?: string
}>()
</script>

<template>
  <section class="introduction-section full-width-section">
    <div class="introduction-container content-container">
      <div class="introduction-content">
        <div v-if="props.imagePath" class="introduction-image-wrapper">
          <div class="introduction-image-container">
            <img :src="props.imagePath" :alt="props.imageAlt || 'Introduction image'" class="introduction-image" />
          </div>
        </div>
        
        <div class="introduction-text-section">
          <div class="introduction-separator"></div>
          <h2 class="introduction-title">{{ props.title || 'ABOUT' }}</h2>
          <div class="introduction-text">
            <p>{{ props.text }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.introduction-section {
  background-color: var(--color-bg-section-primary);
  padding: var(--spacing-section-padding) 0;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: var(--spacing-section-margin-top);
}

.introduction-container {
  width: 70%;
  max-width: 70%;
  margin: 0 auto var(--spacing-container-bottom) auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.introduction-text-section {
  display: flex;
  flex-direction: column;
  width: 100%;
  justify-self: start;
}

.introduction-separator {
  width: 100%;
  height: 1px;
  background-color: var(--color-accent);
  opacity: var(--opacity-separator);
  margin-bottom: var(--spacing-separator-bottom);
}

.introduction-title {
  margin: 0 0 var(--spacing-title-bottom) 0;
  font-size: var(--font-size-title-large);
  font-weight: var(--font-weight-normal);
  color: var(--color-text-primary);
  text-align: left;
}

.introduction-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-content-gap);
  width: fit-content;
  margin: 0 auto;
  align-items: center;
  position: relative;
  left: var(--layout-introduction-offset);
}

.introduction-text {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-text-gap);
}

.introduction-text p {
  color: var(--color-text-secondary);
  font-size: var(--font-size-body-large);
  line-height: 1.5;
  margin: 0;
  font-weight: var(--font-weight-light);
  text-align: left;
}

.introduction-image-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  justify-self: end;
}

.introduction-image-container {
  width: 75%;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--color-white);
  padding: var(--spacing-card-padding);
  box-sizing: border-box;
}

.introduction-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

@media (max-width: 768px) {
  .introduction-content {
    grid-template-columns: 1fr;
    padding-left: var(--spacing-text-gap);
    padding-right: var(--spacing-text-gap);
    left: 0; /* Reset left offset on mobile */
  }
  
  .introduction-title {
    font-size: var(--font-size-title-medium);
    padding-left: var(--spacing-text-gap);
  }
  
  .introduction-container {
    padding: 0 var(--spacing-text-gap);
  }
}
</style>

