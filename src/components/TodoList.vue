<script setup>
import { defineProps, defineEmits } from "vue";
import TodoItem from "../components/TodoItem.vue";

const { todos } = defineProps(["todos"]);
const emit = defineEmits(["remove-todo"]);
</script>

<template>
  <TodoItem
    v-for="todo in todos"
    :key="todo.id"
    :id="todo.id"
    :text="todo.text"
    :isActive="todo.isActive"
    @remove-todo="$emit('remove-todo', $event)"
  />
</template>
