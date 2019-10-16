<template>
  <div class="recipes-new">
    <h1>New Recipe</h1>
    <ul>
      <li v-for="error in errors">{{ error }}</li>
    </ul>

    <form v-on:submit.prevent="submit()">
      <div>
        Title: <input type="text" v-model="newRecipeTitle">
      </div>

      <div>
        Chef: <input type="text" v-model="newRecipeChef">
      </div>

      <div>
        Prep Time: <input type="text" v-model="newRecipePrepTime">
      </div>

      <div>
        Ingredients: <input type="text" v-model="newRecipeIngredients">
      </div>

      <div>
        Directions: <input type="text" v-model="newRecipeDirections">
      </div>

      <div>
        Image URL: <input type="text" v-model="newRecipeImageUrl">
      </div>

      <input type="submit" value="Create">
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
      newRecipeTitle: "",
      newRecipeChef: "",
      newRecipePrepTime: "",
      newRecipeIngredients: "",
      newRecipeDirections: "",
      newRecipeImageUrl: ""
    };
  },
  created: function() {},
  methods: {
    submit: function() {
      var clientParams = {
        title: this.newRecipeTitle,
        chef: this.newRecipeChef,
        prep_time: this.newRecipePrepTime,
        ingredients: this.newRecipeIngredients,
        directions: this.newRecipeDirections,
        image_url: this.newRecipeImageUrl
      };

      axios
        .post("/api/recipes", clientParams)
        .then(response => {
          this.$router.push("/");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>