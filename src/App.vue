<template>
  <div id="app">
    <div class="background">
      <header>
        <h1>BOOLFLIX</h1>
        <input-search @search="filterMoviesTv" />
      </header>
      <main>
        <main-box :movies="movies" :series="series" :populars="populars" :actorsName="actorsName"/>
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
      actorsName: [],
      api_key: '3800b334d89bd3d998f99ccfbfa37575'
      

    }
  },
  mounted () {
      axios.get('https://api.themoviedb.org/3/trending/movie/day?language=it-IT&api_key=3800b334d89bd3d998f99ccfbfa37575').then((element) => {
      this.populars = element.data.results
    });
  },
  methods: {
    //FILTER THE RESULT BY KEYWORD
    filterMoviesTv(keywordSearch) {
      this.populars = [];
      console.log(keywordSearch);
      const params = {
        query: keywordSearch,
        api_key: this.api_key
      }
      //CALL THE API LIST FOR MOVIES
      axios.get('https://api.themoviedb.org/3/search/movie?language=it-IT&' , {params}).then((element) => {
      this.movies = element.data.results
      //ATTEMPT GETTING CAST MEMBERS
      axios.get('https://api.themoviedb.org/3/movie/'+ this.movies.id +'/credits?language=it-IT&api_key=3800b334d89bd3d998f99ccfbfa37575').then((element) => {
        this.actorsName = element.data.cast
      });
    });
    //CALL THE API LIST FOR TV SERIES
    axios.get('https://api.themoviedb.org/3/search/tv?language=it-IT&' , {params}).then((element) => {
      this.series = element.data.results
    });
  }
  }
}
</script>

<style lang="scss">
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
@import 'style/main.scss';
#app{
    background-color: #222;
    .background{
    height: 100vh;
      header{
        background-color: #111;
        h1{
          color: #ff0000;
        }
        padding: 0px 70px;
        height: 80px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    
      }
      main{
        display: flex;
        justify-content: center;
        background-color: #222;
        h1{
          color: #ccc;
          padding: 10px 20px;
        }
      }
    }
}
</style>
