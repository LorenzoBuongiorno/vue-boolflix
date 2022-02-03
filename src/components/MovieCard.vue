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
                <span>lingua:</span>
                {{movie.original_language}}
            </div>
            <div>
                <span>Voto:</span>
                {{movie.vote_average}}
            </div>
        </div>
        <img :src="'https://image.tmdb.org/t/p/original' + movie.poster_path" alt="">
    </div>
</template>

<script>
export default {
    props:{
        movie:Object
    }
}
</script>

<style lang="scss">
@import '@/style/cards.scss'
</style>