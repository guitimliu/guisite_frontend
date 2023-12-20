<script setup lang="ts">
defineProps({
  list: {
    type: Array,
    default: [],
  }
})
</script>

<template>
  <div class="blogCardList">
    <BlogCard
      v-for="item in list"
      :key="item.title"
      class="blogCardList__item"
      :data="item"
    />
  </div>
</template>

<style lang="scss" scoped>
.blogCardList {
  max-width: 100%;
  
  @include desktop-up() {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }

  &__item {
    margin-bottom: 40px;

    @include desktop-up() {
      width: 48%;
      transition: transform .3s;

      &:hover {
        transform: scale(1.05);
      }

      &:nth-child(even) {
        transform: translateY(75px);

        &:hover {
          transform: translateY(75px) scale(1.05);
        }
      }
    }
  }
}
</style>
