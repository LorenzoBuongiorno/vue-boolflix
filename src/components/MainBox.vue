<template>
    <div class="card-box">
        <movie-card  v-for="movie in movies" :key="movie.id" :movie="movie"/>
    </div>
</template>

<script>
import MovieCard from './MovieCard.vue'
export default {
    components: {
        MovieCard
    },
        props: {
        movies: Array
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