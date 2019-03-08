<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <img :src="thumbnail" :key="thumbnail" alt="Recipe image">
    <h5>{{ ingredients }}</h5>
    <a :href="url">Go to Intructions</a>
    <button @click="changeRecipe(-1)">Previous</button>
    <button @click="changeRecipe(1)">Next</button>
  </div>
</template>

<script>
export default {
  name: 'Recipes',
  props: [
    'thumbnail', 'title', 'url', 'ingredients'
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
  .container
    position: absolute
    top: 50%
    left: 50%
    transform: translate(-50%, -50%)
    max-width: 600px
    width: 80%
    border-radius: .5rem
    box-shadow: 0 19px 38px rgba(0, 0, 0, 0.30), 0 15px 12px rgba(0, 0, 0, 0.22)
    background-color: #EAEAEA

  h3
    margin: 40px 0 0

  ul
    list-style-type: none
    padding: 0

  li
    display: inline-block
    margin: 0 10px

  a
    color: #42b983
</style>