<template>
<div>
    <h1>Movies</h1>
    <div class="card-box">
        <movie-card  v-for="movie in movies" :key="movie.id" :movie="movie"/>
    </div>
    <h1>Tv Series</h1>
    <div class="card-box">
        <serie-card  v-for="serie in series" :key="serie.id" :serie="serie"/>
    </div>
</div>
</template>

<script>
import MovieCard from './MovieCard.vue'
import SerieCard from './SerieCard.vue'
export default {
    components: {
        MovieCard,
        SerieCard
    },
        props: {
        movies: Array,
        series: Array
    }
}
</script>

<style lang="scss">
.card-box{
    width: 1500px;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}
</style>