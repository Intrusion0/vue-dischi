<template>
  <div id="app">
    <!-- Componente Header -->
    <Header
    :element="cards"
    @genre="genreHandler"
    @author="authorsHandler"
    />
    <main>
      <!-- Componente Tracks -->
      <Tracks
      @tracks="tracksHandler"
      :selectedGenreOption="this.selectedGenreOption"
      :selectedAuthorOption="this.selectedAuthorOption"
      />
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
  },
  data() {
    return {
      cards: [],
      selectedGenreOption: 'All',
      selectedAuthorOption: 'All'
    }
  },
  methods: {
    tracksHandler(tracks) {
      this.cards = tracks;
    },
    genreHandler(genre) {
      this.selectedGenreOption = genre;
    },
    authorsHandler(author) {
      this.selectedAuthorOption = author;
    }
  }
}
</script>

<style lang="scss">
// General rules
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

// main
main {
  width: 100%;
  background-color: #1e2d3b;
  padding: 75px 0 80px 0;
}

</style>
