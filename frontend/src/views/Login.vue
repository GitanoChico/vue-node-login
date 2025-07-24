<template>
  <div>
    <h2>Login</h2>
    <form @submit.prevent="login">
      <input v-model="username" placeholder="Usuario" />
      <input v-model="password" type="password" placeholder="Contraseña" />
      <button type="submit">Entrar</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return { username: '', password: '' };
  },
  methods: {
    async login() {
      try {
        await axios.post('http://localhost:3000/api/auth/login', {
          username: this.username,
          password: this.password
        }, { withCredentials: true });
        this.$router.push('/dashboard');
      } catch {
        alert('Login fallido');
      }
    }
  }
};
</script>
