<template>
    <div>
        <div v-for="(list, index) in lists" :key="index">
            <ul>
                <li v-for="(movie, index) in list" :key="index">
                    <p v-if="movie.title">Titolo: {{movie.title}}</p>
                    <p v-else>Titolo: {{movie.name}}</p>
                    <p v-if="movie.title">Titolo Originale: {{movie.original_title}}</p>
                    <p v-else>Titolo Originale: {{movie.original_name}}</p>
                    <div>Lingua Originale: <img v-if="movie.original_language === 'en'" src="@/assets/img/en.png" alt="EN"> <img v-if="movie.original_language === 'it'" src="@/assets/img/it.png" alt="it"> <span v-if="movie.original_language != 'en' && movie.original_language != 'it'">{{movie.original_language}}</span></div>
                    <p>Voto: {{movie.vote_average}}</p>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "MainContent",
    props:["lists",]
}
</script>

<style>

</style>