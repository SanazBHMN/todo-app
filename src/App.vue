<script setup>
import { ref, computed, reactive } from "vue";
import Header from "./components/Header.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

import d from "./data/data.json";

const todos = ref(d);
const displayedTodos = reactive({
  items: [...todos.value],
});

const handleAddTodo = (newTodoText) => {
  const newTodo = {
    id: Date.now(),
    text: newTodoText,
    isActive: true,
  };
  todos.value.push(newTodo);
};

const handleRemoveTodo = (todoId) => {
  todos.value = todos.value.filter((todo) => todo.id !== todoId);
};

const showAllTodos = () => {
  displayedTodos.items = [...todos.value];
};

const showActiveTodos = () => {
  displayedTodos.items = todos.value.filter((todo) => todo.isActive);
};

const showCompletedTodos = () => {
  displayedTodos.items = todos.value.filter((todo) => todo.completed);
};

const activeTodos = computed(() => todos.value.filter((todo) => todo.isActive));
</script>

<template>
  <main class="container">
    <Header />
    <TodoInput @add-todo="handleAddTodo" />
    <TodoList :todos="displayedTodos.items" @remove-todo="handleRemoveTodo" />
    <div>
      <small>{{ activeTodos.length }} items left</small>
      <button @click="showAllTodos">All</button>
      <button @click="showActiveTodos">Active</button>
      <button @click="showCompletedTodos">Completed</button>
    </div>
  </main>
</template>

<style scoped></style>
