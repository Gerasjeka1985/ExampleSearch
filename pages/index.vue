<script setup lang="ts">
  import { ref } from "vue";
  import CustomSearch from "~/components/atoms/CustomSearch.vue";
  const runtimeConfig = useRuntimeConfig();
  const searchVal = ref('');
  const {data: posts,refresh,error, pending} = await useFetch(() => `${searchVal.value}`,{baseURL: runtimeConfig.apiBase});

  const handler = () => {
    refresh()
  }
</script>

<template>
  <div class="container">
    <custom-search v-model="searchVal">
      <button
          @click.prevent="handler"
      >
        Обновить
      </button>
    </custom-search>
    <ol>
      <li class="container__item" v-for="item in posts" :key="item.id">
          {{item}}
      </li>
    </ol>
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