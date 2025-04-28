<script setup lang="ts">
import Logo from '@/assets/images/logo.svg'
import { RouterLink } from 'vue-router'
interface MenuLink {
  name: string
  path: string
}

const menu: MenuLink[] = [
  {
    name: 'Home',
    path: '/',
  },
  {
    name: 'About',
    path: '/about',
  },
]
</script>

<template>
  <header class="header__main">
    <div class="header__logo">
      <RouterLink to="/">
        <img :src="Logo" alt="logo" class="logo" />
      </RouterLink>
    </div>
    <nav class="header__nav">
      <ul class="header__nav-list">
        <li class="header__nav-item" v-for="item in menu" :key="item.path">
          <!-- <router-link :to="item.path">{{ item.name }}</router-link> -->
          <RouterLink :to="item.path"> {{ item.name }}</RouterLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped lang="scss">
.header {
  &__main {
    padding: 10px;
    border-bottom: 1px solid #eaeaea;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  &__logo {
    width: 100px;
    img {
      width: 100%;
      height: 100%;
    }
  }

  &__nav {
    ul {
      display: flex;
      gap: 10px;
      list-style: none;
      li {
        a {
          text-decoration: none;
          color: #000;
          font-weight: 600;
          font-family: var(--font-primary);
        }
      }
    }
  }
}
</style>
