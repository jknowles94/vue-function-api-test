<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>{{count}}</h1>
    <h1>Computed: {{computedCount}}</h1>
    <Test :count="count"></Test>
    <button @click="increment">Plus 1</button>
  </div>
</template>

<script>
import {ref, computed} from '@vue/composition-api';
import Test from './components/Test.vue';
export default {
  components: {
    Test
  },
  setup() {
    const count = ref(0);
    const increment = () => {
      count.value++;
    };
    const computedCount = computed(() => count.value * 2);

    return {
      count,
      computedCount,
      increment
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
