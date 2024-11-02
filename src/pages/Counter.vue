<script setup>
import {ref} from "vue";
import Button from "@/components/Button.vue";

const count = ref(0);
</script>

<template>
  <div class="counter">
    <h1 class="title">
      Counter: {{ count }}
    </h1>

    <div class="counter__btns">
      <Button @click="count++" title="+" classes="btn"/>
      <Button @click="count--" title="-" classes="btn"/>
    </div>

    <Button @click="count=0" title="reset" classes="btn btn_reset"/>
  </div>
</template>

<style>
.counter {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.counter__btns {
  display: flex;
  gap: 20px;
  margin-bottom: var(--todo-margin-offset);
}
</style>