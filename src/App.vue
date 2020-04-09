<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col cols="12">
          <Header />
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="3">
          <CategoriesMenu />
        </b-col>
        <b-col cols="9">
          <router-view :key="$route.fullPath"></router-view>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import CategoriesMenu from "./components/CategoriesMenu.vue";
export default {
  name: "App",
  components: {
    Header,
    CategoriesMenu
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


