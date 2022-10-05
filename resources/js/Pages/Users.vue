<template>
  <Head title="Users" />
  <div class="container py-4">
    <h1>Users</h1>
    <table class="table table-bordered table-sm">
      <tbody v-for="user of users.data" :key="user.id">
        <tr>
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td><i class="bi bi-pencil-square"></i> Edit</td>
        </tr>
      </tbody>
    </table>
    <nav>
      <ul class="pagination pagination-sm justify-content-center">
        <li class="d-flex" aria-current="page">
        <Link
          class="page-link"
          v-for="link in users.links"
          :key="link.label"
          :href="link.url"
          v-html="link.label"
        />
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import Layout from "../Shared/Layout.vue";
export default {
  layout: Layout,
  props: {
    users: Object,
  },
};
</script>