<template>
  <div id="app" class='container-fluid'>

    <div class='row'>
      <app-search v-on:newsChanged="getNews"></app-search>
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
import Search from "./components/Search.vue";

export default {
  data: function() {
    return {
      articles: [],
      searchQuery: "world news"
    }
  },
  methods: {
   getNews: function(query){
    var that = this;
    var url = 'https://newsapi.org/v2/everything?' +
          // 'country=us&' +
          'q=' + query + '&' + 
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
    'app-article': Article,
    'app-search': Search
  },
  mounted: function(){
    this.getNews(this.searchQuery)
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
