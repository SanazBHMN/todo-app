<script setup>
import { defineProps } from "vue";
import Todo from "../components/Todo.vue";

const { todos } = defineProps(["todos"]);
</script>

<template>
  <Todo
    v-for="todo in todos"
    :key="todo.id"
    :id="todo.id"
    :text="todo.text"
    :isActive="todo.isActive"
  />
</template>
