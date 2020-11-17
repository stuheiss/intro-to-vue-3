<template>
      <div class="nav-bar"></div>

      <div class="cart">Cart({{ cart }})</div>
      <ProductDisplay :premium="premium" />
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
      cart: 0,
      premium: true,
    };
  },
  methods: {
  },
}
</script>
