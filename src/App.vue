<script setup>
import Header from "./components/Header.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

import data from "./data/data.json";
</script>

<template>
  <main class="container">
    <Header />
    <TodoInput />
    <TodoList :data="data" />
  </main>
</template>

<style scoped></style>
