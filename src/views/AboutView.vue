<template>
  <div class="about">
    <div class="about-main">
      <div class="about-group">
        <div class="about-text">
          <h1 :class="{ dark: !isDark }" class="about-title">
            {{$t("AT") }}
          </h1>
          <p :class="{ dark: !isDark }" class="about-text__block">{{$t("AF") }}</p>
          <p :class="{ dark: !isDark }" class="about-text__block">{{$t("AS") }}</p>
          <p :class="{ dark: !isDark }" class="about-text__block">{{$t("ATH") }}</p>
          <p :class="{ dark: !isDark }" class="about-text__block">{{$t("AFO") }}</p>
          <p :class="{ dark: !isDark }" class="about-text__block">{{$t("AFI") }}</p>
        </div>
        <div class="about-img">
          <img src="../assets/img/about.png" alt="">
        </div>
      </div>
      <div class="about-block">
        <div class="about-inner">
          <p :class="{ dark: !isDark }" class="about-stack">{{$t("AST") }}</p>
          <div class="about-blocks">
            <div :class="{ dark: !isDark }" class="about-block__blocks" v-for="sta in stack" :key="sta">
              <img :src='sta.img' alt="">
              <p>{{ sta.name }}</p>
            </div>
          </div>
        </div>
        <div class="about-inner">
          <p :class="{ dark: !isDark }" class="about-stack">{{$t("AG") }}</p>
          <div class="about-blocks">
            <div :class="{ dark: !isDark }" v-for="lea in learn" :key="lea.name" class="about-block__blocks">
              <img :src='lea.img' alt="">
              <p>{{ lea.name }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <u-footer></u-footer>
  </div>
</template>
<script setup>
import { useDark } from "@vueuse/core";
import uFooter from "../components/uFooter.vue";
import { ref } from "vue";
const isDark = useDark();
const stack = ref([
  {img: new URL('@/assets/img/about/vue.png', import.meta.url).href, name: 'Vue 2/3'},
  {img: new URL('@/assets/img/about/nuxt.png', import.meta.url).href, name: 'Nuxt 2'},
  {img: new URL('@/assets/img/about/sass.png', import.meta.url).href, name: 'Scss'},
  {img: new URL('@/assets/img/about/tail.png', import.meta.url).href, name: 'Tailwind'},
  {img: new URL('@/assets/img/about/vuex.png', import.meta.url).href, name: 'Vuex'},
  {img: new URL('@/assets/img/about/router.png', import.meta.url).href, name: 'Vue-router'},
  {img: new URL('@/assets/img/about/pinia.png', import.meta.url).href, name: 'Pinia'},
  {img: new URL('@/assets/img/about/axios.png', import.meta.url).href, name: 'Axios'},
])
const learn = ref([
  {img: new URL('@/assets/img/about/node.png', import.meta.url).href, name: 'Node js'},
  {img: new URL('@/assets/img/about/ts.png', import.meta.url).href, name: 'TypeScript'},
  {img: new URL('@/assets/img/about/docker.png', import.meta.url).href, name: 'Docker'},
])
</script>
<style scope>
  .about {
    margin-top: 181px;
  }
  .about-group {
    display: flex;
    justify-content: space-between;
  }
  .about-text {
    max-width: 605px;
  }
  .about-block {
    margin-top: -40px;
  }
  .about-title {
    font-size: 24px;
    margin-bottom: 28px;
  }
  .about-text__block {
    margin-bottom: 11px;
  }
  .about-stack {
    font-size: 24px;
    margin-bottom: 23px;
  }
  .about-blocks {
    display: flex;
    flex-wrap: wrap;
    gap: 26px 18px;
    max-width: 430px;
    margin-bottom: 24px;
  }
  .about-block__blocks {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .about-text.dark {
    color: var(--vt-c-main);
  }
  .about-title.dark {
    color: var(--vt-c-main);
  }
  .about-text__block.dark {
    color: var(--vt-c-main);
  }
  .about-stack.dark {
    color: var(--vt-c-main);
  }
  .about-block__blocks.dark p {
    color: var(--vt-c-main);
  }
  @media(max-width: 1024px){
    .about-group {
      flex-direction: column;
      align-items: center;
    }
    .about-block {
      margin-top: 40px;
      display: flex;
      flex-direction: column;
      gap: 20px;
    }
    .about-inner {
      text-align: center;
      display: inline-block;
    }
    .about-blocks {
      align-items: center;
      justify-content: center;
      margin: 10px auto 20px; 
    }
    .about-img {
      margin-top: 20px;
    }
  }
  @media(max-width: 724px){
    .about {
      margin-top: 120px;
    }
  }
  @media(max-width: 475px){
        .about-img img {
            max-width: 300px;
            max-height: 300px;
        }
    }
</style>
