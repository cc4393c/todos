<script setup>
defineProps(["todo"]);

const emit = defineEmits(["change-completed", "remove-todo"]);

const removeTodo = (id) => {
  emit("remove-todo", id);
};

const changeCompleted = (id) => {
  emit("change-completed", id);
};
</script>

<template>
  <div>
    <input type="checkbox" @click="changeCompleted(todo.id)" />
    <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
      {{ todo.content }}
    </span>
    <button @click="removeTodo(todo.id)">Delete</button>
  </div>
</template>
