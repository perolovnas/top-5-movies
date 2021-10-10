<script setup>
import BaseSection from './components/BaseSection.vue'
import axios from 'axios'
</script>

<template>
  <div class="app-wrapper">
      <div class="wrapper">
        <div class="inner">
          <BaseSection
            v-for="(results, i) in result" :key="i"
            :Index="i+1"
            :Poster="results.data.Poster"
            :Title="results.data.Title"
            :Ratings="results.data.Ratings"
            :Plot="results.data.Plot"
            :Rated="results.data.Rated"
            :Genre="results.data.Genre"
            :Actors="results.data.Actors"
            :Director="results.data.Director"
            :Runtime="results.data.Runtime"
            :Released="results.data.Released"
          />
        </div>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: null
    }
  },
  mounted () {
    axios.all([
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=the-two-towers`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=terminator-2`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=dirty-dancing`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=charlie-bartlett`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=the-village`),
    ])
    .then(response => (this.result = response))
  }
}
</script>

<style lang="scss">
* {
  // box-shadow: 0 0 0 1px black;
  // margin: 0;
  // padding: 0;
  box-sizing: border-box;
}

.app-wrapper {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  width: 100%;
  height: auto;

  .wrapper {
    width: 100%;
  }
}

</style>
