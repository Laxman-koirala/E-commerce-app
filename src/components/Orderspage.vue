<template>
  <div class="order-page">
    <h3>My orders</h3>
    <table class="table">
      <tr>
        <th>OrderID</th>
        <th>Items</th>
        <th>Total amount</th>
        <th>Actions</th>
      </tr>
      <tr v-for="order in orders" :key="order.id">
      <td>{{order.id}}</td>
      <td>{{order.items.length}} item(s)</td>
       <td>{{orderAmount(order)}}</td>
      <td>
        <b-button :to="'/orders/' + order.id" variant="primary">Order details</b-button>
      </td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "OrdersPage",
  data: function() {
    return {
      orders: {},
    }
  },
  mounted() {
    axios
      .get("https://euas.person.ee/user/orders")
      .then(response => {
        this.orders = response.data;
      })
      .catch(error => {
        console.log(error);
      });
  },
  
  methods: {
    orderAmount: function(order) {
      let sum = 0;
      for (const item of order.items) {
        sum += item.total;
      }
      return sum;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>