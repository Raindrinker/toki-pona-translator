<template>
  <Translator/>
</template>

<script>
import Translator from './components/Translator.vue'

export default {
  name: 'App',
  components: {
    Translator
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

  height: 100vh;
  overflow: hidden;
  overflow-y: hidden;
  margin: 0;
  padding: 0;
}

body {
  padding: 0;
  margin: 0;
}
</style>
