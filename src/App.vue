<template>
  <HelloWorld/>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css';
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  background-color: black;
}
#app{
  margin: 0 15px;
}
</style>
