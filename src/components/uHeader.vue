<template>
    <div  class="header" :class="{ scrolled: !atTopOfPage, dark: !isDark }">
        <s-container>
            <nav class="header-nav">
                <router-link class="main-logo" to="/"></router-link>
                <div class="header-group">
                    <div>                        
                        <router-link class="header-link" to="/about">{{$t("AB") }}</router-link>
                        <router-link class="header-link" to="/experience">{{$t("EX") }}</router-link>
                    </div>
                    <div class="header-group">
                        <button @click="toggleDark()" class="header-theme">
                        </button>
                        <button class="header-lang" @click="changeLang">
                            {{$t("En")}}
                        </button>
                    </div>
                    <div ref="burger" class="burger" :class="{ open: isOpen }" @click="toggleBurger">
                        <span></span>
                        <span></span>
                        <span></span>
                    </div>  
                    <div :class="{ active: isOpen, dark: !isDark }" class="header-panel"> 
                        <router-link class="header-panel__link" to="/about">{{$t("AB") }}</router-link>
                        <router-link class="header-panel__link" to="/experience">{{$t("EX") }}</router-link>
                        <button class="header-panel__link" @click="changeLang">
                            {{$t("En")}}
                        </button>
                    </div>
                </div>
            </nav>
        </s-container>  
    </div>
</template>
<script setup> 
import { onMounted, onUnmounted, ref } from 'vue' 
import sContainer from './UI/sContainer.vue' 
import { useI18n } from 'vue-i18n';
import { useDark, useToggle } from "@vueuse/core";
const isDark = useDark();
const toggleDark = useToggle(isDark);
const { locale } = useI18n();
// Переменные 
let atTopOfPage = ref(true)
let isOpen = ref(false)
let burger = ref(null)
// функции
onMounted(() => { 
  window.addEventListener('scroll', handleScroll);
  document.addEventListener('click', checkOpen);
}) 
onUnmounted(()=>{
    document.removeEventListener('click', checkOpen) 
})
function handleScroll() {
  if (window.scrollY > 0) {
    if (atTopOfPage.value) atTopOfPage.value = false
  } else {
    if (!atTopOfPage.value) atTopOfPage.value = true
  }
}
function checkOpen(event){
        if (!burger.value.contains(event.target)) {
            isOpen.value = false;
        }
}
function toggleBurger() {
      isOpen.value = !isOpen.value
      
}
function changeLang(){
    locale.value === "en"
    ? (locale.value = "ru")
    : (locale.value = "en");
}
</script>
<style scoped>
    .burger {
        width: 30px;
        height: 20px;
        display: none;
        flex-direction: column;
        justify-content: space-between;
        cursor: pointer;
        margin-left: 10px;
        position: relative;
        z-index: 1000;
    }

    .burger span {
        width: 100%;
        height: 2px;
        background-color: var(--vt-c-main);
        transition: transform 0.3s, opacity 0.3s;
        position: absolute;
    }
    .burger span:last-child{
        top: 15px;
    }
    .burger span:first-child{
        top: 7px;
    }
    .burger.open span:first-child{
        top: 0px;
    }


    .open span:first-child {
        transform: translateY(7px) rotate(45deg);
    }

    .open span:nth-child(2) {
        opacity: 0;
    }

    .open span:last-child {
        transform: translateY(-7px) rotate(-45deg);
    }
    .header {
        position: fixed;
        top: 0;
        z-index: 50;
        width: 100%;
        background-color: var(--vt-c-blue);
        padding: 19px 0px 19px;
    }
    .header.dark {
        background-color: var(--vt-c-black);
    }
    .header-group {
        display: flex;
        align-items: center;
        position: relative;
    }
    .main-logo {
        width: 47px;
        height: 47px;
        display: block;
        background: url('@/assets/img/logo.png') no-repeat center;
    }
    .header-lang {
        margin-left: 18px;
        color: var(--vt-c-main);
        font-size: 16px;
        font-style: normal;
        font-weight: 700;
        border: none;
        background: none;
        cursor: pointer;
    }
    .header-link {
        margin-right: 32px;
        color: var(--vt-c-main);
        text-decoration: none;
        font-size: 16px;
        font-family: Inter, sans-serif;
        font-style: normal;
        font-weight: 700;
    }
    .header-theme {
        width: 43px;
        height: 42px;
        display: block;
        border: none;
        cursor: pointer;
        background: url('@/assets/img/circum_sun.svg');
    }
    .header-panel {
        position: absolute;
        display: none;
    }

    .header-nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    @media(max-width: 1200px){
        .header-lang {
            display: none;
        }
        .header-panel__link {
            color: var(--vt-c-main);
            bottom: 0;
            border: none;
            text-decoration: none;
            background: none;
            font-size: 16px;
            cursor: pointer;
        }
        .header-panel {
            flex-direction: column;
            justify-content: end;
            display: flex;
            height: 300px;
            align-items: center;
            gap: 17px;
            right: -17px;
            width: 200px;
            transform: translateY(-200px);
            padding: 30px;
            transition: all 0.5s ease;
            background-color: var(--vt-c-blue);
        }
        .header-panel.dark {
            background-color: var(--vt-c-black);
        }
        .header-panel.active {
            transform: translateY(0);
        }
        
        .header-link {
            display: none;
        }
        .burger {
            display: flex;
        }
    }
</style>