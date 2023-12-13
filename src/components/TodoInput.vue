<script setup>
import { ref, defineEmits } from "vue";

const newTodo = ref("");
const emit = defineEmits(["add-todo"]);

const addTodo = () => {
  if (newTodo.value.trim()) {
    emit("add-todo", newTodo.value);
    newTodo.value = "";
  }
};
</script>

<template>
  {{ newTodo }}
  <input
    v-model.trim="newTodo"
    @keyup.enter="addTodo"
    type="text"
    name="todo"
    id="todo"
    placeholder="Create a new todo..."
  />
</template>
