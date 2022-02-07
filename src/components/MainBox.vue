<template>
<div>
    <div v-if="movies == 0 && series == 0">
        <h1>Popular</h1>
        <div class="card-box">
            <popular-card  v-for="popular in populars" :key="popular.id" :popular="popular"/>
        </div>
    </div>
    <div v-if="populars == 0 && movies != 0">
        <h1>Movies</h1>
        <div class="card-box">
            <movie-card  v-for="movie in movies" :key="movie.id" :movie="movie" :actorsName="actorsName"/>
        </div>
    </div>
    <div v-if="populars == 0 && series != 0">
        <h1>Tv Series</h1>
        <div class="card-box">
            <serie-card  v-for="serie in series" :key="serie.id" :serie="serie"/>
        </div>
    </div>
</div>
</template>

<script>
import MovieCard from './MovieCard.vue'
import PopularCard from './PopularCard.vue'
import SerieCard from './SerieCard.vue'
export default {
    components: {
        MovieCard,
        SerieCard,
        PopularCard,
    },
        props: {
        movies: Array,
        series: Array,
        populars: Array,
        actorsName: Array
    }
}
</script>

<style lang="scss">
.card-box{
    width: 80vw;
    overflow: scroll;
    white-space:nowrap;
    overflow-y: hidden;
    &::-webkit-scrollbar {
        height: 15px;
    }
    &::-webkit-scrollbar-track {
        box-shadow: inset 0 0 5px #444; 
        border-radius: 10px;
    }
    &::-webkit-scrollbar-thumb {
        background: #555; 
        border-radius: 10px;
    }

}
</style>