<template>
    <div class="movie-card">
        <div class="cover"></div>
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
                <!-- PRINT FLAG IMAGE OR THE LANGUAGE WORD -->
                <img class="language-image" :src="'/flags/' + movie.original_language + '.png'" alt=""  @load="loadImage">
                <span v-if="!isLoaded">{{movie.original_language}}</span>
            </div>
            <div>
                <span>Voto: </span>
                <!-- PRINT STARS FOR EACH VOTE NUMBER  -->
                <span class="stars" v-for="n in Math.ceil(scale(movie.vote_average))" :key="n"><i class="fas fa-star"></i></span>
            </div>
            <div>
                <span>Actors:</span>
                <div>
                    <div v-for="actorName in actorsName" :key="actorName.id">
                        {{actorName.name}}
                    </div>
                </div>
            </div>

        </div>
        <img class="poster-image" :src="'https://image.tmdb.org/t/p/w342/' + movie.poster_path " alt="">
    </div>
</template>

<script>

export default {
    props:{
        movie: Object,
        actorsName: Array
    },
    data() {
        return {
            isLoaded: false,

        }
    },
    methods: {
        loadImage() {
                this.isLoaded = true;
            },
            //SCALE VOTE FROM 1, 10 TO 1,5
            scale (number) {
                return (number - 0) * (5 - 0) / (10 - 0) + 0;
            }
    }
}
</script>

<style lang="scss">
@import '@/style/MovieCards.scss'
</style>