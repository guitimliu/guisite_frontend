<script setup lang="ts">
const emit = defineEmits(['closeBreadMenu']);

interface MenuItem {
  name: string;
  url: string;
}

const mainMenu:MenuItem[] = [
  {
    name: 'Works',
    url: 'works',
  },
  {
    name: 'Blog',
    url: 'blog',
  },
  {
    name: 'Tools',
    url: 'tools',
  },
];

const footerMenu:MenuItem[] = [
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
];

function scrollTo(url) {
  const block = document.querySelector(`#${url}`);
  block?.scrollIntoView({ behavior: 'smooth' });
  emit('closeBreadMenu');
}
</script>

<template>
  <div class="breadMenu">
    <div class="breadMenu__header">
      <nuxt-link class="breadMenu__header__title" to="/" title="Gui Site">
        Gui Site
      </nuxt-link>
      <button @click="$emit('closeBreadMenu')" class="breadMenu__header__closeButton" type="button">
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M19.8945 2.09766L11.9922 10L19.8945 17.9023L17.9023 19.8945L10 11.9922L2.09766 19.8945L0.105469 17.9023L8.00781 10L0.105469 2.09766L2.09766 0.105469L10 8.00781L17.9023 0.105469L19.8945 2.09766Z" fill="white"/>
        </svg>
      </button>
    </div>
    <ul class="breadMenu__list">
      <li v-for="item in mainMenu" :key="item.name" @click="scrollTo(item.url)">
        <button type="button" class="breadMenu__list__item">
          {{ item.name }}
        </button>
      </li>
      <!-- <li>
        <nuxt-link class="breadMenu__list__item" to="/contact" title="Contact">Contact</nuxt-link>
      </li> -->
    </ul>
    <ul class="breadMenu__footer">
      <li v-for="item in footerMenu" :key="item.name">
        <a class="breadMenu__footer__item" :href="item.url" :title="item.name" target="_blank">
          {{ item.name }}
        </a>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.breadMenu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: 10;
  background-color: #000;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  @include desktop-up() {
    display: none;
  }

  &__header, &__list, &__footer {
    width: 90%;
    margin: 0 auto;
  }

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid #fff;
    padding: 16px 0;

    &__title {
      @include font-h1;

      color: #fff;
      text-decoration: none;
    }

    &__closeButton {
      border: none;
      background-color: transparent;
      cursor: pointer;
    }
  }

  &__list {
    display: flex;
    flex-direction: column;
    gap: 48px;
    text-align: center;

    &__item {
      @include font-h1;

      color: #fff;
      text-decoration: none;
      border: none;
      background-color: transparent;
      cursor: pointer;
    }
  }

  &__footer {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 48px;
    border-top: 2px solid #fff;
    padding: 20px 2%;

    &__item {
      @include font-h6;

      color: #fff;
      text-decoration: none;
    }
  }
}
</style>
