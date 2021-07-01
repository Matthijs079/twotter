<template>

<div class="list__block">
  <div class="list__inner">
    <TwootItem v-for="twoot in object_list" :key="twoot.id" :twoot="twoot" @favourite="toggleFavourite"/>
  </div>
</div>
  
</template>

<script>

import TwootItem from './TwootItem.vue';

export default  {
  name: 'ArticleList',
  props: ["object_list"],
  components: {
    TwootItem
  },
  methods: {
    toggleFavourite(id) {
      console.log(`favourite twoot #${id}`)
    }
  }

};
</script>

<style scoped>

</style>
