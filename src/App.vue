<template>

  <div id="app">
    <AppContainer/>
  </div>
  
</template>

<script>
import AppContainer from './components/AppContainer.vue'

export default {
  name: 'app',
  components: {
    AppContainer
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  min-height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
body {
  margin: 0;
}
</style>
