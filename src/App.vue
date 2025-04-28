<script setup lang="ts">
import { RouterView, useRoute } from 'vue-router'
import './assets/styles/styles.scss'
import AuthLayout from './layout/AuthLayout.vue'
import MainLayout from './layout/MainLayout.vue'
import { computed } from 'vue'

const route = useRoute()

const layout = computed(() => {
  if (route.meta.layout === 'auth') {
    return AuthLayout
  } else {
    return MainLayout
  }
})
</script>

<template>
  <component :is="layout">
    <RouterView />
  </component>
</template>
