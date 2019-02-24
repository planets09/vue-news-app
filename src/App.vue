<template>
  <div id="app" class='container-fluid'>

    <div class='row'>
      <input type='text' placeholder='SEARCH'
      v-model='searchQuery'>
      <!-- <p>{{ seachQuery }}</p> -->
      <button v-on:click='getNews'>SUBMIT</button>
    </div>

    <div class='row'>
      <app-article v-for="newsArticle in articles"
      v-bind:data='newsArticle'></app-article>
     
    </div>
  </div>

</template>

<!-- ________________________________________________________ -->

<script>

import Article from "./components/Article.vue";

export default {
  data: function() {
    return {
      articles: [],
      searchQuery: "world news"
    }
  },
  methods: {
   getNews: function(){
    var that = this;
    var url = 'https://newsapi.org/v2/everything?' +
          // 'country=us&' +
          'q=' + this.searchQuery + '&' + 
          'apiKey=57e7cd5efcd041d8977efdfa1d1e4059';
    var req = new Request(url);
    fetch(req)
        .then(function(response) {
          return response.json();
        })
        .then(function(data){
          // console.log(data);
          that.articles = data.articles;
        })
        this.searchQuery = '';
   }
  },
  components: {
    'app-article': Article
  },
  mounted: function(){
    this.getNews()
      }
}
</script>

<!-- ________________________________________________________ -->

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
