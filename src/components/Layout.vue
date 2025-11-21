<script setup lang="ts">
import Banner from './Banner.vue'
import NavBar from './NavBar.vue'
import Footer from './Footer.vue'
import type { NavItem } from './NavBar.vue'
import type { ContactInfo, SocialLink, PaymentMethod } from './Footer.vue'

defineProps<{
  name?: string
  navItems?: NavItem[]
  contact?: ContactInfo[]
  socialLinks?: SocialLink[]
  paymentMethods?: PaymentMethod[]
}>()
</script>

<template>
  <div class="layout">
    <Banner :name="name" />
    <NavBar :items="navItems" />
    <main class="main-content">
      <slot />
    </main>
    <Footer :contact="contact" :social-links="socialLinks" :payment-methods="paymentMethods" />
  </div>
</template>

<style scoped>
.layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.main-content {
  flex: 1;
  padding: 0;
  max-width: 100%;
  margin: 0 auto;
  width: 100%;
}

@media (max-width: 768px) {
  .main-content {
    padding: var(--spacing-text-gap);
  }
}
</style>

