<template>
  <div id="app">
    <header>
      <h1>{{ sitename }}</h1>
      <button class="checkoutbutton" v-on:click="showCheckout()" v-bind:disabled="cart.length === 0">
                    {{this.cart.length}} <i class="fas fa-shopping-cart"></i>Checkout
                </button> 
 
 
       <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.12.1/css/all.css" crossorigin="anonymous">

    </header>
    <main>
      <product-list :lessons="lessons" @addProduct="addToCart"></product-list>
      <checkout-form :cart="cart" @removeProduct="removeProduct"></checkout-form>
    </main>
  </div>
</template>
<script>

import ProductList from "./components/LessonsList.vue";
import CheckoutForm from "./components/Checkout.vue";


export default {
name: "App",
components: {ProductList, CheckoutForm},
  data(){
    return{
    sitename: "After school club",
  
    lessons: [],
    cart: [],
  


    }

  },

  
            created: function () {
              let that = this
                          fetch('http://dominique-walker-cst1345-cw2.herokuapp.com/lessons').then(
                              function (response) {

                                  response.json().then(
                                      function (json) {

                                        that.lessons = json;

                                          console.log(JSON.stringify(json))
                                          that.lessons.push(json)
                                          console.log("lessons retreived sucessfully");
                                      });

          },

                          )

      },
      
    
      
       
    
   

  





  

methods: {
addToCart(lesson) {
this.cart.push(lesson);
lesson.Spaces --; 
},
removeProduct(lesson) {
this.cart.splice(this.cart.indexOf(lesson),1);
lesson.Spaces ++;
},


  showCheckout() {
document.getElementsByClassName('checkout')[0].style.display = 'block';

},






}


}

</script>