```vue
```

### main v-model 
```vue
<input v-model="searchText" />
```
converts to this 
```vue
<input
  :value="searchText"
  @input="searchText = $event.target.value"
/>

```

-----------------------------------------------
### v-model with emit events


```vue
<CustomInput
  :modelValue="message"
  @update:modelValue="newValue => message = newValue"
/>

```
equal to
```vue

<CustomInput v-model="message" />

```


----------------------------------------
CustomInput.vue 
```vue
<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue']
}
</script>

```

App.vue
```vue 
<script>
import CustomInput from './CustomInput.vue'

export default {
  components: { CustomInput },
  data() {
    return {
      message: 'hello'
    }
  }
}
</script>

<template>
  <CustomInput v-model="message" /> {{ message }}
</template>

```



-----------------------------------------------
```vue
```
```vue
```
```vue
```