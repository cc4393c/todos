<script setup>
import { ref } from "vue";
import TodoForm from "./TodoForm.vue";
import TodoItem from "./TodoItem.vue";

const items = ref([
  {
    id: 1,
    content: "Do homework",
    completed: false,
  },
  {
    id: 2,
    content: "Do chores",
    completed: false,
  },
  {
    id: 3,
    content: "Cook dinner",
    completed: false,
  },
]);

const addTodo = (value) => {
  if (value) {
    items.value.push({
      id: new Date().getTime(),
      content: value,
      completed: false,
    });
  }
};

const removeTodo = (id) => {
  items.value = items.value.filter((item) => item.id !== id);
};

const changeCompleted = (id) => {
  items.value = items.value.map((item) => {
    if (item.id === id) {
      item.completed = !item.completed;
    }
    return item;
  });
};
</script>

<template>
  <div>
    <h1>Todos</h1>
    <TodoForm @add-todo="addTodo" />
    <TodoItem
      v-for="item of items"
      :key="item.id"
      :todo="item"
      @remove-todo="removeTodo"
      @change-completed="changeCompleted"
    />
  </div>
</template>
