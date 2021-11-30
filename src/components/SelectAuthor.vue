<template>
  <div class="container-select-author">
      <h3>Seleziona l'autore:</h3>
        <select @change="$emit('changeAuthor', $event)">
            <option selected>All</option>
            <option v-for="author, i in details" 
            :key="i" 
            :value="author.author"
            >{{ author.author }}</option>
        </select>
  </div>
</template>

<script>
export default {
  name: 'SelectAuthor',
  props: {
      details: Array
  }
}
</script>

<style scoped lang="scss">

.container-select-author {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;

    h3 {
        color: white;
        margin-right: 10px;
    }

    select option {
        background: #2e3a46;
        color: #fff;
    }
}

</style>
