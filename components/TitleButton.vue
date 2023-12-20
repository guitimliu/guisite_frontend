<script setup lang="ts">
defineProps({
  title: {
    type: String,
    default: '標題',
  }
})
</script>

<template>
  <div class="titleButton">
    {{ title }}
  </div>
</template>

<style lang="scss" scoped>
.titleButton {
  display: inline-block;
  border: 1px solid #111111;
  border-radius: 12px;
  padding: 12px 20px;

  @include desktop-up() {
    transform: rotate(90deg);
  }
}
</style>
