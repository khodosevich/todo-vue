<script setup>
defineProps({
  title: {
    type: String
  },
  classes: {
    type: String
  }
});
</script>

<template>
  <button :class="classes">
    {{ title }}
  </button>
</template>

<style>
.btn {
  padding: 20px 40px;
  background-color: var(--todo-color-beige);
  border-radius: var(--todo-border-radius);
  font-size: 30px;
  transition: background-color var(--todo-default-transition);
}

.btn:hover {
  background-color: var(--todo-color-hover-beige);
}

.btn_reset {
  background-color: var(--todo-color-red);
}

.btn_reset:hover {
  background-color: var(--todo-color-hover-red);
}
</style>