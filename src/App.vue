<template>
  <div id="app">
    <header>
      <h1><code>transition-group bug</code></h1>
    </header>
    <Group></Group>
    <footer>
      <span>Copyright © 2019 - &nbsp; Rabbit🐇</span>
    </footer>
  </div>
</template>

<script>
import Group from './components/Group.vue'

export default {
  name: 'app',
  components: {
      Group
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  font-size: 1rem;
  height: 100%;
}

* {
  margin: 0;
  padding: 0;
  list-style: none;
}

html {
  box-sizing: border-box;
  background: #2c3e50;
}
html,
body {
  height: 100%;
}

footer {
  height: 30px;
  font-size: 0.5rem;
}
</style>
