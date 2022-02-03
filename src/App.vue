<template>
  <div id="app">
    <header>
      <input-search @search="filterMovies" />
    </header>
    <main>
      <main-box :movies="movies" />
    </main>
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
#app {

}
</style>
