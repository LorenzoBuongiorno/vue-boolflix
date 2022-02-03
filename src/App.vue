<template>
  <div id="app">
    <div class="background">
      <header>
        <input-search @search="filterMovies" />
      </header>
      <main>
        <main-box :movies="movies" />
      </main>
    </div>
  </div>
</template>

<script>
import InputSearch from './components/InputSearch.vue'
import MainBox from './components/MainBox.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    InputSearch,
    MainBox

  },
  data () {
    return {
      movies: [],
      

    }
  },
  methods: {
    filterMovies(keywordSearch) {
      console.log(keywordSearch);
      axios.get('https://api.themoviedb.org/3/search/movie?language=it-IT&api_key=3800b334d89bd3d998f99ccfbfa37575&query=' + keywordSearch).then((element) => {
      this.movies = element.data.results
    })
  }
  }
}
</script>

<style lang="scss">
@import 'style/main.scss';
#app{
    background-color: #333;
    .background{
    background-color: #333;
    height: 100vh;
      header{
        background-color: #111;
        height: 80px;
        display: flex;
        justify-content: end;
        align-items: center;
    
      }
      main{
        display: flex;
        justify-content: center;
        background-color: #333;
      }
    }
}
</style>
