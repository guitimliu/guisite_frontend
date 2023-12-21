<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Scrollbar } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/scrollbar';

defineProps({
  list: {
    type: Array,
    default: [],
  }
})
</script>

<template>
  <swiper class="workList" slides-per-view="auto" :space-between="50" :modules="[Scrollbar]" :scrollbar="{
    draggable: true,
  }">
    <swiper-slide class="workList__slide" v-for="item in list" :key="item.name">
      <div class="workList__item">
        <div class="workList__imageShowRange">
          <img class="workList__image" :src="item.image" :alt="item.name">
        </div>
        <h3 class="workList__name">{{ item.name }}</h3>
        <a v-if="item.url" :href="item.url" class="workList__url" :title="item.name" target="_blank">item.name</a>
      </div>
    </swiper-slide>
  </swiper>
</template>

<style lang="scss" scoped>
.workList {
  max-width: 100%;
  height: 280px;
  margin-bottom: 28px;

  @include desktop-up() {
    margin-bottom: 72px;
  }

  &__slide {
    width: 320px !important;
  }

  &__item {
    position: relative;
  }

  &__item:hover &__image {
    transform: scale(1.2);
  }

  &__imageShowRange {
    width: 100%;
    height: 200px;
    border-radius: 100px;
    overflow: hidden;
  }

  &__image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform .3s;
  }

  &__name {
    line-height: 1.5;
    text-align: center;
    margin-top: 16px;
  }

  &__url {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
  }
}

</style>

<style scoped>
.swiper-scrollbar {
  background: #11111110;
}

.swiper-scrollbar-drag {
  background: #111111;
}
</style>