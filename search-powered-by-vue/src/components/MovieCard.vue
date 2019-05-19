<template>
  <div>
    <md-card md-with-hover>
      <md-ripple>
        <md-card-media>
          <img :src="item.Poster">
        </md-card-media>
        <md-card-header>
          <div class="md-title">{{item.Title}}</div>
          <div class="md-subhead">{{item.Type}} - {{item.Year}}</div>
        </md-card-header>
        <md-card-actions>
          <a :href="externalUrl" target="_blank">Amazon search</a>
        </md-card-actions>
      </md-ripple>
    </md-card>
  </div>
</template>

<script>
export default {
  name: 'MovieCard',
  props: {
    item: Object
  },
  mounted() {
    console.log(this.item);
  },
  computed: {
    externalUrl () {
      return `https://www.amazon.com/s?i=movies-tv&k=${this.item.Title}`;
    }
  }
};
</script>


<style lang="scss" scoped>
  .md-card {
    width: 320px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
</style>
