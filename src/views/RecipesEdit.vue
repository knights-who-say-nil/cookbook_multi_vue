<template>
  <div class="recipes-edit">
    <h1>Edit Recipe</h1>
    <ul>
      <li v-for="error in errors">{{ error }}</li>
    </ul>

    <form v-on:submit.prevent="submit()">
      <div>
        Title: <input type="text" v-model="recipe.title">
      </div>

      <div>
        Chef: <input type="text" v-model="recipe.chef">
      </div>

      <div>
        Prep Time: <input type="text" v-model="recipe.prep_time">
      </div>

      <div>
        Ingredients: <input type="text" v-model="recipe.ingredients">
      </div>

      <div>
        Directions: <input type="text" v-model="recipe.directions">
      </div>

      <div>
        Image URL: <input type="text" v-model="recipe.image_url">
      </div>

      <input type="submit" value="Update">
    </form>
  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      errors: [],
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
  methods: {
    submit: function() {
      var clientParams = this.recipe;

      axios
        .patch("/api/recipes/" + this.$route.params.id, clientParams)
        .then(response => {
          this.$router.push("/recipes/" + response.data.id);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>