<template>
  <div id="app">
    <Recipes 
      :thumbnail="recipes[index].thumbnail"
      :title="recipes[index].title"
      :ingredients="recipes[index].ingredients"
      :url="recipes[index].href"
      :recipeNumber="index + 1"
      :numberOfRecipes="recipes.length"
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
  body
    min-height: 100vh
    margin: 0
    background-image: linear-gradient(to bottom right, #FDC000, #89B859)
    background-repeat: no-repeat
    background-size: cover
</style>
