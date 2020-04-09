<template>
    <div class="shopping-cart-page">
        <h1>Shopping cart</h1>
        <div v-if=!items.length>Your shopping cart is empty, try to add more.</div>

        <table class="table" v-if=items.length>
            <tr>
                <th>Product</th>
                <th>Price</th>
                <th>Quantity</th>
                <th>Amount</th>
                <th>Action</th>
            </tr>
            <tr v-for="(item, index) in items" :key="item.productId + '-'+index">
                <td>
                    <b-link :to="'/products/'+item.productId">
                    <img :src="item.optionImage" class="image-c" />
                    </b-link>
                </td>
                <td>{{ item.price}}</td>
                <td>{{ item.qty}}</td>
                <td>{{ item.total}}</td>
                <td>
                    <b-button variant="danger" @click="removeItem (index)">Remove</b-button>
                </td>

            </tr>
            <tr>
                <td>Total:</td>
                <td></td>
                <td></td>
                <td>{{total}}</td>
                <td></td>
            </tr>
        </table>
        <b-button variant="success" size="lg"
        v-if="this.items.length"
        @click="orderNow">Order now</b-button>
    </div>
</template>

<script>
import axios from "axios";
export default {
    name: 'ShoppingCartPage',
    computed:{

        items: function(){
            return this.$root.$data.cart.items || [];
        },
        total: function(){
            let sum = 0
            for (const item of this.items){
                sum += item.total
            }
            return sum
        }
    },
    methods: {
        removeItem: function(index){
            if (!this.$root.$data.cart.items) this.$root.$data.cart.items = []
            this.$root.$data.cart.items.splice(index,1);
            this.$root.$data.saveCart();
        },
        orderNow: function(){
            let data = this.$root.$data
            let router = this.$router;
            axios.post("https://euas.person.ee/user/carts/"+this.$root.$data.cart.id +"/orders",
            this.$root.$data.cart).then(function (){
              router.push('/orders/'+ data.cart.id+'?success=true')
                data.reinitCart();
                
            })
        }
    }
    
}
</script>

<style scoped>
.image-c{
    max-width: 100px;
    max-height: 110px;
}

</style>