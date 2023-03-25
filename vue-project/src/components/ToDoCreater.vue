<script setup>
import { ref, reactive, defineEmits } from 'vue';

//emit can trigger events and pass data up the component heirarchy.
const emit = defineEmits(["create-todo"]);

//Two ways to have reactive data
//Ref
//const todo = ref("");
//console.log(todo);
//console.log(todo.value);

// //Reactice state (seems more like state in react)
const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: null,
});
// console.log(todoState); >"Testing"

//Creating the function that happens on click of create button
const createTodo = () => {
  todoState.invalid = null;
  if(todoState.todo !== ""){
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMsg = "Todo value can not be empty";
  
 
}
</script>

<template>
  <!--Adding a class binding so the UI changes if error or whatever you set to trigger it-->
  <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
    <input type="text" v-model="todoState.todo"/>
    <!-- @ is shorthand for v-on: then in script what it does.-->
    <button @click="createTodo()">Create</button>
  </div>
  <!-- <p v-if="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p>-->
  <p v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p> 
  <!--While v-if will stop something being rendered if the expression within it returns false has a higher toggle cost, 
      v-show will still render the element - but it will apply display: none to the element.
      If toggled often go v-show, if not v-if-->
</template>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;
  &.input-err {
    border-color: red;
  }
  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }
  input {
    width: 100%;
    padding: 8px 6px;
    border: none;
    &:focus {
      outline: none;
    }
  }
  button {
    padding: 8px 16px;
    border: none;
  }
}
.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}
</style>