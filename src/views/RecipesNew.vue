<template>
  <div class="recipes-new">  
    <!-- Section - Contact Start -->
    <section id="contact" class="bg-gray-dark-2">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-8 text-center">
                    <h3 class="font-alt font-w-600 letter-spacing-2 title-extra-large text-uppercase text-white">New Recipe</h3>
                    <p class="mt-3 text-gray text-extra-large"><i>Create your own</i></p>
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
                                  <input type="text" class="font-alt form-control required" v-model="newRecipeTitle" placeholder="Title">
                              </div>
                              <!-- //.form-group -->
                          </div>
                          <!-- //.col-12 -->

                            <div class="col-lg-6">
                                <div class="form-group">
                                  <input type="text" class="font-alt form-control required" v-model="newRecipePrepTime" placeholder="Prep Time">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-lg-6 -->
                            
                            <div class="col-lg-6">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="newRecipeChef" placeholder="Chef">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-lg-6 -->
                            
                            <div class="col-12">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="newRecipeImageUrl" placeholder="Image URL">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->
                            
                            <div class="col-12">
                                <div class="form-group">
                                    <textarea class="font-alt form-control required" rows="12" placeholder="Ingredients" v-model="newRecipeIngredients"></textarea>
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->

                            <div class="col-12">
                                <div class="form-group">
                                    <textarea class="font-alt form-control required" rows="12" placeholder="Directions" v-model="newRecipeDirections"></textarea>
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->
                            
                            <div class="col-12">
                                <span class="d-block font-alt letter-spacing-1 text-gray text-small text-uppercase">*Please complete all fields correctly</span>
                                <button type="submit" class="btn btn-base-color btn-block btn-large box-shadow-wide mt-5 mx-0 text-white" id="btn-form-contact">Create</button>

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
          this.$router.push("/recipes/" + response.data.id);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>