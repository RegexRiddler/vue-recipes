<template>
  <div id="app">
    <Recipes 
      :thumbnail="recipes[index].thumbnail"
      :title="recipes[index].title"
      :ingredients="recipes[index].ingredients"
      :url="recipes[index].href"
    />
  </div>
</template>

<script>
import Recipes from './components/Recipes.vue'
import { constants } from 'fs';

export default {
  name: 'app',
  components: {
    Recipes
  },
  props: {

  },
  data() {
    return {
      recipes: [],
      index: 0
    }
  },
  beforeMount: function () {
    const conversionUrl = "https://corsanywhereproxy.herokuapp.com/";
    const recipeApi = "http://www.recipepuppy.com/api/";

    fetch(conversionUrl + recipeApi)
      .then(res => res.json())
      .then(data =>{
        this.recipes = data.results;
      })
  }
}
</script>

<style lang="sass">
  *
    box-sizing: border-box
    
  body
   background-color: #2A5362

  #app
    font-family: 'Avenir', Helvetica, Arial, sans-serif
    -webkit-font-smoothing: antialiased
    -moz-osx-font-smoothing: grayscale
    text-align: center
    color: #1F1F1F
    margin-top: 60px
</style>
