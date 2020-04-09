<template>
  <div class="orderDetails">
   <h2> Order Details</h2>
   <b-alert show variant="success"
   v-if="this.$route.query.success"
   >Thank you for submitting your order. It will be shipped in 7 working days</b-alert>
  <table class="table">
      <tr>
        <th>Product</th>
        <th>Price</th>
        <th>Quantity</th>
        <th>Amount</th>
        <th>Actions</th>
      </tr>

      <tr  v-for="(item, index) in order.items" :key="item.productId + '-' + index">
        <td>
          <b-link :to="'/products/' + item.productId"> 
          <img :src="item.optionImage" class="product-image" />
          </b-link>
        </td>
        <td>{{item.price }}</td>
        <td>{{item.qty }} </td>
        <td>{{item.total }} </td>
        <td>
          <b-link :to="'/products/'+ item.productId"> 
            <b-button  variant="primary">Product details </b-button>
          </b-link>    
        </td>
      </tr>
      <tr class = "total-row" v-if="order.items">
        <td>TOTAL: </td> 
        <td></td>
        <td></td> 
        <td>{{total}}</td>
      </tr>
    </table>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: 'orderDetails',
  computed:{
    total : function() {
      let sum=0
      for (const item of this.order.items ){
        sum += item.total
      }
      return sum
    }
  },
  data: function(){
    return{
      order: {},
    }
  },
  mounted() {
  axios
  .get("https://euas.person.ee/user/orders/"+ this.$route.params.orderId)
  .then(response =>{
    this.order=response.data;
    console.log(response.data);
    
  }).catch(error =>{
    console.log(error);
  })
  },
  
}
</script>

<style scoped>
.product-image{
    max-width: 100px;
    max-height: 110px;
}

</style>