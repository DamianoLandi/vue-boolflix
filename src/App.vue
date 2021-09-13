<template>
  <div id="app">
    <nav>
      <input v-model="searchTerm" type="text">
      <button v-on:click="getData">Cerca</button>
    </nav>
    <MainContent :lists="lists"/>  
  </div>
</template>

<script>
import axios from "axios"

import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    MainContent
  },
      data(){
        return{
            searchTerm: "",
            key: "api_key=6bdd58982188b8c812708db73b34338e",
            lang: "&language=it_IT",
            moviesList: null,
            tvList: null,
        }
    },

    computed: {
        query(){
            return `&query=${this.searchTerm}` 
        },

        lists(){
          return [
            this.moviesList,
            this.tvList
          ]
        }
    },

    methods: {
        getData(){
            axios
            .get(`https://api.themoviedb.org/3/search/movie?${this.key}${this.lang}${this.query}`)
            .then((res) => {
                const response = res.data.results;
                this.moviesList = response;
            });

            axios
            .get(`https://api.themoviedb.org/3/search/tv?${this.key}${this.lang}${this.query}`)
            .then((res) => {
                const response = res.data.results;
                this.tvList = response;
            });

            this.searchTerm = "";
        }
    }
}
</script>

<style lang="scss">

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

nav{
  text-align: center;
}
</style>
