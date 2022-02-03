<template>
    <div>
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

</style>