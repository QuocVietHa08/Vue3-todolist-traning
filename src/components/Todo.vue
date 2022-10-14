<script setup>
const props = defineProps({
  todo: {
    title: String,
    id: Number,
    status: String,
  },
});
</script>

<template>
  <div class="todo">
    <span>{{ props.todo.title}} </span>
    <!-- <span>{{ props.todo.index }}</span> -->
    <span class="deleteButton" @click="$emit('delete-todo', props.todo.index)"
      >Detele</span
    >
  </div>
</template>

<style scoped>
.todo {
  margin: 5px 0px;
  padding: 10px 10px;
  border: 1px solid lightblue;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
}

.deleteButton {
  padding: 0px 5px;
  background-color: red;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}
</style>
