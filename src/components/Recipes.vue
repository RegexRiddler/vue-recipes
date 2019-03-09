<template>
  <div class="recipes-root">
    <div class="[ container ]">
      <div class="[ row ]">
        <div class="[ col-sm-3 ] recipe-thumbnail">
          <img :src="thumbnail" :key="thumbnail" alt="Recipe image">
        </div>
        <div class="[ col-sm-7 ] recipe-details">
          <h1 class="recipe-title">{{ title }}</h1>
          <h2 class="recipe-ingredients">Ingredients:</h2>
          <p class="recipe-ingredients-list">{{ ingredients }}</p>
          <a :href="url"><span class="recipe-button">Go to Recipe</span></a>
        </div>
        <div class="[ col-sm-2 ] recipe-controls">
          <i class="material-icons next-btn" @click="changeRecipe(1)">expand_less</i>
          <span>{{ recipeNumber }} / {{ numberOfRecipes }}</span>
          <i class="material-icons prev-btn" @click="changeRecipe(-1)">expand_more</i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Recipes',
  props: [
    'thumbnail', 'title', 'url', 'ingredients', 'recipeNumber', 'numberOfRecipes'
  ],
  methods: {
    changeRecipe: function (param) {
      this.$parent.index += param;
      if (this.$parent.index === this.$parent.recipes.length) {
        this.$parent.index = 0;
      } else if (this.$parent.index === -1) {
        this.$parent.index = this.$parent.recipes.length - 1;
      }
    }
  }
}
</script>

<style lang="sass" scoped>
  @import url('https://fonts.googleapis.com/css?family=Dancing+Script|EB+Garamond')

  .container
    padding: 20px
    position: absolute
    top: 50%
    left: 50%
    max-width: 500px
    height: 100%
    max-height: 300px
    transform: translate(-50%, -50%)
    background-color: white
    border-radius: .5rem
    box-shadow: 0 19px 38px rgba(0, 0, 0, 0.30), 0 15px 12px rgba(0, 0, 0, 0.22)

  .recipe-thumbnail
    margin-bottom: 20px
    & img
      width: auto
      border: solid 3px #EDDFC3
      border-radius: 50%

  .recipe-details
    color: #1F1F1F
    & .recipe-title
      color: #FF2E2E
      font-family: 'Dancing Script', cursive
      font-size: 32px
    & .recipe-ingredients
      font-family: 'EB Garamond', serif
      font-size: 21px
      margin-top: 30px
    & .recipe-ingredients-list
      font-size: 16px
      font-family: 'EB Garamond', serif
      margin-bottom: 30px
    & .recipe-button
      padding: 6px 10px
      border-radius: .5rem
      background-color: #E1E7E7
      transition: .4s ease-in-out
      &:hover
        background-color: #EDDFC3
    & a
      color: inherit
      text-decoration: none

  .recipe-controls
    text-align: center
    color: #89B859
    i
      cursor: pointer
      font-size: 48px
    & *
      display: block
</style>