<template>
  <div class="recipes-edit">
    <!-- Section - Contact Start -->
    <section id="contact" class="bg-gray-dark-2">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-8 text-center">
                    <h3 class="font-alt font-w-600 letter-spacing-2 title-extra-large text-uppercase text-white">Change Recipe</h3>
                    <p class="mt-3 text-gray text-extra-large"><i>Fix up the Fixin's for {{ recipe.title }}</i></p>
                    <span class="bg-base-color mt-4 mx-auto sep-line-medium-thick-long"></span>
                </div>
                <!-- //.col-lg-8 -->
            </div>
            <!-- //.row -->
            

            <div class="row justify-content-center mt-5 pt-lg-5">
                <div class="col-lg-8">
                    <form v-on:submit.prevent="submit()" id="form-contact">
                        <div class="row">
                          <div class="col-12">
                              <div class="form-group">
                                  <input type="text" class="font-alt form-control required" v-model="recipe.title" placeholder="Title">
                              </div>
                              <!-- //.form-group -->
                          </div>
                          <!-- //.col-12 -->

                            <div class="col-lg-6">
                                <div class="form-group">
                                  <input type="text" class="font-alt form-control required" v-model="recipe.prep_time" placeholder="Prep Time">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-lg-6 -->
                            
                            <div class="col-lg-6">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="recipe.chef" placeholder="Chef">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-lg-6 -->
                            
                            <div class="col-12">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="recipe.image_url" placeholder="Image URL">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->
                            
                            <div class="col-12">
                                <div class="form-group">
                                    <textarea class="font-alt form-control required" rows="12" placeholder="Ingredients" v-model="recipe.ingredients"></textarea>
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->

                            <div class="col-12">
                                <div class="form-group">
                                    <textarea class="font-alt form-control required" rows="12" placeholder="Directions" v-model="recipe.directions"></textarea>
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->
                            
                            <div class="col-12">
                                <span class="d-block font-alt letter-spacing-1 text-gray text-small text-uppercase">*Please complete all fields correctly</span>
                                <button type="submit" class="btn btn-base-color btn-block btn-large box-shadow-wide mt-5 mx-0 text-white" id="btn-form-contact">Update</button>

                                <ul class="text-gray mt-3">
                                  <li v-for="error in errors">{{ error }}</li>
                                </ul>
                            </div>
                            <!-- //.col-12 -->
                        </div>
                        <!-- //.row -->
                    </form>
                </div>
                <!-- //.col-lg-8 -->
            </div>
            <!-- //.row -->
        </div>
        <!-- //.container -->
    </section>
    <!-- //Section - Contact End -->
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