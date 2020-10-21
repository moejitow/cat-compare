<template>
  <div id="app">
    <Header :title=title :pages=pages :image=image />
  </div>
</template>

<script>
import Header from './layouts/Header' 

export default {
  name: 'App',
  components: {
    Header
  },
  data() {
    return {
    title: "Cat Compare",
    pages: ["How To", "About"],
    image: "cat.svg" 
    }
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
}
</style>
