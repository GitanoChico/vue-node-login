<template>
  <div>
    <h2>Dashboard</h2>
    <button @click="getRandom">Generar Lista Aleatoria</button>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.contenido }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return { items: [] };
  },
  methods: {
    async getRandom() {
      const res = await axios.get('http://localhost:3000/api/data/random', { withCredentials: true });
      this.items = res.data;
    }
  }
};
</script>
