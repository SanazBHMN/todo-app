<script setup>
import { defineProps, defineEmits } from "vue";

const { id, text, isActive } = defineProps(["id", "text", "isActive"]);

const emit = defineEmits(["remove-todo"]);

const removeTodo = () => {
  emit("remove-todo", id);
};
</script>

<template>
  <div>
    <input type="checkbox" name="todo" :id="`${id}`" />
    <label :for="`${id}`">{{ text }}</label>
    <button @click="removeTodo">Delete</button>
  </div>
</template>
