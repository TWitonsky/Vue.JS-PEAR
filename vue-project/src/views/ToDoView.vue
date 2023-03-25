<script setup>
import { ref } from 'vue';
import { uid } from 'uid';
import ToDoCreater from '../components/ToDoCreater.vue';
import TodoItem from '../components/TodoItem.vue';


//This is the todoList from the toDoCreater Component. When clicked it will emit and be added to the array
const todoList = ref([]);

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: false,
    isEditing: null,
  });
};
</script>

<template>
  <main>
    <h1>Create To Do</h1>
    <ToDoCreater @create-todo="createTodo"/>
    <ul>
      <TodoItem v-for="todo in todoList"/>
    </ul>
  </main>
</template>


<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;
  h1 {
    margin-bottom: 16px;
    text-align: center;
  }
}
</style>