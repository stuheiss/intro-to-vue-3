<template>
      <div class="nav-bar"></div>

      <div class="product-display">
        <div class="product-container">
          <div class="product-image">
            <img :src="image">
          </div>
          <div class="product-info">
            <h1>{{ product }}</h1>
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
    };
  }
}
</script>
