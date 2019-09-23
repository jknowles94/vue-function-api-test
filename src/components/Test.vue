<template>
  <div>
    <h1>Child component</h1>
    <p>{{state.count}}</p>
  </div>
</template>
<script>
import {reactive} from '@vue/composition-api';
export default {
  props: ['count'],
  setup(props) {
    const state = reactive(props);

    return {
      state
    }
  },
  
}
</script>

