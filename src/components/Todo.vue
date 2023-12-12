<script setup>
import { defineProps } from "vue";

const { id, text, isActive } = defineProps(["id", "text", "isActive"]);
</script>

<template>
  <div>
    <input type="checkbox" name="todo" :id="`${id}`" />
    <label :for="`${id}`">{{ text }}</label>
  </div>
</template>
