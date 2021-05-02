<template>
  <div id="app">
    <Ticket />
  </div>
</template>

<script>
import Ticket from './components/Ticket.vue'

export default {
  name: 'App',
  components: {
    Ticket
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  width: 100vw;
  height: 100vh;
  background: rgb(0,219,201);
  background: linear-gradient(162deg, rgba(0,219,201,1) 0%, rgba(42,51,255,1) 100%);
  background-repeat: no-repeat;
  background-attachment: fixed;
  font-family: 'Roboto Mono', monospace;
  margin: 0;
  padding: 0;
}
#app {
  width: 100%;
  height: 100%;
}
</style>
