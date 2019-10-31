<template>
  <div class="recipes-show">

    <!-- Section - Profile Start -->
    <section id="profile" class="bg-gray-dark-2 overflow-hidden py-0">
        <div class="container">
            <div class="row">
                <div class="col-xl-7 col-profile" data-mh="mh-col-profile">
                    <div class="pr-lg-4">
                        <h3 class="font-alt font-w-600 letter-spacing-2 title-extra-large text-uppercase text-white">{{ recipe.title }}!</h3>
                        <h5 class="mt-4 text-large text-white">Chef: {{ recipe.chef }}</h5>
                        <h4 class="mt-4 text-large text-white">Prep Time: {{ recipe.formatted.prep_time }}</h4>
                        <span class="bg-base-color mt-4 sep-line-medium-thick"></span>
                        <p class="mt-4 text-gray text-large">Ingredients</p>
                        <ul class="mt-3 text-gray text-large">
                          <li v-for="ingredient in recipe.formatted.ingredients">{{ ingredient }}</li>
                        </ul>
                        <span class="bg-base-color mt-4 sep-line-medium-thick"></span>
                        <p class="mt-4 text-gray text-large">Directions</p>
                        <ol class="mt-3 text-gray text-large">
                          <li v-for="direction in recipe.formatted.directions">{{ direction }}</li>
                        </ol>
                        <span class="bg-base-color mt-4 sep-line-medium-thick"></span>

                    </div>
                    <!-- //.pr-lg-4 -->
                </div>
                <!-- //.col-xl-7 -->
                
                <div class="col-xl-5 col-profile d-xl-block position-relative" data-mh="mh-col-profile">
                    <div>
                      
                    <img v-bind:src="recipe.image_url" alt="" class="img-fluid left-0 w-100"/>
                    </div>

                    <div>
                      <router-link class="btn box-shadow-wide btn-base-color btn-large mt-4 mt-md-5" v-bind:to=" '/recipes/' + recipe.id + '/edit' ">Edit</router-link>
                      <button class="btn box-shadow-wide btn-base-color btn-large mt-4 mt-md-5" v-on:click="destroyRecipe()">Destroy</button>
                    </div>
                </div>
                <!-- //.col-xl-5 -->
            </div>
            <!-- //.row -->
        </div>
        <!-- //.container -->
    </section>
    <!-- //Section - Profile End -->

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