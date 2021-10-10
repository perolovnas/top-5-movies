<script setup>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
</script>

<template>
  <div class="app-wrapper">
      <div class="wrapper">
        <div class="inner">
          {{result}}
        </div>
      </div>
    <HelloWorld v-if="false" />
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
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=dirty-dancing`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=terminator-2`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=charlie-bartlett`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=the-village`),
      axios.get(`https://www.omdbapi.com/?apikey=8fbe3f08&t=the-two-towers`),
    ])
    .then(response => (this.result = response))
  }
}
</script>

<style lang="scss">
* {
  box-shadow: 0 0 0 1px black;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app-wrapper {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  width: 100%;
  height: auto;
}

.app-wrapper .wrapper {
  width: 100%;
}
</style>
