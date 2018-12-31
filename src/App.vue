<template>
  <div id="app">
    <div class="container">
      <search class="searchComponent" v-on:doSearchRequest="makeQuery"></search>
      <listing v-bind:gifs="gifs"></listing>
    </div>
  </div>
</template>

<script>
  import Search from './components/Search';
  import Listing from './components/Listing';
  export default {
    name: 'app',
    components:{ Search, Listing },
    data() {
      return {
        gifs: []
      }
    },
    methods: {
      makeQuery(query){
        console.log(query);
        this.gifs = [];
        fetch('http://api.giphy.com/v1/gifs/search?q='+query+'&api_key={api_key_here}')
          .then((res) => { return res.json(); })
          .then((res) => { this.gifs = res.data; });
      },
    },
    created() {
      fetch('http://api.giphy.com/v1/gifs/trending?api_key={api_key_here}')
        .then((res) => { return res.json(); })
        .then((res) => { this.gifs = res.data; });
    }
  }
</script>

<style lang="scss">
  @import "./../node_modules/bootstrap/scss/bootstrap.scss";
  .searchComponent{
    margin: 30px 10px;
  }
</style>
