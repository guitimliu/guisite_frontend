<script setup lang="ts">
defineProps({
  data: {
    type: Object,
    default: {},
  }
})

const backgroundColor = ref([
  {
    one: '#FFAD31',
    two: '#FFD439',
  },
  {
    one: '#F0FF3F',
    two: '#00FFC2',
  },
  {
    one: '#FF3FE0',
    two: '#00B2FF',
  },
  {
    one: '#07D0FF',
    two: '#06FFED',
  },
]);
</script>

<template>
  <div class="toolCard">
    <svg class="toolCard__background" width="427" height="256" viewBox="0 0 427 256" fill="none" xmlns="http://www.w3.org/2000/svg">
      <g :filter="`url(#filter0_f_2652_1077_${data.index})`">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M86.8504 -45.8524C124.198 -45.2736 164.362 -47.3068 190.465 -28.014C219.301 -6.7014 236.136 25.9425 221.783 53.8757C208.543 79.6451 162.558 81.7958 128.066 93.4294C94.4939 104.752 63.5467 127.831 28.5443 119.051C-9.08672 109.612 -27.4598 79.9743 -36.9421 52.0399C-46.6549 23.4264 -50.0102 -9.55788 -22.4971 -31.3146C3.79337 -52.1046 47.8666 -46.4566 86.8504 -45.8524Z" :fill="`url(#paint0_linear_2652_1077_${data.index})`"/>
      </g>
      <defs>
      <filter :id="`filter0_f_2652_1077_${data.index}`" x="-244" y="-247" width="671" height="568" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
      <feFlood flood-opacity="0" result="BackgroundImageFix"/>
      <feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
        <feGaussianBlur stdDeviation="100" result="effect1_foregroundBlur_2652_1077"/>
      </filter>
      <linearGradient :id="`paint0_linear_2652_1077_${data.index}`" x1="92" y1="-15.5" x2="91.237" y2="120.999" gradientUnits="userSpaceOnUse">
      <stop :stop-color="backgroundColor[data.index].one"/>
      <stop offset="1" :stop-color="backgroundColor[data.index].two"/>
      </linearGradient>
      </defs>
    </svg>
    <div class="toolCard__top">
      <h2 class="toolCard__title">
        {{ data.title }}
      </h2>
      <span class="toolCard__index">
        0{{ data.index + 1 }}
      </span>
    </div>
    <div class="toolCard__bottom">
      <p class="toolCard__desc">
        {{ data.desc }}
      </p>
      <button type="button" class="toolCard__button">
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M10 0.648438L19.3516 10L10 19.3516L8.35938 17.7109L14.8672 11.1484H0.648438V8.85156H14.8672L8.35938 2.28906L10 0.648438Z" fill="#111111"/>
        </svg>
      </button>
    </div>
    <a :href="data.url" class="toolCard__link" :title="data.title" target="_blank">
      {{ data.title }}
    </a>
  </div>
</template>

<style lang="scss" scoped>
.toolCard {
  width: 100%;
  height: 208px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: relative;
  border: 2px solid #111111;
  border-radius: 16px;
  padding-top: 24px;
  overflow: hidden;

  &__background {
    position: absolute;
    top: -47px;
    left: -44px;
    width: 271px;
    height: 168px;
  }

  &__top, &__bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 16px;
    padding-right: 16px;
  }

  &__top {
    border-bottom: 2px solid #000000;
    padding-bottom: 16px;
  }

  &__bottom {
    padding-top: 24px;
    padding-bottom: 24px;
    transition: background-color .3s;
  }

  &:hover &__bottom {
    position: relative;
    background-color: #111111;
  }

  &:hover &__bottom::after {
    content: 'Try!';
    position: absolute;
    top: 50%;
    left: 16px;
    transform: translateY(-50%);
    color: #ffffff;
  }

  &:hover &__button {
    border: none;
    background-color: #ffffff;
  }

  &__title, &__index {
    @include font-h4;
  }

  &__desc {
    color: #11111180;
    line-height: 1.5;
  }

  &__button {
    width: 52px;
    height: 52px;
    border: 1px solid #111111;
    border-radius: 50%;
    background-color: transparent;
  }

  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
  }
}
</style>
