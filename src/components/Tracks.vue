<template>
  <div class="container-tracks">
    <!-- Componente Loader -->
    <Loader v-if="contCards == false" />
    <!-- Componente CardTrack -->
    <CardTrack
      v-else
      v-for="(card, i) in filteredCards"
      :key="i"
      :details="card"
    />
  </div>
</template>

<script>
import axios from "axios";
import CardTrack from "./CardTrack.vue";
import Loader from "./Loader.vue";

export default {
  name: "Traks",
  components: {
    CardTrack,
    Loader
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      cards: [],
      contCards: false
    }
  },
  props: {
    selectedGenreOption: String,
    selectedAuthorOption: String
  },
  computed: {
    filteredCards() {
      let filteredCards = this.cards;

      if (this.selectedGenreOption !== "All") {
        filteredCards = filteredCards.filter((card) => {
          return card.genre === this.selectedGenreOption;
        });
      }
      if (this.selectedAuthorOption !== "All") {
        filteredCards = filteredCards.filter((card) => {
          return card.author === this.selectedAuthorOption;
        });
      }
      return filteredCards;
    }
  },
  created() {
    this.apiCardMusic();
  },
  methods: {
    apiCardMusic() {
      axios
        .get(this.apiUrl)
        .then((result) => {
          this.contCards = true;
          this.cards = result.data.response;
          this.$emit('tracks', this.filteredCards);
        })
        .catch((error) => {
          console.log("Attenzione!! " + error);
        });
    }
  }
};
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
