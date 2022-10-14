<script setup>
import TodoList from "./components/TodoList.vue";
</script>

<template>
  <div class="todolist-wrapper">
    <TodoList />
  </div>
</template>

<style scoped>
.todolist-wrapper {
  transform: translateX(40%);
  width: 150%;
  margin: auto;
}
</style>
