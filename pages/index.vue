<script setup lang="ts">
  import { ref } from "vue";
  import CustomSearch from "~/components/atoms/CustomSearch.vue";
  import CustomPost from "~/components/atoms/CustomPost.vue";

  const runtimeConfig = useRuntimeConfig();
  const searchVal = ref('');
  const {data: posts,refresh,error, pending} = await useFetch(() => `${searchVal.value}`,{baseURL: runtimeConfig.apiBase});
  const {data: comments} = await useFetch(() => `${searchVal.value}/comments`,{baseURL: runtimeConfig.apiBase});
</script>

<template>
  <div class="container">
    <custom-search v-model="searchVal"></custom-search>
    <custom-post :posts="posts"></custom-post>
    <div class="container__comments">
      <h2>Комментарии</h2>
      <ul>
        <li v-for="comment in comments" style="margin: 20px">
          {{comment.body}}
          <br />
          {{comment.email}}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .container{
    width: 100%;
    height: 100vh;

    &__comments{
      background-color: yellow;
    }
  }
</style>