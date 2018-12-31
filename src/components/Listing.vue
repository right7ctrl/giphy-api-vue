<template>
  <ul class="gif-list">
    <div class="row">
      <li class="gif-item col-md-3" v-for="gif in gifs">
        <img v-bind:src="gif.images.fixed_height_still.url" alt="">
      </li>
    </div>
  </ul>
</template>

<script>
  export default {
    name: "Listing",
    props: ["gifs"]
  }
</script>

<style scoped>
  ul.gif-list {
    list-style: none;
  }

  li.gif-item {
    float: left;
  }

  div.gif-box {
    padding: 10px;
    border-right: 1px solid #ccc;
    border-radius: 5px;
  }
</style>
