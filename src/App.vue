<template>
      <div class="nav-bar"></div>

      <div class="product-display">
        <div class="product-container">
          <div class="product-image">
            <img :src="image">
          </div>
          <div class="product-info">
            <h1>{{ product }}</h1>
            <p v-if="inventory > 10">In Stock</p>
            <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out!</p>
            <p v-else>Out of Stock</p>
            <p v-if="onSale">On Sale</p>
          </div>
        </div>
      </div>
</template>
<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      product: 'Socks',
      image: './assets/images/socks_green.jpg',
      inventory: 100,
      onSale: true,
    };
  }
}
</script>
