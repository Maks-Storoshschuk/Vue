<template>
  <!--  <h1>test component. {{ text }}</h1>-->
  <!--  <button @click="logger"> log </button>-->
  <h3 v-for="item of items" :key="item.id">{{ item.text }}
    <button @click="removeItem(item.id)">remove</button>
  </h3>
</template>

<script>
export default {
  name: "Test",
  // props:['text']
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  methods: {
    logger() {
      console.log(this.text)
    },
    removeItem(id) {
      this.$emit('removeItem', id)
      // this.items = this.items.filter(item => item.id !== id)
    }
  },
  emits:['removeItem']
}
</script>

<style scoped>

</style>
