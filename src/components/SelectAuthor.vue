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
        color: white;
        text-shadow: 0 0 4px black;
        font-weight: 600;

        option {
            background: #2e3a46;
            color: #fff;
        }
    }
}

</style>
