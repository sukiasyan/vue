<template>
  <Header />
  <h1>Hello User, Welcome to Add Restaurante Page</h1>
</template>
<script>
import Header from './Header.vue';
export default {
  name: 'AddRestaurante',
  components: {
    Header,
  },
  mounted() {
    let user = localStorage.getItem('user-info');
    if (!user) {
      this.$router.push({ name: 'SignUp' });
    }
  },
};
</script>
