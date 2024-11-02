<script setup>
import { ref, computed } from 'vue'
import Counter from "@/pages/Counter.vue";
import Todo from "@/components/todo/Todo.vue";
import Home from "@/pages/Home.vue";

const routes = {
  '/': Home,
  '/counter': Counter,
  '/todo': Todo
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/']
})
</script>

<template>
  <header>
    <nav class="navigation">
      <a class="navigation__link" href="#/">home</a>
      <a class="navigation__link" href="#/counter">counter</a>
      <a class="navigation__link" href="#/todo">todo</a>
    </nav>
  </header>

  <main>
    <component :is="currentView" />
  </main>
</template>

<style>
@import './styles/root.scss';
@import './styles/base.scss';

.navigation {
  display: flex;
  gap: 20px;
}

.navigation__link {
  font-size: 25px;
  text-decoration: none;
  color: coral;
}
</style>