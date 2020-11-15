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
            <ul>
              <li v-for="detail in details" :key="detail.id">{{ detail }}</li>
            </ul>
            <div v-for="variant in variants" :key="variant.id">{{ variant.color }}</div>
            <ul>
              <li v-for="size in sizes" :key="size.id">{{ size }}</li>
            </ul>
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
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        { id:2234, color:'green' },
        { id:2235, color:'blue' },
      ],
      sizes: ['small', 'medium', 'large'],
    };
  }
}
</script>
