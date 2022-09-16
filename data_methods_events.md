```vue
<template>
    <div v-if="showBooks">
      <p>{{ title }} - by {{ author }}, {{ age }} years old</p>
    </div>
    <div v-else>
      <p>Click the button below to show books</p>
    </div>
    
    <button @click="toggleShowBooks">
      <span v-if="showBooks">Hide books</span>
      <span v-else>Show books</span>
    </button>
    
    <br>
    <!-- mouse events -->
    <div class="box" @mouseover="handleEvent($event, 5)">mouseover (enter)</div>
    <div class="box" @mouseleave="handleEvent">mouseleave</div>
    <div class="box" @dblclick="handleEvent">double click me</div>
    <div class="box" @mousemove="handleMousemove">position {{ x }} {{ y }}</div>
    
  </template>

```
```vue
<script>
data() {
    return {
      showBooks: true,
      title: 'The Way of Kings',
      author: 'Brandon Sanderson',
      age: 45,
      x: 0,
      y: 0,
    }
  },
  methods: {
    toggleShowBooks() {
      this.showBooks =  !this.showBooks
    },
    handleEvent(e, data) {
      console.log(e.type, e)
      if (data) {
        console.log(data)
      }
    },
    handleMousemove(e) {
      this.x = e.offsetX
      this.y = e.offsetY
    }
  }
  </script>
  ```
