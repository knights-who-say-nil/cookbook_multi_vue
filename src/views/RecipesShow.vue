<template>
  <div class="recipes-show">
    <h1>{{ recipe.title }}</h1>
    <h5>Chef: {{ recipe.chef }}</h5>
    <h4>Prep Time: {{ recipe.prep_time }}</h4>

    <h3>Ingredients: {{ recipe.ingredients }}</h3>
    <h3>Directions: {{ recipe.directions }}</h3>

    <img v-bind:src="recipe.image_url" v-bind:alt="recipe.title">
  </div>
</template>

<style>
</style>

<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      recipe: {}
    };
  },
  created: function() {
    axios
      .get("/api/recipes/" + this.$route.params.id)
      .then(response => {
        this.recipe = response.data;
      });
  },
  methods: {}
};
</script>