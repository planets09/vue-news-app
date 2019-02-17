<template>
  <div id="app" class='container-fluid'>
    <div class='row'>
      <!--note: 'article' represents each individual item in 'articles' object. -->
      <div v-for="article in articles" class="col-4">
          <img v-bind:src="article.urlToImage" v-bind:alt='article.description' class="img-fluid">
          <h4> {{ article.title }} </h4>
          <h6>{{ article.author }} | {{article.source.name }}</h6>
          <p> {{ article.description }}</p>
    
        </div>
    
      </div>
    </div>

</template>

<!-- ________________________________________________________ -->

<script>

// import HelloWorld from './components/HelloWorld.vue'

export default {
  data: function() {
    return {
      articles: []
    }
  },
  mounted: function(){
    var that = this;
    var url = 'https://newsapi.org/v2/top-headlines?' +
          'country=us&' +
          'apiKey=57e7cd5efcd041d8977efdfa1d1e4059';
    var req = new Request(url);
    fetch(req)
        .then(function(response) {
          return response.json();
        })
        .then(function(data){
          console.log(data);
          that.articles = data.articles;
        })
      },
  components: {
    // appHello: HelloWorld
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
