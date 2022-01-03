<template>
  <div>
   <div class="container-fluid">
     <!-- navbar -->
     <ul class="nav nav-tabs">
       <li class="nav-item">
         <button v-on:click="goRecipes" class="nav-link active" aria-current="page">Recipes</button>
       </li>
       <li class="nav-item">
         <button v-on:click="goAddRecipe" class="nav-link">Add New</button>
       </li>
        <li class="nav-item">
         <button v-on:click="goAboutUs" class="nav-link">About Us</button>
       </li>
     </ul>
     <!-- end navbar -->
     <div>
       <Recipes v-if="page==='recipes'"/>
       <AddRecipe v-if="page==='add'"/>
       <AboutUs v-if="page==='about-us'"/>
       
     </div>
   </div>
 </div>
</template>

<script>
import AddRecipe from "@/components/AddRecipe"
import Recipes from "@/components/Recipes"
import AboutUs from "@/components/AboutUs"

export default {
  name: 'App',
  components: {
     Recipes, AddRecipe, AboutUs
  },
  data: function() {
    return {
      'page': 'recipes'
    }
  },
  methods:{
    'goRecipes': function() {
      this.page = "recipes"
    },
    'goAddRecipe': function() {
      this.page = "add"
    },
    'goAboutUs': function() {
      this.page= "about-us"
    }
  }
}
</script>
<style>

</style>
