<template>
  <div id="app">
    <Header :genres="allGenres" @changedGenre="updatedGenre" />

    <Main @genresReady="setGenres" :selectedGenre="currentGenre" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',

  data: function() {
    return {
      allGenres: [],
      currentGenre: []
    }
  },

  methods: {
    setGenres: function(array) {
      this.allGenres = array;
    },

    updatedGenre:function(newGenre) {
      this.currentGenre = newGenre;
    }
  },

  components: {
    Header,
    Main
  }
}
</script>

<style lang="scss">

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

</style>
