<template>
  <div>
    <div class="home">
      <div class="home-text">
        <p class="home-previe" :class="{ dark: !isDark }">{{$t("HH") }}</p>
        <h1 class="home-title" :class="{ dark: !isDark }">{{$t("HN") }}</h1>
        <p class="home-main__text" :class="{ dark: !isDark }">{{$t("HF") }}</p>
        <p class="home-main__text" :class="{ dark: !isDark }">{{$t("HS") }}</p>
      </div>
      <div class="home-img">
        <img src="../assets/img/me.png" alt="">
      </div>
    </div>
    <div class="home-group" :class="{ dark: !isDark }">
        <a href="mailto:ilya-lavrov-2003@list.ru?subject = Feedback&body = Message" class="home-btn mail" :class="{ dark: !isDark }">Email</a>
        <a href="https://t.me/Big_Iluxa" class="home-btn teleg" :class="{ dark: !isDark }">Telegramm</a>
        <a href="https://www.linkedin.com/in/ilya-lavrov-a77b0526b/" class="home-btn linkd" :class="{ dark: !isDark }">Linkedln</a>
        <a href="https://github.com/Babarica" class="home-btn git" :class="{ dark: !isDark }">Github</a>
      </div>
  </div>
</template>
<script setup>
import { useDark } from "@vueuse/core";
  const isDark = useDark();
</script>
<style scoped>
  .home {
    margin-top: 199px;
    display: flex;
    justify-content: space-between;
  }
  .home-previe {
    color: var(--vt-c-black);
    margin-bottom: 5px;
    font-size: 16px;
  }
  .home-text {
    color: var(--vt-c-black);
    display: flex;
    flex-direction: column;
    max-width: 540px;
  }
  .home-main__text {
    max-width: 540px;
    color: var(--vt-c-black);
    margin-bottom: 20px;
    font-size: 16px;
    display: inline-block;
  }
  .home-title {
    font-size: 64px;
    font-weight: 500;
    margin-bottom: 30px;
    display: inline;
  }
  .home-group {
    margin-top: 80px;
    display: flex;
    gap: 13px;
    color: var(--vt-c-black);
    flex-wrap: wrap;
  }
  .home-btn {
    padding: 13px 63px 13px 77px;
    border: 1px solid var(--vt-c-blue);
    background: none;
    cursor: pointer;
    position: relative;
    color: var(--vt-c-black);
    text-decoration: none;
  }
  .mail::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(../assets/img/Email.png) no-repeat center;
    left: 26%;
    top: 22%;
  }
  .teleg::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(../assets/img/Telegramm.png) no-repeat center;
    left: 24%;
    top: 22%;
  }
  .linkd::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(../assets/img/linked.svg) no-repeat center;
    left: 26%;
    top: 22%;
  }
  .git::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(../assets/img/git.svg) no-repeat center;
    left: 26%;
    top: 22%;
  }
  .home-group.dark {
    color: var(--vt-c-main)
  }
  .home-btn.dark {
    color: var(--vt-c-main)
  }
  .home-previe.dark {
    color: var(--vt-c-main)
  }
  .home-text.dark {
    color: var(--vt-c-main)
  }
  .home-main__text.dark {
    color: var(--vt-c-main)
  }
   .home-title.dark {
    color: var(--vt-c-main)
   }
   .mail.dark::after {
    background: url(../assets/img/white/email.svg) no-repeat center;
   }
   .teleg.dark::after {
    background: url(../assets/img/white/teleg.svg) no-repeat center;
   }
   .linkd.dark::after {
    background: url(../assets/img/white/linkdn.svg) no-repeat center;
   }
   .git.dark::after {
    background: url(../assets/img/white/git.svg) no-repeat center;
   }
   @media(max-width: 1000px){
    .home {
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
    .home-title {
      text-align: center;
    }
    .home-previe {
      text-align: center;
   }
   .home-group {
    justify-content: center;
    padding-bottom: 20px;
   }
  }
  @media(max-width: 724px){
    .home {
      margin-top: 120px;
    }
  }
  @media(max-width: 425px){
    .home-img img {
      max-width: 300px;
      max-height: 300px;
    }
  }
</style>
