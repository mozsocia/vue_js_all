# how to use in vue 2

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

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  data() {
    return {
      newTodo: "",
    };
  },
  computed: {
    ...mapGetters(["getTodos"]),
    todos() {
      return this.getTodos;
    },
  },
  created() {
    this.fetchTodos(); // Fetch todos when the component is created
  },
  methods: {
    ...mapActions(["fetchTodos", "addTodo"]),
    addNewTodo() {
      if (this.newTodo) {
        const todo = { title: this.newTodo, completed: false };
        this.addTodo(todo);
        this.newTodo = ""; // Clear the input field
      }
    },
  },
};
</script>
```
