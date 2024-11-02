<script setup>
defineProps({
  todo: {
    type: Object
  }
});
</script>

<template>
  <div class="todo-item">
    {{ todo.title }}

    <button class="todo-item__delete"
            @click="$emit('delete', todo.id)">
      delete
    </button>
  </div>
</template>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  padding: 20px;
  font-size: 25px;
  background-color: var(--todo-color-grey);
  border-radius: var(--todo-border-radius);
}

.todo-item__delete {
  padding: 10px 20px;
  background-color: var(--todo-color-red);
  color: var(--todo-color-white);
  border-radius: var(--todo-border-radius);
  transition: background-color var(--todo-default-transition);
}

.todo-item__delete:hover {
  background-color: var(--todo-color-hover-red);
}
</style>