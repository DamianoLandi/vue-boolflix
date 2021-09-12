<template>
    <div>
        <div v-for="(list, index) in lists" :key="index">
            <ul>
                <li v-for="(movie, index) in list" :key="index">
                    <p v-if="movie.title">Titolo: {{movie.title}}</p>
                    <p v-else>Titolo: {{movie.name}}</p>
                    <p v-if="movie.title">Titolo Originale: {{movie.original_title}}</p>
                    <p v-else>Titolo Originale: {{movie.original_name}}</p>
                    <p>Lingua Originale: {{movie.original_language}}</p>
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