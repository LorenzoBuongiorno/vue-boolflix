<template>
    <div class="card">
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
                <span>Voto:</span>
                {{movie.vote_average}}
            </div>
        </div>
        <img class="poster-image" :src="'https://image.tmdb.org/t/p/original' + movie.poster_path" alt="">
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
            }
    }
}
</script>

<style lang="scss">
@import '@/style/cards.scss'
</style>