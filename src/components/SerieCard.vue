<template>
    <div class="serie-card">
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
                <span>Voto:</span>
                {{serie.vote_average}}
            </div>
        </div>
        <img class="poster-image" :src="'https://image.tmdb.org/t/p/original' + serie.backdrop_path " alt="">
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
            }
    }
}
</script>

<style lang="scss">
@import '@/style/SerieCards.scss'
</style>