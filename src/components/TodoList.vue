<script setup>
import Todo from "./Todo.vue";
import { ref } from "vue";

const todos = ref([]);
const inputRef = ref("");
function handleOnChangeInput(event) {
  inputRef.value = event.target.value;
}

function addTodo() {
  const newTodo = {
    status: "create",
    title: inputRef.value,
  };
  todos.value.push(newTodo);
  inputRef.value = "";
}

function deleteTodo(todoIndex) {
  const cloneTodo = todos.value.filter((_, index) => index !== todoIndex);
  todos.value = cloneTodo;
}

function editTodo(todoIndex) {
  const cloneTodo = [...todos.value];
  cloneTodo[todoIndex] = { ...cloneTodo[todoIndex], status: "edit" };
  todos.value = cloneTodo;
}

function changeTodo(todoIndex, changeValue) {
  const cloneTodo = [...todos.value];
  cloneTodo[todoIndex] = {
    ...cloneTodo[todoIndex],
    status: "create",
    title: changeValue,
  };
  todos.value = cloneTodo;
}
</script>

<template>
  <div class="todo-input">
    <input
      class="input"
      :value="inputRef"
      @input="handleOnChangeInput"
      placeholder="Enter your todo"
    />
    <button class="button" @click="addTodo">Add</button>
  </div>
  <div class="todo-wrapper" v-for="(todo, index) in todos" :key="todo">
    <Todo
      :todo="{ id: index, ...todo }"
      @edit-todo="editTodo"
      @delete-todo="deleteTodo"
      @change-todo="changeTodo"
    />
  </div>
</template>

<style scoped>
.input {
  height: 30px;
  width: 100%;
  border-radius: 5px;
  border: 1px solid lightblue;
  outline: none;
  text-indent: 10px;
}

.todo-input {
  /* margin: 10px auto; */
  height: 50%;
  display: flex;
  gap: 10px;
  width: 100%;
}

.button {
  background-color: lightblue;
  color: white;
  border: 1px solid lightblue;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}

.todo-wrapper {
  width: 100%;
}
</style>
