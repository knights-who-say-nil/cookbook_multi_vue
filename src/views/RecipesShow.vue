<template>
  <div class="recipes-show">
    <h1>{{ recipe.title }}</h1>
    <h5>Chef: {{ recipe.chef }}</h5>
    <h4>Prep Time: {{ recipe.formatted.prep_time }}</h4>

    <h3>Ingredients:</h3>
    <ul>
      <li v-for="ingredient in recipe.formatted.ingredients">{{ ingredient }}</li>
    </ul>

    <h3>Directions: </h3>
    <ol>
      <li v-for="direction in recipe.formatted.directions">{{ direction }}</li>
    </ol>

    <img v-bind:src="recipe.image_url" v-bind:alt="recipe.title">

    <div>
      <router-link v-bind:to=" '/recipes/' + recipe.id + '/edit' ">Edit</router-link>
      <button v-on:click="destroyRecipe()">Destroy</button>
    </div>
  </div>
</template>

<style>
</style>

<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      recipe: {
        id: "",
        title: "",
        chef: "",
        prep_time: "",
        ingredients: "",
        directions: "",
        image_url: "",
        friendly_created_at: "",
        formatted: {
          prep_time: "",
          directions: [],
          ingredients: []
        }
      }
    };
  },
  created: function() {
    axios
      .get("/api/recipes/" + this.$route.params.id)
      .then(response => {
        this.recipe = response.data;
      });
  },
  methods: {
    destroyRecipe: function() {
      axios
        .delete("/api/recipes/" + this.recipe.id)
        .then(response => {
          this.$router.push("/");
        });
    }
  }
};
</script>