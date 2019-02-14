<template>
  <div id="app" class='container-fluid'>
    <div class='row'>
      <!--note: 'article' represents each individual item in 'articles' object. -->
      <div v-for="article in articles" class='col-4'>
          <h4> {{ article.title }} </h4>
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
      articles: [
        {
         title: "Article 1: Morbi non pretium purus",
         description: "Pellentesque id ex in ligula vestibulum dictum at et lorem. Nam quis ultricies purus, ac interdum sem. Nam porta quis leo id ullamcorper." 
        },
        {
         title: "Article 2: Vestibulum tempus",
         description: "Cras dictum varius diam, at finibus leo varius ac. Aenean et libero" 
        },
        {
         title: "Article 3: Curabitur at odio ligula",
         description: "Etiam sagittis sed diam ac egestas. Ut viverra" 
        },
      ]
    }
  },
  methods: {

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
