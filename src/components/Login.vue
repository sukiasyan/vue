<template>
  <img class="logo" alt="Vue logo" src="../assets/logo.png" />
  <h1>Login</h1>
  <div class="login">
    <input type="text" v-model="email" placeholder="Enter email" />
    <input type="password" v-model="password" placeholder="Enter password" />
    <button v-on:click="login" class="button">Login</button>

    <p><router-link to="/sign-up">Sign Up</router-link></p>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'LogIn',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    async login() {
      let result = await axios.get(
        `http://localhost:3000/users?email=${this.email}&password=${this.password}`
      );
      console.warn(result.status, result.data);
      if (result.status === 200 && result.data.length > 0) {
        localStorage.setItem('user-info', JSON.stringify(result.data));
        this.$router.push({ name: 'Home' });
      }
    },
  },
  mounted() {
    let user = localStorage.getItem('user-info');
    if (user) {
      this.$router.push({ name: 'Home' });
    }
  },
};
</script>
