<script setup lang="ts">
  import {CustomPostsTypes} from "~/types/CustoPostsTypes";

  const props = defineProps<{
    posts: CustomPostsTypes[]
  }>();
</script>

<template>
  <ul class="posts">
    <li
        class="posts__item"
        v-if="posts.length > 1"
        v-for="item in posts"
        :key="item.id"
    >
      <h2>{{item.title}}</h2>
      <h4>{{item.body}}</h4>
    </li>
    <li
        v-else
        class="posts__item"
    >
      <h2>{{posts.title}}</h2>
      <h4>{{posts.body}}</h4>
    </li>
  </ul>
</template>

<style scoped lang="scss">
  .posts{

    &__item{
      background-color: #dcdc90;
      margin-bottom: 50px;
    }
  }
</style>

