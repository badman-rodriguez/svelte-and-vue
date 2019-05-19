<template>
  <div class="md-layout md-gutter md-alignment-center">
    <card  v-for="(result, index) in results" :key="index" :item="result"> </card>
  </div>
</template>

<style lang="scss" scoped>
  .md-content {
    width: 200px;
    height: 200px;
    display: inline-flex;
    justify-content: center;
    align-items: center;
  }
</style>

<script>
import Card from '@/components/MovieCard.vue';

export default {
  name: 'MovieList',
  components: {
    Card,
  },
  props: {
    results: {
      type: Array,
      default: () => [],
    }
  },
};
</script>
