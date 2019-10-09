<template>
  <div id="app">
    <Nav msg="Let's get started"/>
  </div>
</template>

<script>
import Nav from './components/Nav.vue'

export default {
  name: 'app',
  components: {
    Nav
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  box-sizing: border-box;
	margin:0;
  padding:0;
}

h1, h2, h3, h4, h5, h6, p {
	margin: 0;
}

*, *:before, *:after {
	box-sizing: inherit;
}
</style>
