<template>
  <div id="app">
    <h1>Icons Repository</h1>
    <ul class="app-icons">
      <li><icon variant="home" color="blue"/></li>
      <li><icon variant="profile"/></li>
      <li><icon variant="cart" opacity="0.5"/></li>
      <li><icon variant="no-such-icon"/></li>
    </ul>
  </div>
</template>

<script>
import Icon from './components/icons/Icon.vue'
export default {
  name: 'app',

  components: {
    Icon,
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.app-icons {
  list-style: none;
  display: block;
}

.app-icons:after {
  clear: both;
}

.app-icons > li {
  float: left;
  width: 50px;
  height: 50px;
  margin-right: 10px;
  padding: 20px;
  background-color: gray;
  border-radius: 3px;
  border: 1px solid black;
}
</style>
