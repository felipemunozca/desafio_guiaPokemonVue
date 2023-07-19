<template>
  <div id="app">
    <Pokemon/>
  </div>
</template>

<script>
import Pokemon from '@/components/Pokemon.vue';

export default {
  name: 'App',
  components: {
    Pokemon,
  }
}
</script>

<style>
/* * {
  margin: 0;
  padding: 0;
} */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
