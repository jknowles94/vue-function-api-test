<template>
  <div>
    <h1>Child component</h1>
    <p>{{test}}</p>
  </div>
</template>
<script>
import { value, watch } from 'vue-function-api';
export default {
  props: ['count'],
  setup(props) {
    const test = value(props.count);
    watch(() => props.count, (count) => {
      test.value = count;
    });
    return {
      test
    }
  },
  
}
</script>

