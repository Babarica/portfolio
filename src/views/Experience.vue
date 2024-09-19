<template>
<div class="exp">
    <div class="exp-group">
        <h1 class="exp-title" :class="{ dark: !isDark }">{{ $t("EE") }}</h1>
        <div v-for="block in locale == 'ru' ? blocks : enBlocks" :key="block">
            <s-exp-card :experience="block"></s-exp-card>
        </div>
    </div>
    <u-footer></u-footer>
</div>

</template>
<script setup>
import uFooter from '@/components/uFooter.vue';
const { locale } = useI18n();
import { useI18n } from 'vue-i18n';
import { ref } from 'vue';
import sExpCard from '../components/UI/sExpCard.vue';
import { useDark } from "@vueuse/core";
const isDark = useDark();
const blocks =  ref([
        {  
            title: "HTML-Верстальщик", 
            date: "Сентябрь 2022г. - Ноябрь 2022г.", 
            place: "WebBooster", "Основные обязанности:": [ "Кроссбраузерная верстка", "Адаптивная верстка", "Mobile first верстка", "Верстка лендингов по макетам", "Поддержка существующих проектов", "Взаимодействие с project менеджерами", "Реализация кастомных javascript виджетов"],
            "Достижения:": "Сверстал порядка 10 лендингов от различных заказчиков. Сдавал сайт под ключ на wordpress. Работал с различными crm-системами такими как OpenCart, 1c bitrix, wordpress.", 
            links: ["https://babarica.github.io/Tatu-Master/", "https://babarica.github.io/Parquet-company/"], 
            "Используемый стек:": ["HTML5", "CSS3", "SCSS", "BEM", "JavaScript", "Gulp", "Git"] 
        },
        {
            title: "HTML-Верстальщик",
            date: "Сентябрь 2020г. - июнь 2021г.", 
            place: "Freelance", 
            "Основные обязанности:": ["Кроссбраузерная верстка", "Адаптивная верстка", "Mobile first верстка", "Верстка лендингов по макетам", "Поддержка существующих проектов", "Взаимодействие с project менеджерами", "Реализация кастомных javascript виджетов"],
            "Достижения:": "Получил бесценный опыт работы в команде.",
            "Используемый стек:": ["HTML5", "CSS3", "SCSS", "BEM", "JavaScript", "Gulp", "Git"] 
        },
        {
            title: "Frontend-разработчик",
             date: "Ноябрь 2022г. - Март 2023г.",
            place: "onPoint (Проектная работа)", 
            "Основные обязанности:": ["Разработка и создание новых разделов (страниц)", "Разработка новых компонентов", "Поддержка существующих проектов", "Написание бизнес логики", "Взаимодействие с backend разработчиками, аналитиками, тестировщиками", "Взаимодействие с RESTful API", "Разработка и поддержка UI kit", "Кроссбраузерная верстка", "Адаптивная верстка", "Рефакторинг кода", "Код ревью"],
            "Достижения:": "Вместе с командой из 11 человек разрабатываю крупный проект для американского рынка аналог TT ELD. Работаю с оптимизацией UI компонентов и их подключению в архитектуру приложения. Конвертирую полученные данные из бэкенда в word, pdf.", "Используемый стек:": ["Vue 3", "Vue-router", "Pinia", "Axios", "Storybook", "Vite", "Git"] 
        },
        {
            title: "Frontend-разработчик",
             date: "Июля 2023г. - по настоящее время",
            place: "Rocket Firm", 
            "Основные обязанности:": ["Разработка и создание новых разделов (страниц)", "Разработка новых компонентов", "Поддержка существующих проектов", "Написание бизнес логики", "Взаимодействие с backend разработчиками, аналитиками, тестировщиками", "Взаимодействие с RESTful API", "Разработка и поддержка UI kit", "Кроссбраузерная верстка", "Адаптивная верстка", "Рефакторинг кода", "Код ревью"],
            "Достижения:": "Успешно завершил несколько крупных проектов, работал с различными библиотеками для создания таблиц, конвертации pdf, создания Google и Yandex карт.", "Используемый стек:": ["Vue 3", "Vue-router", "Pinia", "Axios", "Storybook", "Vite", "Git"],
            links: ["https://nationalbank.kz/ru", "https://tour.market", "https://sportqory.kz/ru"]
        },
])
const enBlocks =  ref([
        {  
            title: "HTML Developer", 
            date: "September 2022 - November 2022", 
            place: "WebBooster", 
            "Основные обязанности:": [ 
                "Cross-browser HTML coding",
                "Responsive web design",
                "Mobile-first approach",
                "Landing page development from design mockups",
                "Supporting existing projects",
                "Collaborating with project managers",
                "Implementing custom JavaScript widgets"
            ],
            "Достижения:": "Developed around 10 landing pages for various clients. Delivered turnkey websites on WordPress. Worked with different CRM systems such as OpenCart, 1C Bitrix, WordPress.", 
            links: ["https://babarica.github.io/Tatu-Master/", "https://babarica.github.io/Parquet-company/"], 
            "Используемый стек:": ["HTML5", "CSS3", "SCSS", "BEM", "JavaScript", "Gulp", "Git"] 
        },
        {
            title: "HTML Developer",
            date: "September 2020 - June 2021", 
            place: "Freelance", 
            "Основные обязанности:": [
            "Cross-browser HTML coding",
                "Responsive web design",
                "Mobile-first approach",
                "Landing page development from design mockups",
                "Supporting existing projects",
                "Collaborating with project managers",
                "Implementing custom JavaScript widgets"
            ],
            "Достижения:": "Gained invaluable experience working in a team.",
            "Используемый стек:": ["HTML5", "CSS3", "SCSS", "BEM", "JavaScript", "Gulp", "Git"] 
        },
        {
            title: "Frontend Developer",
             date: "November 2022 - March 2023",
            place: "onPoint (Project work)", 
                "Основные обязанности:": [
                "Development and creation of new sections (pages)",
                "Development of new components",
                "Supporting existing projects",
                "Writing business logic",
                "Collaborating with backend developers, analysts, testers",
                "Working with RESTful API",
                "Developing and maintaining UI kit",
                "Cross-browser HTML coding",
                "Responsive web design",
                "Code refactoring",
                "Code review"
            ],
            "Достижения:": "Working on a major project for the American market similar to TT ELD with a team of 11 people. Optimizing UI components and integrating them into the application architecture. Converting backend data to Word and PDF formats.", "Используемый стек:": ["Vue 3", "Vue-router", "Pinia", "Axios", "Storybook", "Vite", "Git"] 
        },
        {
            title: "Frontend Developer",
             date: "July 2023 - Present",
            place: "Rocket Firm", 
                "Основные обязанности:": [
                "Development and creation of new sections (pages)",
                "Development of new components",
                "Supporting existing projects",
                "Writing business logic",
                "Collaborating with backend developers, analysts, testers",
                "Working with RESTful API",
                "Developing and maintaining UI kit",
                "Cross-browser HTML coding",
                "Responsive web design",
                "Code refactoring",
                "Code review"
            ],
            "Достижения:": "Successfully completed several large projects, worked with various libraries to create tables, convert pdf, create Google and Yandex maps.", "Используемый стек:": ["Vue 3", "Vue-router", "Pinia", "Axios", "Storybook", "Vite", "Git"],
            links: ["https://nationalbank.kz/ru", "https://tour.market", "https://sportqory.kz/ru"]
        },
])
</script>
<style scoped>
    .exp-title {
        font-size: 24px;
        color: var(--vt-c-black);
        margin-bottom: 25px;
    }
    .exp-title.dark {
        color: var(--vt-c-main)
    }
    .exp {
        margin-top: 181px;
    }
    @media(max-width: 724px){
        .exp {
            margin-top: 120px;
        }
    }
</style>