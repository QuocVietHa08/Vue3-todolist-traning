<script setup>
import { ref, watch } from "vue";
const inputRef = ref("");
const props = defineProps({
  todo: {
    title: String,
    id: Number,
    status: String,
  },
});

function handleOnChangeInput(event) {
  inputRef.value = event.target.value;
}

watch(() => (inputRef.value = props.todo.title));
</script>
<template>
  <div class="todo">
    <span v-if="props.todo.status === 'create'">{{ props.todo.title }} </span>
    <span v-if="props.todo.status === 'edit'">
      <input :value="inputRef" @input="handleOnChangeInput" />
    </span>
    <div class="buttonWrapper">
      <span
        v-if="props.todo.status === 'create'"
        class="editButton"
        @click="$emit('edit-todo', props.todo.id)"
        >Edit</span
      >
      <span
        v-if="props.todo.status === 'edit'"
        class="editButton"
        @click="$emit('change-todo', props.todo.id, inputRef.valueOf())"
        >Done</span
      >
      <span class="deleteButton" @click="$emit('delete-todo', props.todo.id)"
        >Detele</span
      >
    </div>
  </div>
</template>

<style scoped>
.todo {
  width: 100%;
  margin: 15px 0px;
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

.editButton {
  background-color: lightgreen;
  color: white;
  border-radius: 5px;
  padding: 0px 5px;
  cursor: pointer;
}

.buttonWrapper {
  display: flex;
  gap: 10px;
}
</style>
