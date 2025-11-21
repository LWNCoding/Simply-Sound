<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'

export interface CarouselItem {
  id: string | number
  image: string
  title?: string
  description?: string
}

const props = defineProps<{
  title: string
  items: CarouselItem[]
}>()

const currentIndex = ref(0)
const isMobile = ref(false)

const visibleCards = computed(() => isMobile.value ? 1 : 3)

const totalPages = computed(() => Math.ceil(props.items.length / visibleCards.value))

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 768
}

onMounted(() => {
  checkMobile()
  window.addEventListener('resize', checkMobile)
})

onUnmounted(() => {
  window.removeEventListener('resize', checkMobile)
})

const nextPage = () => {
  currentIndex.value = (currentIndex.value + 1) % totalPages.value
}

const prevPage = () => {
  currentIndex.value = currentIndex.value === 0 ? totalPages.value - 1 : currentIndex.value - 1
}

const carouselTransform = computed(() => {
  if (currentIndex.value === 0) {
    return `translateX(0)`
  }
  if (isMobile.value) {
    return `translateX(-${currentIndex.value * 40}%)`
  }
  // On desktop, move by one page width plus gap
  return `translateX(calc(-${currentIndex.value * 100}% - var(--spacing-gap)))`
})
</script>

<template>
  <section class="carousel-section full-width-section">
    <div class="carousel-container content-container">
      <h2 class="carousel-title section-title-aligned">{{ props.title }}</h2>
      
      <div class="carousel-wrapper">
        <button class="carousel-nav carousel-nav-prev" @click="prevPage" aria-label="Previous">
          <svg class="carousel-arrow" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M15 18L9 12L15 6" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
        
        <div class="carousel-track">
          <div class="carousel-items" :style="{ transform: carouselTransform, width: isMobile ? `${props.items.length * 100}%` : `${totalPages * 100}%` }">
            <div class="carousel-card" v-for="item in props.items" :key="item.id">
            <div class="carousel-image-container">
              <img :src="item.image" :alt="item.title || `Item ${item.id}`" class="carousel-image" />
            </div>
            <div v-if="item.title" class="carousel-text">{{ item.title }}</div>
            <div v-if="item.description" class="carousel-description">{{ item.description }}            </div>
            </div>
          </div>
        </div>
      
        <button class="carousel-nav carousel-nav-next" @click="nextPage" aria-label="Next">
          <svg class="carousel-arrow" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M9 18L15 12L9 6" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.carousel-section {
  margin-top: var(--spacing-section-margin-top);
  background-color: var(--color-bg-section-primary);
  padding: var(--spacing-section-padding) 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel-container {
  margin-bottom: var(--spacing-container-bottom);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel-title {
  margin: 0 0 var(--spacing-title-bottom) 0;
  font-size: var(--font-size-title-large);
  font-weight: var(--font-weight-normal);
  color: var(--color-text-primary);
  text-align: left;
  width: 100%;
}

.carousel-wrapper {
  display: flex;
  align-items: center;
  gap: var(--spacing-gap);
  width: 100%;
  justify-content: flex-start;
  position: relative;
  margin: 0 auto;
}

.carousel-nav {
  background: transparent;
  border: 1px solid var(--color-text-primary);
  color: var(--color-text-primary);
  width: var(--spacing-nav-button);
  height: var(--spacing-nav-button);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background-color 0.2s, color 0.2s;
  flex-shrink: 0;
  outline: none;
}

.carousel-nav:hover {
  background-color: var(--color-text-primary);
  color: var(--color-white);
}

.carousel-arrow {
  width: 100%;
  height: 100%;
  min-width: 48px;
  max-width: 48px;
}

.carousel-track {
  flex: 1 1 0;
  overflow: hidden;
  position: relative;
  min-width: 0;
  display: flex;
  justify-content: flex-start;
  margin-left: 0;
}

.carousel-items {
  display: flex;
  gap: var(--spacing-gap);
  transition: transform 0.3s ease;
  padding-left: 0;
  box-sizing: border-box;
}

.carousel-card {
  background-color: var(--color-white);
  aspect-ratio: 3 / 4;
  flex: 0 0 calc((100% - var(--spacing-gap) * 2) / 3);
  min-width: 0;
  position: relative;
  overflow: hidden;
  padding: var(--spacing-card-padding) var(--spacing-card-padding) 0 var(--spacing-card-padding);
  display: flex;
  flex-direction: column;
}

@media (max-width: 768px) {
  .carousel-nav {
    width: 36px;
    height: 36px;
  }

  .carousel-card {
    flex: 0 0 100%;
    aspect-ratio: 4 / 5;
    max-width: 300px;
    margin: 0 auto;
    padding: var(--spacing-card-padding);
  }

  .carousel-image {
    max-height: 200px;
    object-fit: contain;
  }

  .carousel-title {
    padding-left: var(--spacing-text-gap);
    text-align: center;
  }
}

.carousel-image-container {
  width: 100%;
  flex-shrink: 0;
  overflow: hidden;
}

.carousel-image {
  width: 100%;
  height: auto;
  aspect-ratio: 1 / 1;
  object-fit: cover;
  display: block;
}

.carousel-text {
  text-align: center;
  font-weight: var(--font-weight-bold);
  margin-top: var(--spacing-text-gap);
  color: var(--color-accent);
  font-size: var(--font-size-title-medium);
}

.carousel-description {
  text-align: center;
  margin-top: var(--spacing-content-internal);
  color: var(--color-text-primary);
  font-size: var(--font-size-body-large);
  font-weight: var(--font-weight-normal);
}
</style>
