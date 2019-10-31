<template>
  <div class="recipes-index">
    <!-- Section - Services Start -->
    <section id="services" class="bg-gray-dark-2">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-8 text-center">
                    <h3 class="font-alt font-w-600 letter-spacing-2 title-extra-large text-uppercase text-white">Here's my Reipes...</h3>
                    <p class="mt-3 text-gray text-extra-large"><i>You've been warned</i></p>
                    <span class="bg-base-color mt-4 mx-auto sep-line-medium-thick-long"></span>
                </div>
                <!-- //.col-lg-8 -->
            </div>
            <!-- //.row -->
            
            <div class="row mt-5 pt-5">
                <div v-for="recipe in recipes" class="col-lg-4 bg-gray-dark-3 border-md-0 border-left border-bottom border-top border-right border-gray-2" data-mh="mh-col-services">
                  <router-link v-bind:to="'/recipes/' + recipe.id">
                    <div class="px-lg-3 py-5 py-lg-4 text-center text-lg-left">
                        <i class="icon-Chess text-base-color title-extra-large"></i>
                        <span class="d-block font-alt letter-spacing-2 mt-2 text-extra-large text-uppercase text-white">{{ recipe.title }}</span>
                        <span class="bg-base-color ml-lg-0 mt-3 mx-auto sep-line-thick"></span>
                        <p class="m-0 mt-3 text-gray text-medium">Ingredients</p>
                        <ul class="m-0 mt-3 text-gray text-medium">
                          <li v-for="ingredient in recipe.formatted.ingredients">{{ ingredient }}</li>
                        </ul>
                    </div>
                    <!-- //.px-lg-3 -->
                  </router-link>
                </div>
                <!-- //.col-lg-4 -->
            </div>
            <!-- //.row -->
        </div>
        <!-- //.container -->
    </section>
    <!-- //Section - Services End -->

  </div>
</template>

<style>
img {
  width: 250px;
}
</style>

<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      recipes: []
    };
  },
  created: function() {
    axios
      .get("/api/recipes")
      .then(response => {
        this.recipes = response.data;
      });
  },
  methods: {}
};
</script>