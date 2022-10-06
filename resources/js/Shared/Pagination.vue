<template>
  <nav>
    <ul class="pagination pagination-sm justify-content-center">
      <Component
        class="page-link"
        v-for="link in links"
        :is="link.url ? 'Link' : 'li'"
        :key="link.label"
        :href="link.url"
        :class="{ 'text-secondary': ! link.url, 'page-active' : link.active }"
        v-html="link.label"
      />
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    links: Array
  }
};
</script>