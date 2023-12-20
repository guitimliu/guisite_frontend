<script setup lang="ts">
defineProps({
  data: {
    type: Object,
    default: {},
  }
})

const isSafari = ref(false);

onMounted(() => {
  isSafari.value = getIsSafari();
})

function getIsSafari() {
  const ua = navigator.userAgent.toLocaleLowerCase();
  return (ua.indexOf('safari') != -1) ? (ua.indexOf('chrome') == -1) : false;
}
</script>

<template>
  <div class="blogCard">
    <img v-if="!isSafari" class="blogCard__image" :src="data.image" :alt="data.title">
    <h2 class="blogCard__title">{{ data.title }}</h2>
    <p class="blogCard__desc">{{ data.desc }}</p>
    <a class="blogCard__url" :href="data.url" :title="data.title" target="_blank">{{ data.title }}</a>
  </div>
</template>

<style lang="scss" scoped>
.blogCard {
  position: relative;

  &__image, &__title {
    margin-bottom: 16px;
  }

  &__image {
    width: 100%;
    max-width: 100%;
    border-radius: 12px;
    object-fit: cover;
    aspect-ratio: 2 / 1;
  }

  &__title {
    @include font_h4;
  }

  &__desc {
    @include font-base;
    color: #11111180;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    max-height: 2 * 16 * 1.5;
  }

  &__url {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
  }
}
</style>
