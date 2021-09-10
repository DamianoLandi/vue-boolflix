<template>
    <div>
        <input v-model="searchTerm" type="text">
        <button v-on:click="getData">Cerca</button>
    </div>
</template>

<script>
import axios from "axios"

export default {
    name: "Header",
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

<style>

</style>