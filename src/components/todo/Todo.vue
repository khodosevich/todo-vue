<script>
import TodoItem from "@/components/todo/TodoItem.vue";

let nextTodoId = 1;

export default {
  components: {
    TodoItem
  },
  data() {
    return {
      newTodoText: '',
      todos: [
        {
          id: nextTodoId++,
          title: 'todo vue'
        },
        {
          id: nextTodoId++,
          title: 'counter'
        }
      ]
    }
  },
  methods: {
    newTodo() {
      const newTodo = this.newTodoText.trim();

      if (newTodo) {
        this.todos.push({
          id: nextTodoId++,
          title: newTodo
        });

        this.newTodoText = '';
      }
    },
    deleteTodo(removeId) {
      this.todos = this.todos.filter(todo => todo.id !== removeId);
    }
  }
};
</script>

<template>
  <div class="todos">
    <div class="todos__add-todo">
      <input type="text"
             class="todos__input"
             v-model="newTodoText"
             @keydown.enter="newTodo"
             placeholder="new todo">
      <button @click="newTodo"
              class="todos__btn">
        add
      </button>
    </div>

    <ul class="todos__items" v-if="todos.length">
      <TodoItem v-for="todo in todos"
                :key="todo.id"
                :todo="todo"
                @delete="deleteTodo"
      />
    </ul>

    <div class="todos__empty" v-else>
      empty
    </div>
  </div>
</template>

<style scoped>
.todos {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin-block: var(--todo-margin-offset);
}

.todos__input {
  padding: 10px;
  font-size: 20px;
  background-color: var(--todo-color-white);
  border: 1px solid var(--todo-color-grey);
  border-radius: var(--todo-border-radius);
  outline: 0;
}

.todos__add-todo {
  display: flex;
  gap: 10px;
  margin-bottom: var(--todo-margin-offset);
}

.todos__btn {
  padding: 10px 20px;
  background-color: var(--todo-color-green);
  color: var(--todo-color-white);
  border-radius: var(--todo-border-radius);
  transition: background-color var(--todo-default-transition);
}

.todos__btn:hover {
  background-color: var(--todo-color-hover-green);
}

.todos__items {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 20px;
  margin: 0;
  padding: 0;
}

.todos__empty {
  font-size: 40px;
}
</style>