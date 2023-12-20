<script setup lang="ts">
import messages from '@/public/langData.json';

const { tm, locale } = useI18n({
  messages,
});
</script>

<template>
  <div class="home">
    <p class="home__content">Hello World!</p>
  </div>
</template>

<style lang="scss" scoped>
  .home {
    &__content {
      font-size: 20px;
      line-height: 1.2;
    }
  }
</style>