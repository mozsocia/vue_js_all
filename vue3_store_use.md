# how to use in vue 3

```vue
<template>
  <div>
    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.title }}</li>
    </ul>

    <form @submit.prevent="addNewTodo">
      <input type="text" v-model="newTodo" placeholder="Enter a new todo" />
      <button type="submit">Add Todo</button>
    </form>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from "vue";
import { useStore } from "vuex";

const store = useStore();

const newTodo = ref("");
const todos = computed(() => store.getters.getTodos);

const fetchTodos = () => {
  store.dispatch("fetchTodos");
};

const addNewTodo = () => {
  if (newTodo.value) {
    const todo = { title: newTodo.value, completed: false };
    store.dispatch("addTodo", todo);
    newTodo.value = ""; // Clear the input field
  }
};

onMounted(fetchTodos); // Fetch todos when the component is mounted
</script>
```
