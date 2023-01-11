<script setup>
import { ref } from "vue";

const inputValue = ref("");

const emit = defineEmits(["add-todo"]);

const addTodo = () => {
  emit("add-todo", inputValue.value);
  inputValue.value = "";
};
</script>

<template>
  <div>
    <input
      type="text"
      placeholder="Add todo..."
      v-model="inputValue"
      @keyup.enter="addTodo"
    />
    <button @click="addTodo">Add</button>
  </div>
</template>
