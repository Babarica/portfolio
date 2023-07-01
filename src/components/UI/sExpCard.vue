<template>
    <div :class="{ dark: !isDark }" class="exp-main">
        <div :class="{ dark: !isDark }" class="exp-group">
            <h2 class="exp-title">{{ experience.title}}</h2>
            <p :class="{ dark: !isDark }" class="exp-date">{{ experience.date }}</p>
        </div>
      <p class="exp-place">{{ experience.place }}</p>
      <h3 class="exp-must">{{ $t("EM") }}</h3>
      <ul>
        <li :class="{ dark: !isDark }" class="exp-duty" v-for="duty in experience['Основные обязанности:']" :key="duty">{{ duty }}</li>
      </ul>
      <h3 class="exp-achiv">{{ $t("EA") }}</h3>
      <p :class="{ dark: !isDark }" class="exp-achiv__text">{{ experience['Достижения:'] }}</p>
      <h3 class="exp-stack">{{ $t("ES") }}</h3>
      <div class="exp-inner">
        <p :class="{ dark: !isDark }" class="exp-item" v-for="tech in experience['Используемый стек:']" :key="tech">{{ tech }}</p>
      </div>
      <h3 class="exp-link" v-show="experience.links">Ссылки на работы:</h3>
      <ul>
        <li  class="exp-link__item" v-for="link in experience.links" :key="link">
          <a :class="{ dark: !isDark }" :href="link">{{ link }}</a>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
    import { useDark } from "@vueuse/core";
  export default {
    setup(){
        const isDark = useDark();
        return { isDark }
    },
    props: {
      experience: {
        type: Object,
        default: ''
      }, // Принимаем объект с данными опыта работы в качестве пропса
    },
  };
  </script>
  <style scoped>
    .exp-item.dark {
        color: var(--vt-c-main);
    }
    .exp-duty.dark {
        color: var(--vt-c-main);
    }
    .exp-main {
        margin-bottom: 49px;
    }
    .exp-main.dark {
        color: var(--vt-c-main)
    }
    .exp-title {
        font-size: 24px;
        font-weight: 700;
    }
    .exp-achiv__text.dark {
        color: var(--vt-c-main)
    }
    .exp-group {
        display: flex;
        justify-content: space-between;
        margin-bottom: 11px;
    }
    .exp-group.dark {
        color: var(--vt-c-main)
    }
    .exp-link__item.dark {
        color: var(--vt-c-main)
    }
    .exp-link {
        margin-bottom: 10px;
    }
    .exp-place {
        color: #778BD4;
        margin-bottom: 11px;
    }
    .exp-must {
        font-weight: 500;
        margin-bottom: 10px;
    }
    .dark {
        color: var(--vt-c-main)
    }
    .exp-duty {
        margin-bottom: 10px;
    }
    .exp-achiv {
        margin-bottom: 19px;
    }
    .exp-achiv__text {
        margin-bottom: 30px;
    }
    .exp-inner {
        display: flex;
        margin-top: 10px;
        gap: 10px;
    }
    @media(max-width: 550px){
        .exp-group {
            flex-direction: column;
            gap: 10px;
        }
    }
  </style>