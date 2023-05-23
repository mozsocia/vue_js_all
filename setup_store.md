# Store setup

```js
import { createStore } from 'vuex'

const store = createStore({
  state: {
    todos: []
  },
  mutations: {
    SET_TODOS(state, todos) {
      state.todos = todos;
    },
    ADD_TODO(state, todo) {
      state.todos.push(todo);
    }
  },
  actions: {
    fetchTodos({ commit }) {
      // Make an API call or fetch todos from any data source
      // For simplicity, we'll use a hardcoded example
      const todos = [
        { id: 1, title: 'Todo 1', completed: false },
        { id: 2, title: 'Todo 2', completed: true },
        { id: 3, title: 'Todo 3', completed: false }
      ];

      // Commit the todos to the store
      commit('SET_TODOS', todos);
    },
    addTodo({ commit }, todo) {
      // Generate a unique ID for the new todo (replace with your logic)
      const newTodo = { ...todo, id: Date.now() };

      // Commit the new todo to the store
      commit('ADD_TODO', newTodo);
    }
  },
  getters: {
    getTodos(state) {
      return state.todos;
    }
  }
});

export default store;
```

main.js

```js
import { createApp } from 'vue'
import './style.css'
import App from './App.vue'
import store from './store'


createApp(App)
  .use(store)
  .mount('#app')
```
