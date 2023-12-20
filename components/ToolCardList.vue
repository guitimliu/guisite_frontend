<script setup lang="ts">
defineProps({
  list: {
    type: Array,
    default: {},
  }
})
</script>

<template>
  <div class="toolCardList">
    <ToolCard
      v-for="item in list" :key="item.index"
      class="toolCardList__item"
      :data="item"
    />
  </div>
</template>

<style lang="scss" scoped>
.toolCardList {
  width: 100%;

  @include desktop-up() {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }

  &__item {
    margin-bottom: 40px;

    @include desktop-up() {
      width: 45%;
    }
  }
}
</style>
