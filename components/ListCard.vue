<script setup lang="ts">
defineProps({
  title: {
    type: String,
    default: '',
  },
  list: {
    type: Array,
    default: [],
  }
})
</script>

<template>
  <div class="listCard">
    <h2 class="listCard__title">
      {{ title }}
    </h2>
    <ul>
      <li v-for="(item, key) in list" :key="'skill'+key" class="listCard__item">
        <div class="listCard__item__field">
          <svg class="listCard__item__icon" width="26" height="20" viewBox="0 0 28 16" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M14 21L5.75 26L7.9375 16.625L0.6875 10.3125L10.25 9.5L14 0.6875L17.75 9.5L27.3125 10.3125L20.0625 16.625L22.25 26L14 21Z" fill="#111111"/>
          </svg>
          <p class="listCard__item__text">
            {{ item }}
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.listCard {
  &__title {
    @include font-h2;
    margin-bottom: 32px;
  }

  &__item {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 8px;

    &__field {
      display: flex;
      gap: 4px;
      line-height: 1.5;
    }
    
    &__icon {
      min-width: 16px;
      max-width: 16px;
      min-height: 16px;
      max-width: 16px;
      margin-top: -2px;
    }

    &::after {
      content: '';
      width: 100%;
      height: 1px;
      background-color: #111111;
      margin-top: 16px;
      margin-bottom: 16px;
      margin-left: 20px;
    }
  }
}
</style>
