<script setup lang="ts">
export interface NavItem {
  label: string
  path: string
}

defineProps<{
  items?: NavItem[]
}>()
</script>

<template>
  <nav class="navbar full-width-section">
    <ul class="nav-list">
      <li v-for="item in items" :key="item.path" class="nav-item">
        <a :href="item.path" class="nav-link">{{ item.label }}</a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.navbar {
  background-color: var(--color-bg-footer);
  border-bottom: 1px solid var(--color-border);
  padding: 0;
  margin-bottom: 0;
}

.nav-list {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  justify-content: center;
  flex-wrap: wrap;
}

.nav-item {
  margin: 0;
}

.nav-link {
  display: block;
  padding: var(--spacing-nav-padding-vertical) var(--spacing-nav-padding-horizontal);
  color: var(--color-accent-dark);
  text-decoration: none;
  transition: background-color 0.2s, color 0.2s;
  font-size: var(--font-size-title-medium);
  font-weight: var(--font-weight-normal);
}

.nav-link:hover {
  background-color: var(--color-accent-dark);
  color: var(--color-bg-footer);
}

.nav-link:active {
  background-color: var(--color-border);
}

@media (max-width: 768px) {
  .nav-list {
    flex-direction: column;
  }
  
  .nav-link {
    padding: var(--spacing-content-internal) var(--spacing-nav-padding-horizontal);
    text-align: center;
  }
}

@media (prefers-color-scheme: light) {
  .navbar {
    background-color: var(--color-bg-light);
    border-bottom: 1px solid var(--color-border-light);
  }
  
  .nav-link {
    color: var(--color-text-primary);
  }
  
  .nav-link:hover {
    background-color: var(--color-bg-light-hover);
    color: var(--color-text-light-hover);
  }
  
  .nav-link:active {
    background-color: var(--color-bg-light-active);
  }
}
</style>

