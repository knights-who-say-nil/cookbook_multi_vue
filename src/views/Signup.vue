<template>
  <div class="signup">
    <!-- Section - Contact Start -->
    <section id="contact" class="bg-gray-dark-2">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-8 text-center">
                    <h3 class="font-alt font-w-600 letter-spacing-2 title-extra-large text-uppercase text-white">Sign Up</h3>
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
                                    <input type="text" class="font-alt form-control required" v-model="name" placeholder="Name">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->

                            <div class="col-12">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="email" placeholder="Email">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->
                            
                            <div class="col-12">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="password" placeholder="Password">
                                </div>
                                <!-- //.form-group -->
                            </div>
                            <!-- //.col-12 -->

                            <div class="col-12">
                                <div class="form-group">
                                    <input type="text" class="font-alt form-control required" v-model="passwordConfirmation" placeholder="Password Confirmation">
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

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      name: "",
      email: "",
      password: "",
      passwordConfirmation: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        name: this.name,
        email: this.email,
        password: this.password,
        password_confirmation: this.passwordConfirmation
      };
      axios
        .post("/api/users", params)
        .then(response => {
          this.$router.push("/login");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>