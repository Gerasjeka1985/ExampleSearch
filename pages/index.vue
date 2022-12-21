<script setup lang="ts">
  import CustomSearch from "~/components/atoms/CustomSearch.vue";

  const {data: posts} = await useFetch('https://jsonplaceholder.typicode.com/posts');
</script>

<template>
  <div class="container">
    <custom-search></custom-search>
    <ol>
      <li class="container__item" v-for="item in posts" :key="item.id">
        <div>
          <h2>
            {{item.title}}
          </h2>
        </div>
        <div>
          <p>
            {{item.body}}
          </p>
        </div>
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