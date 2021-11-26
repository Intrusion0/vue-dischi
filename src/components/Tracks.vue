<template>
  <div class="container-tracks">
      <CardTrack v-for="card, i in cards" :key="i"
      :details="card"
      />
  </div>
</template>

<script>
import axios from 'axios'
import CardTrack from './CardTrack.vue'

export default {
  name: 'Traks',
  components: {
      CardTrack
  },
  data() {
      return {
          apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
          cards: []
      }
  },
  created() {
      this.apiCardMusic();
  },
  methods: {
      apiCardMusic() {
          axios .get(this.apiUrl)
          .then ((result) => {
              this.cards = result.data.response;
          })
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
    padding-left: 30px;
}
</style>
