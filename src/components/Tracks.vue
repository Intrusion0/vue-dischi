<template>
  <div class="container-tracks">
      <!-- Componente Select Genre -->
      <SelectGenre 
      @changeGenre="selectGenreOption"
      />
      <!-- Componente SelectAuthor -- BONUS -- -->
      <SelectAuthor
      :details="cards"
      @changeAuthor="SelectAuthorOption"
      />
      <!-- Componente Loader -->
      <Loader v-if="contCards == false"/>
      <!-- Componente CardTrack -->
      <CardTrack v-else 
      v-for="card, i in filteredAuthorCards" 
      :key="i"
      :details="card"
      />
  </div>
</template>

<script>
import axios from 'axios'
import CardTrack from './CardTrack.vue'
import Loader from './Loader.vue'
import SelectGenre from './SelectGenre.vue'
import SelectAuthor from './SelectAuthor.vue'

export default {
  name: 'Traks',
  components: {
      CardTrack,
      Loader,
      SelectGenre,
      SelectAuthor
  },
  data() {
      return {
          apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
          cards: [],
          contCards: false,
          selectedGenreOption: 'All',
          selectedAuthorOption: 'All'
      }
  },
  computed: {
      filteredGenreCards() {
          if (this.selectedGenreOption == 'All') {
              return this.cards;
          }
          return this.cards.filter((card) => {
              return card.genre === this.selectedGenreOption;
          })
      },
      filteredAuthorCards() {
          if (this.selectedAuthorOption == 'All') {
              return this.cards;
          }
          return this.cards.filter((card) => {
              return card.author === this.selectedAuthorOption;
          })
      }
  },
  created() {
      this.apiCardMusic();
  },
  methods: {
      apiCardMusic() {
          axios.get(this.apiUrl)
          .then((result) => {
              this.contCards = true;
              this.cards = result.data.response;
          })
          .catch ((error) => {
              console.log('Attenzione!! ' + error);
          })
      },
      selectGenreOption(event) {
          this.selectedGenreOption = event.target.value;
          console.log(event.target.value);
      },
      SelectAuthorOption(event) {
          this.selectedAuthorOption = event.target.value;
          console.log(event.target.value);
      }
  }
}
</script>

<style scoped lang="scss">
.container-tracks {
    display: flex;
    flex-wrap: wrap;
    width: 65%;
    margin: 0 auto;
    padding: 0 10px 0 27px;
}

</style>
