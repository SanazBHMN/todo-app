<script setup>
import { ref } from "vue";
import Header from "./components/Header.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

import d from "./data/data.json";

const todos = ref(d);

const handleAddTodo = (newTodoText) => {
  const newTodo = {
    id: Date.now(),
    text: newTodoText,
    isActive: true,
  };
  todos.value.push(newTodo);
};
</script>

<template>
  <main class="container">
    {{ todos }}
    <Header />
    <TodoInput @add-todo="handleAddTodo" />
    <TodoList :todos="todos" />
  </main>
</template>

<style scoped></style>
