<template>
  <div class="md-layout custom-input-class">
    <md-field>
      <label>Search for a movie:</label>
      <md-input v-model="initial" class=""></md-input>
    </md-field>
    <div>
      <md-button class="md-raised md-primary" v-on:click="search">Find a Movie</md-button>
    </div>
    <div>
      <md-radio v-model="searchType" value="title">By Title <small>(Default)</small></md-radio>
      <md-radio v-model="searchType" value="id">By ID</md-radio>
    </div>
  </div>
</template>
<script>
export default {
  name: 'search-input',
  data: () => ({
    initial: '',
    searchType: 'title',
  }),
  props: {
    searchByTextFn: Function,
    searchByIdFn: Function, 
  },
  methods: {
    search() {
      if(this.searchType === 'title') {
        this.searchByTextFn(this.initial).then(resp => this.$emit('on-search', resp));
      } else {
        this.searchByIdFn(this.initial).then(resp => this.$emit('on-search', resp));
      }
    }
  }
};
</script>
<style>
  .custom-input-class {
    width: 50%;
    margin: 0 auto;
  }
</style>
