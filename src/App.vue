<script setup lang="ts">
import { RouterView, useRoute } from 'vue-router'
import './assets/styles/styles.scss'
import AuthLayout from './layout/AuthLayout.vue'
import MainLayout from './layout/MainLayout.vue'

const route = useRoute()
console.log(route)

const isAuthLayout = route.meta.layout === 'auth' ? true : false
</script>

<template>
  <div v-if="isAuthLayout">
    <AuthLayout>
      <RouterView />
    </AuthLayout>
  </div>
  <div v-else>
    <MainLayout>
      <RouterView />
    </MainLayout>
  </div>
</template>
