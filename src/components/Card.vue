<template>
    <div class="cards-container">
        <div v-for="(movie, index) in list" :key="index" class="card-bg">
            <img  :src="movie.poster_path ? imgUrl + movie.poster_path : 'https://www.altavod.com/assets/images/poster-placeholder.png'" alt="Poster" class="poster">
            <div class="card-info">
                <p v-if="movie.title">Titolo: {{movie.title}}</p>
                <p v-else>Titolo: {{movie.name}}</p>
                <p v-if="movie.title">Titolo Originale: {{movie.original_title}}</p>
                <p v-else>Titolo Originale: {{movie.original_name}}</p>
                <div>Lingua Originale: <img v-if="movie.original_language === 'en'" src="@/assets/img/en.png" alt="EN" class="lang"> <img v-if="movie.original_language === 'it'" src="@/assets/img/it.png" alt="it" class="lang"> <span v-if="movie.original_language != 'en' && movie.original_language != 'it'">{{movie.original_language}}</span></div>
                <p>Voto: <span v-for="num in adaptNumber(movie.vote_average)" :key="num"><i class="fas fa-star"></i></span><span v-for="num in (5 - adaptNumber(movie.vote_average))" :key= "num"><i class="far fa-star"></i></span></p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: [
        "list",
    ],
    data(){
        return{
            imgUrl: "https://image.tmdb.org/t/p/w342",
        }
    },
    methods: {
        adaptNumber(num){
            let newNum = num/2;
            return Math.ceil(newNum)
        }
    }
}
</script>

<style>
    .cards-container{
        display: flex;
        max-width: 75vw;
        margin: auto;
        flex-wrap: wrap;
        justify-content: space-around;
    }

    .card-bg{
        padding: 20px;
        height: 400px;
        width: 300px;
        position: relative;
        margin-bottom: 30px;
    }
    
    .poster{
        height: 100%;
        width: 100%;
    }

    .card-info{
        opacity: 0;
        background-color: gray;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 1;
        height: 100%;
        width: 100%;
        overflow-y: scroll;
        text-align: center;
    }

    .card-info:hover{
        opacity: 1;
    }

    .lang{
        height: 50px;
        widows: 100px;
    }
</style>