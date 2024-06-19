<template>
  <div id="app">
    <header>
      <h1>Vue.js API Integration</h1>
    </header>
    <main>
      <ApiData />
    </main>
  </div>
</template>

<script>
import ApiData from './components/ApiData.vue';

export default {
  name: 'App',
  components: {
    ApiData
  }
};
</script>

<style>
body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  text-align: center;
}

header {
  background: #42b983;
  padding: 20px;
  color: white;
}

main {
  padding: 20px;
}

@media (max-width: 600px) {
  .api-data {
    padding: 10px;
  }

  input {
    padding: 8px;
  }

  li {
    padding: 8px;
  }
}
</style>
