<script setup>
import TodoList from "./components/TodoList.vue";
</script>

<template>
  <div class="todolist-container">
    <div class="todolist-wrapper">
      <h1>Todolist make by Vue</h1>
      <TodoList />
    </div>
  </div>
</template>

<style scoped>
.todolist-container {
  width: 30vw;
  height: 70vh;
}

.todolist-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  /* width: 100vw; */
  /* margin: auto; */
  /* background-color: red; */
}
</style>
