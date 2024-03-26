```vue
<script setup>
import { useForm } from 'vee-validate';
import * as yup from 'yup';
import { onMounted, onUpdated } from 'vue';

const { errors, handleSubmit, defineField } = useForm({
  validationSchema: yup.object({
    email: yup.string().email().required(),
    password: yup.string().min(6).required(),
  }),
});
onMounted(() => {
  console.log('Component mounted');
});
onUpdated(() => {
  console.log('Component updated');
  if (errors) {
    console.log(errors.value);
  }
});
// Creates a submission handler
// It validate all fields and doesn't call your function unless all fields are valid
const onSubmit = handleSubmit((values) => {
  alert(JSON.stringify(values, null, 2));
});

const [email, emailAttrs] = defineField('email');
const [password, passwordAttrs] = defineField('password');

</script>

<template>
  <form @submit="onSubmit">
    <input
      type="email"
      v-model="email"
      v-bind="emailAttrs"
      :class="{ red: errors.email }"
    />
    <div>{{ errors.email }}</div>

    <input
      type="password"
      v-model="password"
      v-bind="passwordAttrs"
      :class="{ red: errors.password }"
    />
    <div>{{ errors.password }}</div>

    <button>Submit</button>
  </form>
</template>
```
