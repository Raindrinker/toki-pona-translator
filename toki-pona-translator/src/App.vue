<template>
  <Translator/>
  <Dictionary/>
</template>

<script>
import Translator from './components/Translator.vue'
import Dictionary from "./components/Dictionary";

export default {
  name: 'App',
  components: {
    Dictionary,
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
  margin: 0;
  padding: 0;
}

body {
  padding: 0;
  margin: 0;
}
</style>
