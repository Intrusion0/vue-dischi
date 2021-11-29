<template>
  <div class="container-select-tracks">
      <h3>Seleziona il genere:</h3>
        <select @change="$emit('changeGenre', $event)">
            <option selected>All</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
  </div>
</template>

<script>
export default {
  name: 'SelectGenre'
}
</script>

<style scoped lang="scss">

.container-select-tracks {
    display: flex;
    justify-content: center;
    width: 100%;
    padding-bottom: 90px;

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
