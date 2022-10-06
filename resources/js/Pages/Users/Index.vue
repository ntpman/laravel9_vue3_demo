<template>
  <Head title="Users" />
  <div class="container py-4">
    <div class="d-flex justify-content-between align-items-center">
      <h1>Users</h1>
      <input
        v-model="search"
        type="text"
        class="form-control w-25"
        id=""
        placeholder="Search..."
      />
    </div>
    <table class="table">
      <tbody>
        <tr v-for="user of users.data" :key="user.id">
          <td>{{ user.name }}</td>
          <td>
            <Link :href="`/users/${user.id}/edit`">
              <i class="bi bi-pencil-square"></i> edit
            </Link>
          </td>
        </tr>
      </tbody>
    </table>
    <Pagination :links="users.links" />
  </div>
</template>

<script>
import Layout from "../../Shared/Layout.vue";
import Pagination from "../../Shared/Pagination.vue";
export default {
  layout: Layout,
  components: { Pagination },
};
</script>

<script setup>
import { ref, watch } from "vue";
import { Inertia } from "@inertiajs/inertia";

let prorps = defineProps({
  users: Object,
  filters: Object,
});

let search = ref(prorps.filters.search);

watch(search, (value) => {
  Inertia.get(
    "/users",
    { search: value },
    {
      preserveState: true,
      replace: true,
    }
  );
});
</script>

<style>
.page-active {
  color: #fff;
  background: #0d6efd;
}
</style>