<template>
  <div class="category-page">
    Category page for {{this.$route.params.categoryAlias}}
    <ProductPanel :categoryAlias="this.$route.params.categoryAlias" />
  </div>
</template>

<script>
import ProductPanel from "./ProductPanel.vue";
export default {
  name: "CategoryPage",
  components: {
    ProductPanel
  }
};
</script>

<style scoped>
</style>