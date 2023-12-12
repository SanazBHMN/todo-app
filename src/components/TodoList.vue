<script setup>
import { defineProps } from "vue";
import Todo from "../components/Todo.vue";

const { data } = defineProps(["data"]);
</script>

<template>
  <Todo
    v-for="d in data"
    :key="d.id"
    :id="d.id"
    :text="d.text"
    :isActive="d.isActive"
  />
</template>
