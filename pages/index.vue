<script setup lang="ts">
  import { ref } from "vue";
  import CustomSearch from "~/components/atoms/CustomSearch.vue";
  import CustomPost from "~/components/atoms/CustomPost.vue";

  const runtimeConfig = useRuntimeConfig();
  const searchVal = ref('');
  const {data: posts,refresh,error, pending} = await useFetch(() => `${searchVal.value}`,{baseURL: runtimeConfig.apiBase});
</script>

<template>
  <div class="container">
    <custom-search v-model="searchVal"></custom-search>
    <custom-post :posts="posts"></custom-post>
  </div>
</template>

<style scoped lang="scss">
  .container{
    width: 100%;
    height: 100vh;
  }
</style>