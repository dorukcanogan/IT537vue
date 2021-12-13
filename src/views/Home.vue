<template>
  <div id="app">
    <navbar :handleRequest="handleRequest"></navbar>
    <b-container class="bv-example-row">
      <b-row>
        <b-col>
          <h4 class="baslık">Öne Çıkan Haberler</h4>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <carousel></carousel>
        </b-col>
      </b-row>
      <b-row class="text-center">
        <b-col>
          <topheadlines class="view" :topheadlines=topheadlines></topheadlines>
        </b-col>
      </b-row>
    </b-container>
    <Footer :text="['center', 'lg-start']">
    </Footer>
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
import topheadlines from '../components/topheadlines.vue'
import Footer from '../components/Footer.vue'
import carousel from '../components/carousel.vue'

export default {
  name: 'App',
  components: {
    Navbar,topheadlines,Footer,carousel
  },
  data() {
    return {
      gifs:[],
      topheadlines:[],
      apikey:'a1b7ccaf7ffe425caa0f9f0253fe1a29'
    }
  },
  methods: {
    handleRequest(query){
    this.topheadlines = []; 
    const url = `https://newsapi.org/v2/top-headlines?country=${query}&apiKey=098ba3055806413080e3a055f8e8c17b`;
    fetch(url)
    .then((response) => {return response.json()})
    .then((response) => {
      this.topheadlines = response.articles;
    })
    }
  },
  created() {
    const url = 'https://newsapi.org/v2/top-headlines?country=tr&pageSize=32&apiKey=098ba3055806413080e3a055f8e8c17b';
    fetch(url)
    .then((response) => {return response.json()})
    .then((response) => {
      this.topheadlines = response.articles;
    })

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.baslık{
  margin-top:1%;
  float:left;

}
</style>
