<script setup lang="ts">
import { useI18n } from 'vue-i18n';

const { tm, locale } = useI18n();

const title:string = 'Gui Site';

const peopleNum:number = 11920;

interface LangItem {
  name: string;
  slug: string;
}

const langMenu:LangItem[] = [
  {
    name: '中文',
    slug: 'zh-hant',
  },
  {
    name: 'English',
    slug: 'en',
  },
]

interface MenuItem {
  name: string;
  url: string;
}

const FooterMenu:MenuItem[] = [
  {
    name: 'Blog',
    url: 'https://guiblogs.com/',
  },
  {
    name: 'Behance',
    url: 'https://www.behance.net/1a4b8b89/projects',
  },
  {
    name: 'GitHub',
    url: 'https://github.com/guitimliu',
  },
  {
    name: 'Linkedin',
    url: 'https://www.linkedin.com/in/%E6%A1%82%E5%BB%B7-%E5%8A%89-0167641ab/',
  },
  {
    name: 'Cakeresume',
    url: 'https://www.cakeresume.com/s--sI2HcyKiJPFCPtv8Zrk9mw--/guitimliu',
  },
  {
    name: 'Linktr',
    url: 'https://linktr.ee/guitimliu',
  },
]

const copyright:string = '© 2023 Gui. All rights reserved.';
</script>

<template>
  <div class="footer">
    <div class="footer__top">
      <a href="/" class="footer__title">{{ title }}</a>
      <!-- <p class="footer__peopleNum">
        <span class="footer__peopleNum__count">
          {{ peopleNum }}
        </span>
        次瀏覽
      </p> -->
      <ul class="footer__langList">
        <li v-for="item in langMenu" :key="item.name">
          <button class="footer__langList__item" type="button" @click="$i18n.locale = item.slug">{{ item.name }}</button>
        </li>
      </ul>
    </div>
    <div class="footer__bottom">
      <ul class="footer__menu">
        <li v-for="item in FooterMenu" :key="item.name">
          <a class="footer__menu__item" :href="item.url" :title="item.name" target="_blank">{{ item.name }}</a>
        </li>
      </ul>
      <p class="footer__copyright">
        {{ copyright }}
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.footer {
  width: 90%;
  margin: auto;
  text-align: center;
  z-index: 3;

  &__top {
    margin-bottom: 16px;

    @include desktop-up() {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding-bottom: 16px;
      border-bottom: 2px solid #111111;
    }
  }

  &__title {
    @include font_h3;

    display: block;
    color: #111;
    text-decoration: none;
    transition: letter-spacing .3s;
    margin-bottom: 16px;
    
    &:hover {
      letter-spacing: 2px;
    }

    @include desktop-up() {
      margin-bottom: 0;
    }
  }

  &__peopleNum {
    @include font_h6;
    color: #1111114D;
    border-bottom: 2px solid #111111;
    padding-bottom: 16px;
    margin-bottom: 16px;

    @include desktop-up() {
      border: none;
      padding-bottom: 0;
      margin-bottom: 0;
    }

    &__count {
      color: #111111;
    }
  }

  &__langList {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 40px;
    border-bottom: 2px solid #111111;
    padding-bottom: 16px;

    @include desktop-up() {
      border: none;
      padding-bottom: 0;
    }

    &__item {
      position: relative;
      border: none;
      background-color: transparent;
      cursor: pointer;
      padding: 2px;
      transition: color .3s;

      &:after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 0;
        height: 100%;
        z-index: -1;
        background-color: #111;
        transition: width .3s;
      }

      &:hover {
        color: #ffffff;
      }

      &:hover:after {
        width: 100%;
      }
    }
  }

  &__menu {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 16px;
    margin-bottom: 24px;

    &__item {
      @include font_h6;

      position: relative;
      text-decoration: none;
      color: #111111;
      padding: 2px;
      transition: color .3s;

      &:after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 0;
        height: 100%;
        z-index: -1;
        background-color: #111;
        transition: width .3s;
      }

      &:hover {
        color: #ffffff;
      }

      &:hover:after {
        width: 100%;
      }
    }
  }

  &__copyright {
    @include font_h6;
    color: #111111;
    margin-bottom: 28px;
  }

  @include desktop-up() {
    &__bottom {
      display: flex;
      flex-direction: row-reverse;
      justify-content: space-between;
    }   
  }
}
</style>