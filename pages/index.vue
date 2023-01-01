<script setup lang="ts">
  import { ref } from "vue";
  import CustomSearch from "~/components/atoms/CustomSearch.vue";
  const runtimeConfig = useRuntimeConfig();
  const searchVal = ref('');
  const {data: posts,refresh,error, pending} = await useFetch(() => `${searchVal.value}`,{baseURL: runtimeConfig.apiBase});
</script>

<template>
  <div class="container">
    <custom-search v-model="searchVal"></custom-search>
    <div
        class="container__item"
        v-if="posts.length > 1"
        v-for="item in posts"
        :key="item.id"
    >
      <h2>{{item.title}}</h2>
      <h4>{{item.body}}</h4>
    </div>
    <div v-else>
      <h2>{{posts.title}}</h2>
      <h4>{{posts.body}}</h4>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .container{
    width: 100%;
    height: 100vh;

    &__item{
      margin-bottom: 50px;
    }
  }
</style>