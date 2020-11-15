<template>
  <h1>{{ product }}</h1>
  <p>{{ description }}</p>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      product: 'Socks',
      description: 'fancy socks'
    };
  }
}
</script>
