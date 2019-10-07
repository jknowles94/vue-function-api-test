<template>
  <div class="item">
    {{task}}
    <button @click="deleteTask(id)">Delete</button>
  </div>
</template>
  
<script>
// import {ref} from '@vue/composition-api';
export default {
  props: {
    task: String,
    deleteTask: Function,
    id: Number
  }
}
</script>

<style scoped>
  .item {
    padding: 25px;
  }
</style>