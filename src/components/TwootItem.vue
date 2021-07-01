<template>
  <div class="list__item" @click="favouriteTwoot(twoot.id)">
    {{ twoot.title }}
  </div>
</template>

<script>
export default {
  name: "TwootItem",
  props: {
    twoot: {
      type: Object,
      required: true
    }
  },
  methods: {
    favouriteTwoot(id) {
      this.$emit('favourite', id)
    }
  }
}
</script>
