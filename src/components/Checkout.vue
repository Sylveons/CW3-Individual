<template>
<div>
<h2>Checkout</h2>
<h3>Added products</h3>
<div v-for='lesson in cart' :key="lesson.id">
{{lesson.Subject}}
{{lesson.Location}}
<button @click='remove(product)'>remove</button>
</div>
<p>
<strong>Name </strong>
<input v-model="name" />
<strong> Address </strong>
<input v-model="address" /> 
<strong> Phone Number </strong>
<input v-model="phonenumber" /> 
  <button class="checkoutbutton" v-on:click="showCheckout()" v-bind:disabled="cart.length === 0">
                    <!-- add the cart icon -->
                    {{this.cart.length}} Checkout
                </button>
</p>
</div>
</template>

<script>
export default {
name: "CheeckoutForm",
props: ['cart'],
data() {
return { name: "" , address: "", PhoneNumber: "",};
},
methods: {
remove(lesson) {
this.$emit('removeProduct'
, lesson)
}
}
};
</script>