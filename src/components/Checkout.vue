<template>
<div class = "checkout">
<h2>Checkout</h2>
<h3>Added products</h3>
<div v-for='lesson in cart' :key="lesson.id">
 <figure>
        <img v-bind:src="lesson.Image" width="50" height="50">
      </figure>  
{{lesson.Subject}}
{{lesson.Location}}

<button @click='remove(lesson)'>remove</button>
</div>
<p>
<strong>Name </strong>
<input v-model="name" />
<strong> Address </strong>
<input v-model="address" /> 
<strong> Phone Number </strong>
<input v-model="phonenumber">
  <button class="checkoutbutton"><i class="fas fa-check"></i> Submit
                </button> 
 
</p>

                      <li v-for="error in errors" :key="error">{{ error }}</li>

</div>
</template>

<script>
export default {
name: "CheckoutForm",
props: ['cart'],

data() {
return {
  name: "" , address: "", phonenumber: "",};
},

methods: {
  
remove(lesson) {
this.$emit('removeProduct'
, lesson)
},




}

}
</script>