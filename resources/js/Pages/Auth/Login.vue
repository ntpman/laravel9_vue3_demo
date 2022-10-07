<template>
  <Head title="Login" />
  <div class="container py-4">
    <div class="d-flex justify-content-between align-items-center">
      <h1>Login</h1>
    </div>
    <form @submit.prevent="submit">
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input v-model="form.email" type="email" class="form-control" />
        <span
          v-if="form.errors.email"
          v-text="form.errors.email"
          class="text-danger"
        ></span>
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input v-model="form.password" type="password" class="form-control" />
        <span
          v-if="form.errors.password"
          v-text="form.errors.password"
          class="text-danger"
        ></span>
      </div>
      <button type="submit" class="btn btn-primary" :disabled="form.processing">
        Login
      </button>
    </form>
  </div>
</template>

<script>
import Layout from "../../Shared/Layout.vue";
export default {
  layout: Layout,
};
</script>

<script setup>
import { useForm } from '@inertiajs/inertia-vue3';
let form = useForm({
  email: '',
  password: '',
});

let submit = () => {
  form.post('/login');
};
</script>