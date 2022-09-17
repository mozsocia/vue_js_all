#### two way of emit events

```vue

<button @click="$emit('someEvent')">click me</button>

```

```vue
<button @click="handleClick">click me</button>

export default {
  methods: {
    handleClick() {
      this.$emit('someEvent')
    }
  }
}

```
The parent can then listen to it using v-on:

```vue
<MyComponent @some-event="callback" />

```

-----------------
Event Arguments
```vue
<button @click="$emit('increaseBy', 1)">
  Increase by 1
</button>

```
```vue
<MyButton @increase-by="(n) => count += n" />

```

-----------------------------------------------
------------------------------------------------
### Declaring Emitted Events

```vue
export default {
  emits: ['inFocus', 'submit']
}
```
### Events Validation 

NewCom.vue
```vue
<template>
  <div>
    <h2>This is a popup new</h2>
    <button @click="$emit('sendMe', 34)">Send</button>
  </div>
</template>

<script>
export default {
  name: "NewCom",
  emits: {
    sendMe(n) {
      if (n) {
        console.log("child ", n);
        return true;
      } else {
        console.warn("Invalid submit event payload!");
        return false;
      }
    },
  },
};
</script>
```
App.vue
```vue
  <NewCom @send-me="callback" />

```
```vue
```
```vue
```
```vue
```
