<template>
  <main>
    <div v-for="lesson in lessons" :key="lesson.id">
      <h2>{{ lesson.Subject }}</h2>
      <figure>
        <img v-bind:src="lesson.Image" />
      </figure>
      <p>Location: {{ lesson.Location }}></p>
      <p>Price: {{ lesson.Price }}</p>
      <p>Available stock: {{ lesson.Spaces }}</p>
      <button @click="addToCart(lesson)">Add to cart</button>
    </div>
  </main>
</template>

<script>
export default {
  name: "ProductList",
  props: ['lessons'],
 

 
  data() { return {}; },
    
  methods: {
    addToCart(lesson) {
      this.$emit("addProduct", lesson);
    }
  }
    }
  

  
  
</script>