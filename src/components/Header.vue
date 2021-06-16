<template>
  <div class="header">
      <img src="../assets/spotify.png" alt="spotify-logo">
      <select
        v-model="selectedGenre"
        @change="$emit('changedGenre', selectedGenre)"
      >
       <option value="">seleziona un genere</option>   
       <option
        v-for="(genre, index) in genres"
        :key="index"
        :value="genre">
        {{ genre }}
       </option>
      </select>
  </div>
</template>

<script>
export default {
    name: "Header",

    data: function() {
        return {
            selectedGenre:''
        }
    },

    props: {
        "genres": Array
    }
}
</script>

<style lang="scss" scoped>
.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 70px;
    width: 100%;
    background-color: #2e3a46;

    img {
        max-height: 60px;
    }
}
</style>