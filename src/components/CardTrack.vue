<template>
  <div class="card-track">
      <img :src="details.poster" :alt="details.title">
      <h2>{{details.title.toUpperCase()}}</h2>
      <span>{{details.author}}</span>
      <span>{{details.year}}</span>
  </div>
</template>

<script>
export default {
  name: 'cardTrack',
  props: {
      details: Object
  }
}
</script>

<style scoped lang="scss">
$card-background-color: #2e3a46;
$title-card-color: #fff;
$text-card-color: #808080;

.card-track {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: calc(20% - 40px);
    background-color: $card-background-color;
    margin: 0 20px 20px;
    padding-top: 20px;

    img {
        width: 80%;
    }

    h2 {
        color: $title-card-color;
        text-align: center;
        margin: 20px 0 25px;
    }

    span {
        color: $text-card-color;
        font-weight: 500;
        font-size: 18px;
    }

    span:last-child {
        margin-bottom: 15px;
    }
}
</style>
