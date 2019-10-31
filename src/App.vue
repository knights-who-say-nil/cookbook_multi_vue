<template>
  <div id="app">
    <!-- Section - Home Start -->
    <section v-if=" $router.currentRoute.path === '/'" id="home" class="home-bg-static bg-cover bg-gray-dark bg-overlay-black-5 w-100">
        <div class="container h-100">
            <div class="row align-items-center h-100 justify-content-center">
                <div class="col-lg-9 text-center">
                    <h2 class="font-alt font-w-600 letter-spacing-2 m-0 mt-3 opacity-9-5 text-uppercase text-white title-sm-extra-large-2 title-extra-large-4">Josh's Cookbook</h2>
                    <span class="d-block font-alt mt-2 opacity-9-5 text-white title-sm-extra-large title-extra-large-3">Delicate Delicacies</span>
                    <span class="d-block font-alt mb-2 mt-2 opacity-9-5 text-white text-extra-large">If you look at my recipes, you'll see I'm a bad cook</span>
                </div>
                <!-- //.col-lg-9 -->
            </div>
            <!-- //.row -->
        </div>
        <!-- //.container -->
    </section>
    <!-- //Section - Home End -->
    
    
    <!-- Navigation Start -->
    <nav id="navigation" class="navbar navbar-dark navbar-expand-lg bg-dark">
        <div class="container">
            <div class="navbar-header d-lg-none">
                <a class="navbar-brand page-scroll" href="#page-top">BERG</a>
                
                <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbar-berg" aria-controls="navbar-berg" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
            </div>
            <!-- //.navbar-header -->
            
            <div class="navbar-collapse collapse justify-content-center" id="navbar-berg">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <router-link class="nav-link" to="/">Home</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" to="/recipes/new">New Recipe</router-link>
                    </li>
                    <li class="nav-item">
                      <router-link class="nav-link" to="/signup">Sign Up</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" to="/login">Log In</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" to="/Logout">Log Out</router-link>
                    </li>
                </ul>
            </div>
            <!-- //.navbar-collapse -->
        </div>
        <!-- //.container -->
    </nav>
    <!-- //Navigation End -->

    <router-view/>

    <!-- Footer End -->
    <footer class="bg-gray-dark">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col text-center">
                    <ul class="m-0 p-0">
                        <li class="list-inline-item">
                            <a href="#" target="_blank" class="bg-gray-2 box-shadow-wide rounded text-white text-extra-large">
                                <i class="fa fa-facebook ease"></i>
                            </a>
                        </li>
                        <li class="list-inline-item">
                            <a href="#" target="_blank" class="bg-gray-2 box-shadow-wide rounded text-white text-extra-large">
                                <i class="fa fa-twitter ease"></i>
                            </a>
                        </li>
                        <li class="list-inline-item">
                            <a href="#" target="_blank" class="bg-gray-2 box-shadow-wide rounded text-white text-extra-large">
                                <i class="fa fa-linkedin ease"></i>
                            </a>
                        </li>
                        <li class="list-inline-item">
                            <a href="#" target="_blank" class="bg-gray-2 box-shadow-wide rounded text-white text-extra-large">
                                <i class="fa fa-dribbble ease"></i>
                            </a>
                        </li>
                        <li class="list-inline-item">
                            <a href="#" target="_blank" class="bg-gray-2 box-shadow-wide rounded text-white text-extra-large">
                                <i class="fa fa-instagram ease"></i>
                            </a>
                        </li>
                        <li class="list-inline-item">
                            <a href="#" target="_blank" class="bg-gray-2 box-shadow-wide rounded text-white text-extra-large">
                                <i class="fa fa-pinterest ease"></i>
                            </a>
                        </li>
                    </ul>
                    
                    <p class="m-0 mt-4 text-gray text-medium">&copy; 2017 Nick Berg. All rights reserved.</p>
                </div>
                <!-- //.col -->
            </div>
            <!-- //.row -->
        </div>
        <!-- //.container -->
    </footer>
    <!-- //Footer End -->

  </div>
</template>

<style>
</style>
