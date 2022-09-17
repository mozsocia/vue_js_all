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


-------------------------------------------
-----------------------------------------------
UserName.vue
```vue
<script>
export default {
  props: {
        firstName: String,
        lastName: String
	},
  emits: ['update:firstName', 'update:lastName']
}
</script>

<template>
  <input
    type="text"
    :value="firstName"
    @input="$emit('update:firstName', $event.target.value)"
  />
  <input
    type="text"
    :value="lastName"
    @input="$emit('update:lastName', $event.target.value)"
  />
</template>
```

App.vue

```vue
<script>
import UserName from './UserName.vue'

export default {
  components: { UserName },
  data() {
    return {
      first: 'John',
      last: 'Doe'
    }
  }
}
</script>

<template>
  <h1>{{ first }} {{ last }}</h1>
  <UserName
    v-model:first-name="first"
    v-model:last-name="last"
  />
</template>
```
```vue
```