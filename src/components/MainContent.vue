<template>
    <div class="cards-container">
        <div v-for="(list, index) in lists" :key="index" class="main-container">
            <div class="title-container" v-if="list != null">
                <h2 v-if="index === 0">Film</h2>
                <h2 v-else>Serie TV</h2>
            </div>
            <div class="card-container">
                <Card :list="list"/>
            </div>
        </div>
    </div>
</template>

<script>
import Card from "@/components/Card.vue"

export default {
    name: "MainContent",
    components: {
        Card,
    },
    props:["lists",]
}
</script>

<style>
    .cards-container{
        background-color: rgb(138, 136, 136);
        min-height: calc(100vh - 100px);
    }

    .card-container{
        display: flex;
        justify-content: space-around;
        position: relative;
    }

    h2{
        text-align: center;
        margin: 40px auto;
        color: rgb(172, 7, 7);
        text-transform: uppercase;
        font-size: 35px;
    }
</style>