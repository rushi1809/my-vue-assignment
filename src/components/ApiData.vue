<template>
  <div class="api-data">
    <input v-model="query" @input="fetchData" placeholder="Search..." />
    <ul>
      <li v-for="item in filteredData" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      query: '',
      data: [],
      filteredData: []
    };
  },
  methods: {
    async fetchData() {
      try {
        const response = await axios.get(`https://api.github.com/search/repositories?q=${this.query}`);
        this.data = response.data.items;
        this.filteredData = this.data;
      } catch (error) {
        console.error(error);
      }
    }
  },
  watch: {
    query(newQuery) {
      this.filteredData = this.data.filter(item =>
        item.name.toLowerCase().includes(newQuery.toLowerCase())
      );
    }
  }
};
</script>

<style scoped>
.api-data {
  max-width: 600px;
  margin: auto;
}

input {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  padding: 10px;
  border: 1px solid #eee;
  border-radius: 4px;
  margin-bottom: 10px;
  background: #f9f9f9;
}
</style>
