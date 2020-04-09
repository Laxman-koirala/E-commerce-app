<template>
  <div class="header">
  <b-navbar type="dark" variant="dark">
    <b-navbar-brand href="#">E-commerce Platform</b-navbar-brand>
      <b-navbar-nav>
        <b-nav-item> 
     <b-link to="/">Home</b-link>
        </b-nav-item>
        <b-nav-item>
   <b-link to="/cart">Shopping cart</b-link>
        </b-nav-item>
        <b-nav-item>
<b-link to="/orders">My Orders</b-link>
        </b-nav-item>

       

      </b-navbar-nav>
  </b-navbar>
</div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
</style>
