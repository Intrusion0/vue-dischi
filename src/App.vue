<template>
  <div id="app">
    <!-- Componente Header -->
    <Header/>
    <main>
      <!-- Componente Tracks -->
      <Tracks/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tracks from './components/Tracks.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tracks
  }
}
</script>

<style lang="scss">
// General rules
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

</style>
