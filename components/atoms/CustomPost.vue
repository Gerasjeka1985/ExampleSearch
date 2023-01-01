<script setup lang="ts">
  import {CustomPostsTypes} from "~/types/CustoPostsTypes";
  import {ref} from "vue";
  const val = ref('')

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
      <h3>
        <strong>Название поста : </strong>
        <br />
          <span style="color: blue">{{item.title}}</span>
      </h3>
      <h4>
        <strong>Описание поста</strong>
        <br />
        <span>{{item.body}}</span>
      </h4>
    </li>
    <li
        v-else
        class="posts__item"
    >
      <h3>
        <strong>Название поста : </strong>
        <br />
        <span style="color: blue">{{posts.title}}</span>
      </h3>
      <h4>
        <strong>Описание поста</strong>
        <br />
        <span>{{posts.body}}</span>
      </h4>
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

