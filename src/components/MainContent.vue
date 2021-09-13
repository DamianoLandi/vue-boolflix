<template>
    <div class="cards-container">
        <div v-for="(list, index) in lists" :key="index" class="card-container">
            <Card :list="list"/>
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
        display: flex;
        justify-content: space-around;
    }

    .card-container{
        width: 20%;
    }
</style>