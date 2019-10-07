<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Todo list</h1>
    <input v-model="newListItem"/>
    <button @click="addTask()">Add Task</button>
    <div class="todo-container">
      <h2 v-if="todoList.length <= 0">No Items!</h2>
      <ToDoListItem v-for="item in todoList" :key="item.id" :id="item.id" :task="item.task" :deleteTask="deleteTaskItem"></ToDoListItem>
    </div>
  </div>
</template>

<script>
// import { reactive, toRefs} from '@vue/composition-api';
import {ref, reactive} from '@vue/composition-api';
import ToDoListItem from './components/ToDoListItem.vue';
export default {
  components: {
    ToDoListItem
  },
  setup() {
    const todoList = reactive([]);
    let newListItem = ref('');

    function addTask() {
      todoList.push({
        id: todoList.length + 1,
        task: newListItem.value
      });
      newListItem.value = '';
    }

    function deleteTaskItem(id) {
      let index = todoList.findIndex((el) => {
        return el.id === id;
      });

      if(index === -1) return;

      todoList.splice(index, 1);
    }

    return {
      newListItem,
      todoList,
      addTask,
      deleteTaskItem
    }

    // COULD ALSO BE WRITTEN LIKE 
    // const state = reactive({
    //   todoList: [],
    //   newListItem: ''
    // });

    // function addTask() {
    //   state.todoList.push({
    //     id: state.todoList.length + 1,
    //     task: state.newListItem
    //   });
    //   state.newListItem = '';      
    // }

    // return {
    //   ...toRefs(state),
    //   addTask
    // }
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

.todo-container {
  border: 1px solid;
  margin-top: 30px;
}
</style>
