<script setup lang="ts">
import { ref } from 'vue'

const email = ref('')
const submitted = ref(false)

const handleSubmit = (e: Event) => {
  e.preventDefault()
  if (email.value) {
    // Handle newsletter signup logic here
    submitted.value = true
    email.value = ''
    setTimeout(() => {
      submitted.value = false
    }, 3000)
  }
}
</script>

<template>
  <section class="newsletter-section full-width-section">
    <div class="newsletter-container content-container">
      <h2 class="newsletter-title section-title-aligned">SIGN UP FOR OUR NEWSLETTER</h2>
      <form class="newsletter-form" @submit="handleSubmit">
        <input
          v-model="email"
          type="email"
          class="newsletter-input"
          placeholder="Enter your email"
          required
        />
        <button type="submit" class="newsletter-button">Subscribe</button>
      </form>
      <p v-if="submitted" class="newsletter-success">Thank you for subscribing!</p>
    </div>
  </section>
</template>

<style scoped>
.newsletter-section {
  margin-top: var(--spacing-section-margin-top);
  background-color: var(--color-bg-section-secondary);
  padding: var(--spacing-section-padding) 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.newsletter-container {
  width: 80%;
  max-width: 80%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0;
  box-sizing: border-box;
}

.newsletter-title {
  margin: 0 0 var(--spacing-title-bottom) 0;
  font-size: var(--font-size-title-large);
  font-weight: var(--font-weight-normal);
  color: var(--color-text-primary);
  text-align: center;
  width: 100%;
}

.newsletter-form {
  display: flex;
  gap: var(--spacing-gap);
  width: 100%;
  max-width: 600px;
  align-items: center;
  padding-left: calc(var(--spacing-nav-button) + var(--spacing-gap));
  padding-right: calc(var(--spacing-nav-button) + var(--spacing-gap));
  box-sizing: border-box;
}

.newsletter-input {
  flex: 1;
  padding: var(--spacing-text-gap) var(--spacing-gap);
  font-size: var(--font-size-body-large);
  font-weight: var(--font-weight-light);
  color: var(--color-text-primary);
  background-color: var(--color-white);
  border: 1px solid var(--color-border);
  font-family: inherit;
  box-sizing: border-box;
  outline: none;
  transition: border-color 0.2s;
}

.newsletter-input:focus {
  border-color: var(--color-accent);
}

.newsletter-input::placeholder {
  color: var(--color-text-secondary);
  opacity: 0.6;
}

.newsletter-button {
  padding: var(--spacing-text-gap) var(--spacing-gap-large);
  font-size: var(--font-size-body-large);
  font-weight: var(--font-weight-normal);
  color: var(--color-white);
  background-color: var(--color-text-primary);
  border: 1px solid var(--color-text-primary);
  cursor: pointer;
  transition: background-color 0.2s, color 0.2s;
  font-family: inherit;
  white-space: nowrap;
}

.newsletter-button:hover {
  background-color: var(--color-accent-dark);
  border-color: var(--color-accent-dark);
}

.newsletter-success {
  margin: var(--spacing-text-gap) 0 0 0;
  font-size: var(--font-size-body-large);
  color: var(--color-accent);
  font-weight: var(--font-weight-normal);
  padding-left: calc(var(--spacing-nav-button) + var(--spacing-gap));
  box-sizing: border-box;
  width: 100%;
}

@media (max-width: 768px) {
  .newsletter-form {
    flex-direction: column;
    padding-left: var(--spacing-text-gap);
    padding-right: var(--spacing-text-gap);
  }
  
  .newsletter-input {
    width: 100%;
  }
  
  .newsletter-button {
    width: 100%;
  }
  
  .newsletter-title {
    font-size: var(--font-size-title-medium);
    padding-left: var(--spacing-text-gap);
  }
  
  .newsletter-success {
    padding-left: var(--spacing-text-gap);
  }
}
</style>

