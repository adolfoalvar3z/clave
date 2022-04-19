<template>
  <ClavesUsuarios/>
</template>

<script>
import ClavesUsuarios from '@/components/ClavesUsuarios.vue';

export default {
  name: 'App',
  components: {
    ClavesUsuarios,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html, body{
  background: url(/public/jajas.jpg) no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;}
</style>
