<template>
  <div class="main-page">
    Main page from component
    <ProductPanel title="Recommended/Latest" section="recommended" />
    <ProductPanel title="Buy Now" section="buynow" />
    <ProductPanel title="Top Selling" section="topselling" />
    <ProductPanel title="Best offer" section="bestoffer" />
  </div>
</template>


<script>
import ProductPanel from "./ProductPanel.vue";

export default {
  name: "MainPage",
  components: {
    ProductPanel
  }
};
</script>
