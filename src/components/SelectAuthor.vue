<template>
  <div class="container-select-author">
        <select @change="$emit('changeAuthor', $event)">
            <option disabled selected>Seleziona Autore</option>
            <option>All</option>
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
    justify-content: flex-end;
    align-items: center;
    margin-left: 30px;

    h3 {
        color: white;
        margin-right: 10px;
    }

    select {  
        background: #18d860;
        min-height: 30px;
        min-width: 150px;
        color: #000000;
        text-shadow: 0 0 4px #ffffff;
        font-weight: 700;
        font-size: 15px;

        option:not([disabled]) {
            color: #fff;
            font-weight: 600;

            &:nth-child(even) {
              background-color: #2e3a46;
            }

            &:nth-child(odd) {
              background-color: #1e2d3b;
            }
        }
    }
}

</style>
