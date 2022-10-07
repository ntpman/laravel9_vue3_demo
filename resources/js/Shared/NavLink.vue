<template>
  <Link :class="{ 'active': active }">
    <slot />
  </Link>
</template>

<script>
export default {
  props: {
    active: Boolean,
  },
};
</script>