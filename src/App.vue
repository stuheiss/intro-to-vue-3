<template>
      <div class="nav-bar"></div>

      <div class="cart">Cart({{ cart }})</div>

      <div class="product-display">
        <div class="product-container">
          <div
            class="product-image"
            :class="{ 'out-of-stock-img': !inStock }"
          >
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
            <div
              v-for="variant in variants" :key="variant.id"
              @mouseover="updateImage(variant.image)"
              class="color-circle"
              :style="{ backgroundColor:variant.color }"
            >
            </div>
            <ul>
              <li v-for="size in sizes" :key="size.id">{{ size }}</li>
            </ul>
            <button
              :disabled="!inStock"
              class="button"
              :class="{ disabledButton: !inStock }"
              @click="addToCart"
            >Add to Cart</button>
            <button
              :disabled="cart <= 0"
              class="button"
              :class="{ disabledButton: cart <= 0 }"
              @click="removeFromCart"
            >Remove from Cart</button>
          </div>
        </div>
      </div>
</template>
<script>

export default {
  name: 'App',
  components: {
  },
  computed: {
    inStock() {
      return this.inventory > 0;
    }
  },
  data() {
    return {
      cart: 0,
      product: 'Socks',
      image: './assets/images/socks_green.jpg',
      inventory: 100,
      onSale: true,
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        { id:2234, color:'green', image:'./assets/images/socks_green.jpg' },
        { id:2235, color:'blue',  image:'./assets/images/socks_blue.jpg'  },
      ],
      sizes: ['small', 'medium', 'large'],
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    removeFromCart() {
      this.cart -= 1;
    },
    updateImage(variantImage) {
      this.image = variantImage;
    }
  },
}
</script>
