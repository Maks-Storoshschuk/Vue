<template>
  <button @click="isVisible = !isVisible">toggle list visibility({{ isVisible }})</button>
  <Test v-if="isVisible" :items="items" @removeItem="removeItemFromList"/>
  <h1 v-else-if="!isVisible && counter === 0">some strange things</h1>
  <h1 v-else>List is hidden</h1>
  <img alt="Vue logo" src="./assets/logo.png">
  <!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->

  <h1 v-show="isVisible">{{ user.name }}</h1>
  <div>counter value: {{ counter }}</div>
  <button v-on:click="incCounter">increment</button>
  <!--  <button v-on:click="()=>decCounter(35)">decrement</button>-->
  <button v-on:click="decCounter(35, $event)">decrement</button>

  <!--  <h3>{{ items[0].text }}-->
  <!--    <button @click="removeItem(items[0].id)">remove</button>-->
  <!--  </h3>-->
  <!--  <h3>{{ items[1].text }}-->
  <!--    <button @click="removeItem(items[1].id)">remove</button>-->
  <!--  </h3>-->
  <!--  <h3>{{ items[2].text }}-->
  <!--    <button @click="removeItem(items[2].id)">remove</button>-->
  <!--  </h3>-->


</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Test from "@/components/Test";

export default {
  name: 'App',
  data() {
    return {
      items: [
        {id: 1, text: 'text1'},
        {id: 2, text: 'text2'},
        {id: 3, text: 'text3'},
      ],
      counter: 0,
      userName: 'Maks',
      user: {
        name: 'Peter'
      },
      isVisible: true
    }
  },
  methods: {
    incCounter() {
      this.counter++

      this.user.name += ' ?'
    },
    decCounter(...args) {
      this.counter--
      console.log(args)
    },
    removeItemFromList(id) {
      this.$emit('removeItem', id)
      this.items = this.items.filter(item => item.id !== id)
    }
  },
  components: {
    // HelloWorld,
    Test
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
