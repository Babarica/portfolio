<template>
  <u-header></u-header>
  <div>
    <s-container>
      <router-view v-slot="{ Component, route }">
        <transition name="main" mode="out-in">
          <component :is="Component" :key="route.path"/>
        </transition>
      </router-view>
    </s-container>

  </div>

</template>
<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import uHeader from '@/components/uHeader.vue'
  import sContainer from '@/components/UI/sContainer.vue'
  import { useDark } from "@vueuse/core";
  const isDark = useDark({
  selector: 'body',
  attribute: 'color-scheme',
  valueDark: 'dark',
  valueLight: 'light',
})
</script>

<style>
.main-enter-active,
  .main-leave-active{
    transition: opacity 0.35s, transform 0.35s;
  }
  .main-enter-from,
  .main-leave-to {
    opacity: 0;
    transform: translateX(-30%);
  }
  body[color-scheme='light']{
    background: var(--vt-c-brown);
  }
</style>
