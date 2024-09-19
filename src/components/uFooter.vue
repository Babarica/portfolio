<template>
    <footer class="footer">
        <p :class="{ dark: !isDark }" class="footer-title">
            {{$t("FT") }}
        </p>
        <div class="home-group" :class="{ dark: !isDark }">
            <a href="mailto:ilya-lavrov-2003@list.ru?subject = Feedback&body = Message" class="home-btn mail" :class="{ dark: !isDark }">Email</a>
            <a href="https://t.me/gde_iluxa" class="home-btn teleg" :class="{ dark: !isDark }">Telegramm</a>
            <a href="https://www.linkedin.com/in/ilya-lavrov-a77b0526b/" class="home-btn linkd" :class="{ dark: !isDark }">Linkedln</a>
            <a href="https://github.com/Babarica" class="home-btn git" :class="{ dark: !isDark }">Github</a>
      </div>
    </footer>
</template>


<script setup>
import { useDark } from "@vueuse/core";
const isDark = useDark();
</script>

<style scoped>
    .footer::after {
        position: absolute;
        content: "";
        width: 100%;
        top: -30px;
        height: 1px;
        background: var(--vt-c-blue);
    }
    .footer-title {
        text-transform: uppercase;
    }
    .footer-title.dark {
        color: var(--vt-c-main);
    }
  .footer {
    display: flex;
    position: relative;
    align-items: center;
    margin-top: 120px;
    padding-bottom: 35px;
    justify-content: space-between;
  }
  .home-btn.dark {
    color: #F0F8FF;
  }
 .home-group {
    display: flex;
    gap: 13px;
    color: #13151C;
    flex-wrap: wrap;
  }
 .home-btn {
    padding: 13px 63px 13px 77px;
    border: 1px solid var(--vt-c-blue);
    background: none;
    cursor: pointer;
    position: relative;
    color: #13151C;
    text-decoration: none;
  }
  .mail::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(@/assets/img/Email.png) no-repeat center;
    left: 26%;
    top: 22%;
  }
  .teleg::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(@/assets/img/Telegramm.png) no-repeat center;
    left: 24%;
    top: 22%;
  }
  .linkd::after {
    position: absolute;
    content: "";
    width: 21px;
    height: 21px;
    background: url(@/assets/img/linked.svg) no-repeat center;
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
   @media(max-width: 1024px){
    .footer {
        margin-top: 60px;
        flex-direction: column;
        gap: 20px;
    }
    .home-group {
        justify-content: center;
        align-items: center;
    }
   }
</style>