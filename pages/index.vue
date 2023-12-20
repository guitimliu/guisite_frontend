<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { useFetch } from '#app';
import AOS from 'aos';
import 'aos/dist/aos.css';

import messages from '@/public/langData.json';

const homeBlock = ref(null);

onMounted(() => {
  AOS.init();
})
const { tm, locale } = useI18n({
  messages,
});

interface BlogItem {
  title: string,
  image: string,
  desc: string,
  url: string,
}

const blogData: Ref<BlogItem[]> = ref([]);

async function getBlogData() {
  try {
    const { data, error } = await useFetch('https://guiblogs.com/api/posts.json');
    blogData.value = data.value;
  } catch (e) {
    console.log(e);
  }
}
getBlogData();
</script>

<template>
  <div class="home">
    <p class="home__content">Hello World!</p>
    <div ref="homeBlock" class="home__block">
      <div class="home__container">
        <div id="blog" class="home__block__layout" data-aos="fade-up" data-aos-duration="800">
          <TitleButton title="Blog" />
          <BlogCardList :list="blogData" class="home__blog" />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .home {
    &__container {
      width: 90%;
      margin: auto;
    }

    &__block {
      position: relative;
      z-index: 3;
      background-color: #111111;
      padding: 72px 0 36px;
      margin-bottom: 36px;
      transition: background-color .8s;

      &__layout {
        display: flex;
        flex-direction: column;
        align-items: start;
        gap: 24px;
        width: 1100px;
        max-width: 100%;
        margin: auto;

        @include desktop-up() {
          flex-direction: row;
          justify-content: space-between;
          gap: 72px;
        }
      }
    }

    &__blog {
      @include desktop-up() {
        margin-bottom: 100px;
      }
    }
  }
</style>