<template>
    <div class="movie-card">
        <div class="description">
            <div>
                <span>Titolo:</span>
                {{movie.title}}
            </div>
            <div>
                <span>Titolo Originale:</span>
                {{movie.original_title}}
            </div>
            <div>
                <span>Lingua:</span>
                <img class="language-image" :src="'/flags/' + movie.original_language + '.png'" alt=""  @load="loadImage">
                <span v-if="!isLoaded">{{movie.original_language}}</span>
            </div>
            <div>
                <span>Voto: </span>
                <span class="stars" v-for="n in Math.ceil(scale(movie.vote_average))" :key="n"><i class="fas fa-star"></i></span>
            </div>
        </div>
        <a href="#">
            <img class="poster-image" :src="'https://image.tmdb.org/t/p/w500/' + movie.poster_path " alt="">
        </a>
    </div>
</template>

<script>
export default {
    props:{
        movie:Object
    },
    data() {
        return {
            isLoaded: false
        }
    },
    methods: {
        loadImage() {
                this.isLoaded = true;
            },
            scale (number) {
    return (number - 0) * (5 - 0) / (10 - 0) + 0;
            },


    }
}
</script>

<style lang="scss">
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
@import '@/style/MovieCards.scss'
</style>