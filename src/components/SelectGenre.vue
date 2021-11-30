<template>
  <div class="container-select-tracks">
        <select @change="$emit('changeGenre', $event)">
          <option selected disabled>Seleziona genere</option>
            <option>All</option>
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
    justify-content: flex-end;
    width: 100%;

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
