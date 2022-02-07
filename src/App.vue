<template>
  <div id="app">
    <div class="background">
      <header>
        <input-search @search="filterMoviesTv" />
      </header>
      <main>
        <main-box :movies="movies" :series="series" :populars="populars"/>
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
      series: [],
      populars: [],
      api_key: '3800b334d89bd3d998f99ccfbfa37575'
      

    }
  },
  mounted () {
      axios.get('https://api.themoviedb.org/3/trending/movie/day?language=it-IT&api_key=3800b334d89bd3d998f99ccfbfa37575').then((element) => {
      this.populars = element.data.results
    });
  },
  methods: {
    filterMoviesTv(keywordSearch) {
      console.log(keywordSearch);
      const params = {
        query: keywordSearch,
        api_key: this.api_key
      }
      axios.get('https://api.themoviedb.org/3/search/movie?language=it-IT&' , {params}).then((element) => {
      this.movies = element.data.results
    });
    axios.get('https://api.themoviedb.org/3/search/tv?language=it-IT&' , {params}).then((element) => {
      this.series = element.data.results
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
