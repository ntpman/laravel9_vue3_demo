<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark mt-2">
    <div class="container">
      <a class="navbar-brand" href="#">
        <i class="bi bi-code-slash"></i> 
        <small class="fw-light"> Demo </small>
        <small class="text-success">Laravel9 + Vue3</small></a
      >
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li>
            <NavLink href="/" :active="$page.component == 'Home'">
              Home
            </NavLink>
          </li>
          <li>
            <NavLink href="/users" :active="$page.component == 'Users'">
              Users
            </NavLink>
          </li>
          <li>
            <NavLink href="/settings" :active="$page.component == 'Settings'">
              Settings
            </NavLink>
          </li>
        </ul>
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
          <li>
            <NavLink href="#" class="text-white">
              Welcome Back, <span class="fst-italic text-warning"> {{ username }} </span>
            </NavLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import NavLink from "./NavLink.vue";

export default {
  components: { NavLink },

  computed: {
    username() {
      return this.$page.props.auth.user.username
    }
  },
};
</script>