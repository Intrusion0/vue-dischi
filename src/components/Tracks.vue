<template>
  <div class="container-tracks">
      <!-- Componente Selected -->
      <SelectGenre @changeGenre="selectOption"/>
      <!-- Componente Loader -->
      <Loader v-if="contCards == false"/>
      <!-- Componente CardTrack -->
      <CardTrack v-else v-for="card, i in filteredCards" :key="i"
      :details="card"
      />
  </div>
</template>

<script>
import axios from 'axios'
import CardTrack from './CardTrack.vue'
import Loader from './Loader.vue'
import SelectGenre from './SelectGenre.vue'

export default {
  name: 'Traks',
  components: {
      CardTrack,
      Loader,
      SelectGenre
  },
  data() {
      return {
          apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
          cards: [],
          contCards: false,
          selectedOption: 'All',
      }
  },
  computed: {
      filteredCards() {
          if (this.selectedOption == 'All') {
              return this.cards;
          }
          return this.cards.filter((card) => {
              return card.genre === this.selectedOption;
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
      selectOption(event) {
          this.selectedOption = event.target.value;
          console.log(event.target.value);
      },
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
