<template>
  <div id="app">
    <RandomQuote  :quotes="quotes" :colors="colors"></RandomQuote>
  </div> 
</template>

<script>

import RandomQuote from './components/RandomQuote.vue'

export default {
  name: 'app',
  components: {
    RandomQuote
  },

    data() {
    return {
      quotes: [],
      colors: ['#8080ff', '#6699ff', '#4dd2ff', '#00e6e6', 
      '#4dffb8', '#ffcc66', '#ff9966', '#ff6666', '#ff80aa', '#99cc00', '#ff1a66', 
      '#ff99ff', '#4d0099', '#4d79ff', '#cc0066', '#e62e00'],
    }
  },

  mounted() {
      this.fetchQuotes()
  },

  methods: {
    fetchQuotes() {
      fetch('/quotes.json')
      .then(res => res.json())
      .then(data => this.quotes = data)
      .catch(error => console.error(error))
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Noto+Sans&display=swap');


#app {
  font-family: 'Noto Sans', sans-serif;
}

body {
  background: url('/crumpled.jpg');
  background-size: cover;
}

</style>
