<template>
      <div class="nav-bar"></div>

      <div class="cart">Cart({{ cart.length }})</div>
      <div class="cart">Cart({{ cart }})</div>
      <ProductDisplay :premium="premium" @add-to-cart="updateCart" @remove-from-cart="removeFromCart" />
</template>
<script>
import ProductDisplay from './components/ProductDisplay'

export default {
  name: 'App',
  components: {
    ProductDisplay
  },
  data() {
    return {
      cart: [],
      premium: true,
    };
  },
  methods: {
    updateCart(id) {
      this.cart.push(id);
    },
    removeFromCart(id) {
      const index = this.cart.indexOf(id);
      if (index >= 0) {
        this.cart.splice(index, 1);
      }
    },
  },
}
</script>
