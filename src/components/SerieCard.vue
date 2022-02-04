<template>
    <div class="serie-card">
        <div class="cover"></div>
        <div class="description">
            <div>
                <span>Titolo:</span>
                {{serie.name}}
            </div>
            <div>
                <span>Titolo Originale:</span>
                {{serie.original_name}}
            </div>
            <div>
                <span>Lingua:</span>
                <img class="language-image" :src="'/flags/' + serie.original_language + '.png'" alt=""  @load="loadImage">
                <span v-if="!isLoaded">{{serie.original_language}}</span>
            </div>
            <div>
                <span>Voto: </span>
                <span class="stars" v-for="n in Math.ceil(scale(serie.vote_average))" :key="n"><i class="fas fa-star"></i></span>

            </div>
        </div>
        <img class="poster-image" :src="'https://image.tmdb.org/t/p/w342/' + serie.backdrop_path " alt="">
    </div>
</template>

<script>
export default {
    props:{
        serie:Object
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
@import '@/style/SerieCards.scss'
</style>