<template>

<div class="list__block">
  <div class="list__inner">
    <div class="list__item" v-for="twoot in twoots" :key="twoot.id">
      {{ twoot.title }}
    </div>
  </div>
</div>
  
</template>

<script>

export default  {
  name: 'ArticleList',
  data () {
    return {
      twoots: [
        {
          id: 1,
          content: "Matthijs is amazing",
          title: "Matthijs"
        },
        {
          id: 2,
          content: "This is my second twoot",
          title: "twotter"
        }
      ]
    }
  }

};
</script>

<style scoped>

</style>
