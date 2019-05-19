<template>
  <div class="home">
    <header>
      <img alt="Vue logo" src="../assets/logo.png">
      <search-input 
        :searchByTextFn="searchByTitle"
        :searchByIdFn="searchById"
        @on-search="assignResults"
      ></search-input>
    </header>
    <main class="custom-main-class">
      <movie-list :results="results"></movie-list>
    </main>
</div>
</template>

<script>
// @ is an alias to /src
import 'whatwg-fetch';
import MovieList from '@/components/MovieList.vue';
import SearchInput from '@/components/SearchInput.vue';

export default {
  name: 'home',
  components: {
    MovieList,
    SearchInput,
  },
  data: () => ({
    results: [],
  }),
  methods: {
    searchByTitle(title) {
      return fetch(`http://www.omdbapi.com/?apikey=17c6ef7d&s=${title}`).then(resp => resp.json())
    },
    searchById(id) {
      return fetch(`http://www.omdbapi.com/?apikey=17c6ef7d&i=${id}`).then(resp => resp.json())
    },
    assignResults(resp) {
      this.results = resp ? resp.Search : []
    }
  }
};
</script>

<style>
  .custom-main-class {
    margin: 0 auto;
  }
</style>

