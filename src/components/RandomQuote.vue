<template>
  <div>
    <h1 id="heading">Random Quotes</h1>
    <div id="quoteBox" :style="{'background-color': color}" :class="fadeClass"> 
      <p class="quoteMarks">"<span class="quoteText">{{ quote.quote }}</span>"</p>
      <p><em>A Quote by - {{ quote.author }}</em></p>
    </div>
    <div id="btn-container"> <button @click="newQuote(); newColor();" id="btn">New Quote</button> </div>

  </div>
</template>



<script>
export default {
  name: 'RandomQuote',

  props: {
    quotes: {
      type: Array,
      required: true
    },
    colors: {
      type: Array,
      required: true
    }
  }, 

  data() {
    return {
      quote: '',
      color: '#8080ff',
      fadeClass: 'fade',
    }
  },

  methods: {
    newQuote() {
      this.quote = this.quotes[Math.floor(Math.random() * (this.quotes.length))];
    },
    newColor() {
      this.color = this.colors[Math.floor(Math.random() * (this.colors.length))];
    }
  },

    mounted() {
      setTimeout(() => {
        this.newQuote()
        this.newColor()
      }, 1000);
  }

}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  #heading {
    color: rgb(39, 95, 151);
    text-align: center;
    letter-spacing: 5px;
  }

  #quoteBox {
    margin: 30px auto;
    min-height: 250px;
    max-width: 600px;
    font-family: 'Noto Sans', sans-serif;
    color: white;
    text-align: center;
    padding: 40px;
  }

  #btn-container {
    display: flex;
    justify-content: center;
  }

  #btn {
    width: 200px;
    height: 50px;
    background: rgb(39, 95, 151);
    color: white;
    font-size: 17px;
    cursor: pointer;
    border: none;
    text-decoration: none;
  }

  #btn:hover {
    background: rgb(24, 60, 95);
    transition: all 0.4s ease;
  }

  .fade {
    transition: all 0.5s ease;
  }

  .quoteMarks {
    font-size: 30px;
    line-height: 1.1;
  }

  .quoteText {
    font-size: 18px;
  }


</style>
