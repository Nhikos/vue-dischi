<template>
  <div v-if="!loading" class="main">
      <div class="wrap">
          <div 
          class="container"
          v-for="(card, index) in filteredCard"
          :key= "index">
              <Card :item="card" />
          </div>
      </div>
  </div>
  <Loader message="Loading..." v-else />
</template>

<script>
import Card from './Card'
import Loader from './Loader'
import axios from 'axios';

export default {
    name: "Main",

    props: {
        selectedGenre: Array
    },

    components: {
        Card,
        Loader
    },
    data: function () {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            cards: [],
            genres: [],
            loading: true
        }
    },
    created: function () {
        axios
            .get(this.apiUrl)
            .then(
                (results) => {
                    console.log(results.data);
                    this.cards = results.data.response;
                    console.log(this.cards);
                    
                    this.cards.forEach(
                        (element) =>{
                            if(!this.genres.includes(element.genre)) {
                                this.genres.push(element.genre);
                            }
                        }
                    );

                    this.$emit('genresReady', this.genres)
                    this.loading = false;
                }
            )
            .catch();
    },
    computed: {
        filteredCard: function() {
            if(this.selectedGenre == "") {
                return this.cards;
            }
            return this.cards.filter(
                element => element.genre == this.selectedGenre
            )
        }
    }
}
</script>

<style>
.main {
    height: calc(100vh - 70px);
    background-color: #1e2d3b;
    }

.wrap {
    display: flex;
    flex-wrap: wrap;
    align-content: space-around;
    justify-content: space-around;
    width: 70%;
    height: 100%;
    margin: 0 auto;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 360px;
    width: 200px;
    margin: 0px 20px;
    background-color: #2e3a46;
}
</style>