<template>
  <header>
      <img src="@/assets/img/logo-spotify.png" alt="logo spotify">
      <!-- Componente Select Genre -->
      <SelectGenre @changeGenre="selectGenreOption" />
      <!-- Componente SelectAuthor -- BONUS -- -->
      <SelectAuthor :details="element" @changeAuthor="selectAuthorOption" />
  </header>
</template>

<script>
import SelectGenre from "./SelectGenre.vue"
import SelectAuthor from "./SelectAuthor.vue"

export default {
  name: 'Header',
  props: {
      element: Array
  },
  components: {
    SelectGenre,
    SelectAuthor
  },
  data() {
    return {
      test: [],
    }
  },
  methods: {
    selectGenreOption(event) {
      this.selectedGenreOption = event.target.value;
      this.$emit('genre', this.selectedGenreOption);
    },
    selectAuthorOption(event) {
      this.selectedAuthorOption = event.target.value;
      this.$emit('author', this.selectedAuthorOption);
    }
  }
}
</script>

<style scoped lang="scss">

header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #2e3a46;
    width: 100%;
    padding: 12px 23px;
}
</style>
