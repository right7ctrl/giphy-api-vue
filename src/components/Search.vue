<template>
  <div class="container m_top30">

    <div class="row">
      <div class="col-md-8">
        <input class="form-control" v-model='query' v-on:keypress.enter="searchRequest" placeholder="Type something and hit enter" type="text">
      </div>
      <div class="col-md-4">
        <button @click="searchRequest" class="btn btn-success btn-full-width">Search</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Search",
    data() {
      return {
        query: '',
      }
    },

    methods: {
      searchRequest(){
        this.$emit('doSearchRequest', this.query);
      }
    }
  }
</script>

<style scoped>
  .m_top30 {
    margin-top: 30px;
  }
  button.btn-full-width{
    width: 100%;
  }
</style>
