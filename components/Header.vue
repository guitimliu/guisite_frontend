<script setup lang="ts">
import { ref } from 'vue';

interface MenuItem {
  name: string;
  url: string;
}

const menu:MenuItem[] = [
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

const showBreadMenu = ref(false);

function closeBreadMenu() {
  showBreadMenu.value = false;
}

function scrollTo(url) {
  const block = document.querySelector(`#${url}`);
  block?.scrollIntoView({ behavior: 'smooth' });
}

function backToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' });
}
</script>

<template>
  <div class="header">
    <h1 @click="backToTop" class="header__title">Gui Site</h1>
    <button @click="showBreadMenu = true;" type="button" class="header__breadMenu">
      <svg width="26" height="18" viewBox="0 0 26 18" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M0.25 0.5H25.75V3.35547H0.25V0.5ZM0.25 10.3945V7.60547H25.75V10.3945H0.25ZM0.25 17.5V14.6445H25.75V17.5H0.25Z" fill="#111111"/>
      </svg>
    </button>
    <ul class="header__mainMenu">
      <li v-for="item in menu" :key="item.name">
        <button type="button" class="header__mainMenu__item" @click="scrollTo(item.url)">
          {{ item.name }}
        </button>
      </li>
      <!-- <li>
        <a class="header__mainMenu__item" href="#">Contact</a>
      </li> -->
    </ul>
    <div class="header__background" />
  </div>
  <BreadMenu @closeBreadMenu="closeBreadMenu" v-show="showBreadMenu" />
</template>

<style lang="scss" scoped>
.header {
  position: fixed;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 90%;
  border-bottom: 2px solid #000;
  background-color: transparent;
  padding: 16px 0;
  margin: auto;
  z-index: 1;

  &__title {
    @include font-h1;

    color: #000;
    text-decoration: none;
    transition: letter-spacing .3s;
    cursor: pointer;
    
    &:hover {
      letter-spacing: 2px;
    }
  }

  &__breadMenu {
    background-color: transparent;
    border: none;
    cursor: pointer;

    @include desktop-up() {
      display: none;
    }
  }

  &__mainMenu {
    display: none;

    @include desktop-up() {
      display: flex;
      justify-content: flex-end;
      align-items: center;
      gap: 32px;

      &__item {
        @include font-h3;

        position: relative;
        color: #000;
        text-decoration: none;
        border: none;
        background-color: transparent;
        cursor: pointer;
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
  }

  &__background {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -2;
    width: 100%;
    height: 100%;
    background-color: #ffffff;
    opacity: 0.8;
  }
}
</style>
