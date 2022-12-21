<script setup lang="ts">
import {ref} from 'vue';

const searchValue = ref("");

const handler = (val: any) => {
  console.log(val);
}
</script>

<template>
  <form class="search">
    <input
        class="search__ipt"
        type="search"
        placeholder="введите название альбома"
        v-model="searchValue"
    />
    <button
        class="search_btn"
        @click.prevent="handler(searchValue)"
    >
      Сортировать
    </button>
  </form>
</template>

