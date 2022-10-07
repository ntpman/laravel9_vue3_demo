<template>
  <Head title="Create User" />
  <div class="container py-4">
    <div class="d-flex justify-content-between align-items-center">
      <h1>Create New User</h1>
      <Link href="/users" class="btn btn-secondary">Back</Link>
    </div>
    <form @submit.prevent="submit">
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input v-model="form.name" type="text" class="form-control" />
        <span
          v-if="errors.name"
          v-text="errors.name"
          class="text-danger"
        ></span>
      </div>
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input v-model="form.email" type="email" class="form-control" />
        <span
          v-if="errors.email"
          v-text="errors.email"
          class="text-danger"
        ></span>
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input v-model="form.password" type="password" class="form-control" />
        <span
          v-if="errors.password"
          v-text="errors.password"
          class="text-danger"
        ></span>
      </div>
      <button type="submit" class="btn btn-primary" :disabled="processing">
        Submit
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
import { reactive, ref } from "vue";
import { Inertia } from "@inertiajs/inertia";

defineProps({
  errors: Object,
});

let form = reactive({
  name: "",
  email: "",
  password: "",
});

let processing = ref(false);

let submit = () => {
  Inertia.post("/users", form, {
    onStart: () => {
      processing.value = true;
    },
    onFinish: () => {
      processing.value = false;
    },
  });
};
</script>