<script setup lang="ts">
export interface Review {
  id: string | number
  name: string
  rating: number
  text: string
}

const props = defineProps<{
  title?: string
  reviews: Review[]
}>()

const renderStars = (rating: number) => {
  const fullStars = Math.floor(rating)
  const hasHalfStar = rating % 1 !== 0
  const emptyStars = 5 - fullStars - (hasHalfStar ? 1 : 0)
  return '★'.repeat(fullStars) + (hasHalfStar ? '☆' : '') + '☆'.repeat(emptyStars)
}

const getReviewClass = (index: number, total: number): string => {
  if (index < 3) return `review-${['1st', '2nd', '3rd'][index]}`
  if (total === 4 && index === 3) return 'review-4th'
  if (total === 5) return index === 3 ? 'review-4th-of-5' : 'review-5th'
  return ''
}
</script>

<template>
  <section class="reviews-section full-width-section">
    <div class="reviews-container content-container">
      <h2 class="reviews-title section-title-aligned">{{ props.title || 'REVIEWS' }}</h2>
      
      <div class="reviews-grid">
        <div 
          v-for="(review, index) in props.reviews" 
          :key="review.id" 
          class="review-card"
          :class="getReviewClass(index, props.reviews.length)"
        >
          <div class="review-stars">{{ renderStars(review.rating) }}</div>
          <p class="review-text">{{ review.text }}</p>
          <p class="review-name">— {{ review.name }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.reviews-section {
  margin-top: var(--spacing-section-margin-top);
  background-color: var(--color-bg-section-primary);
  padding: var(--spacing-section-padding) 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.reviews-container {
  margin-bottom: var(--spacing-container-bottom);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.reviews-title {
  margin: 0 0 var(--spacing-title-bottom-large) 0;
  font-size: var(--font-size-title-large);
  font-weight: var(--font-weight-normal);
  color: var(--color-text-primary);
  text-align: left;
  width: 100%;
}

.reviews-grid {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: var(--spacing-content-gap);
  width: 100%;
  padding-left: calc(var(--spacing-nav-button) + var(--spacing-gap));
  padding-right: calc(var(--spacing-nav-button) + var(--spacing-gap));
}

/* First row - 3 reviews spanning 2 columns each */
.review-1st {
  grid-column: 1 / 3;
}

.review-2nd {
  grid-column: 3 / 5;
}

.review-3rd {
  grid-column: 5 / 7;
}

/* When there are 4 reviews, center the 4th below the 2nd (columns 3-4) */
.review-4th {
  grid-column: 3 / 5;
  justify-self: center;
}

/* When there are 5 reviews - position between columns */
.review-4th-of-5 {
  /* Position between 1 and 2 - spans columns 2-3 */
  grid-column: 2 / 4;
  justify-self: center;
}

.review-5th {
  /* Position between 2 and 3 - spans columns 4-5 */
  grid-column: 4 / 6;
  justify-self: center;
}

.review-card {
  background-color: var(--color-white);
  padding: var(--spacing-content-gap);
  display: flex;
  flex-direction: column;
}

.review-stars {
  font-size: var(--font-size-icon-large);
  color: var(--color-accent);
  margin-bottom: var(--spacing-text-gap);
  line-height: 1;
}

.review-text {
  color: var(--color-text-secondary);
  font-size: var(--font-size-body-large);
  line-height: 1.6;
  margin: 0 0 var(--spacing-content-medium) 0;
  font-weight: var(--font-weight-light);
}

.review-name {
  color: var(--color-accent);
  font-size: var(--font-size-body-large);
  font-weight: var(--font-weight-normal);
  margin: 0;
  margin-top: auto;
}

@media (max-width: 768px) {
  .reviews-grid {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-content-gap);
    padding-left: var(--spacing-text-gap);
    padding-right: var(--spacing-text-gap);
  }

  .review-1st,
  .review-2nd,
  .review-3rd,
  .review-4th,
  .review-4th-of-5,
  .review-5th {
    grid-column: unset;
    justify-self: unset;
  }
  
  .reviews-container {
    padding: 0 var(--spacing-text-gap);
  }
  
  .reviews-title {
    font-size: var(--font-size-title-medium);
    padding-left: var(--spacing-text-gap);
  }
}
</style>

