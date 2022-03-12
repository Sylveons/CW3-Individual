<template>
  <main>
    <div v-for="lesson in lessons" :key="lesson.id">
      <h2>{{ lesson.Subject }}</h2>
      <figure>
        <img v-bind:src="lesson.Image" width="150" height="150">
      </figure>
      <p>Location: {{ lesson.Location }}</p>
      <p>Price: {{ lesson.Price }}</p>
      <p>Available stock: {{ lesson.Spaces }}</p>
         <button class="add to cart" v-on:click="addToCart(lesson)"
                        v-bind:disabled="lesson.Spaces === 0 ">Add to
                        cart</button>
    </div>
  </main>
</template>

<script>
export default {
  name: "ProductList",
  props: ["lessons"],

  data() {
    return {};
  },

  methods: {
    addToCart(lesson) {
      this.$emit("addProduct", lesson);
    },
    
  },
};
</script>