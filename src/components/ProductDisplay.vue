<template>
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
        <p v-if="quantity > 10">In Stock</p>
        <p v-else-if="quantity <= 10 && quantity > 0">Almost sold out!</p>
        <p v-else>Out of Stock</p>
        <p v-if="onSale">On Sale</p>
        <p>Shipping: {{ shipping }}</p>

        <ProductDetails :details="details" />

        <div
          v-for="(variant, index) in variants" :key="variant.id"
          @mouseover="updateVariant(index)"
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
import ProductDetails from './ProductDetails'

export default {
  name: 'ProductDisplay',
  components: {
    ProductDetails
  },
  props: {
    premium: {
      type: Boolean,
      required: true,
    },
  },
  computed: {
    shipping() {
      return this.premium
        ? 'Free'
        : '$2.99';
    },
    inStock() {
      return this.quantity > 0;
    },
    image() {
      return this.variants[this.selectedVariant].image;
    },
    quantity() {
      return this.variants[this.selectedVariant].quantity;
    },
    onSale() {
      return this.variants[this.selectedVariant].onSale;
    },
  },
  data() {
    return {
      product: 'Socks',
      selectedVariant: 0,
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        { id:2234, color:'green', image:'./assets/images/socks_green.jpg', quantity:50, onSale:true },
        { id:2235, color:'blue', image:'./assets/images/socks_blue.jpg', quantity:0, onSale:false },
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
    updateVariant(index) {
      this.selectedVariant = index;
    },
  },
}
</script>
