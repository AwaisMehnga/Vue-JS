<template>
        <SearchRecipe
            :recipe-data="recipeData"
            :get-recipe-names="getRecipeNames"
            :get-recipe="getRecipe"
        ></SearchRecipe>
        <!-- starting recipe rendering here -->
        
        <h1 class='recipeHeading' v-if="recipeData.length > 0">{{recipeData[0].strMeal}}</h1>
        <RecipeData
            :recipe-data="recipeData"
        ></RecipeData>
</template>
  
<script>
import Axios from 'axios'
import SearchRecipe from './SearchRecipe.vue'
import RecipeData from './RecipeData.vue'
export default {
    components:{
        SearchRecipe,
        RecipeData
    },
    async created(){
        try {
            const response = await Axios.get('https://www.themealdb.com/api/json/v1/1/search.php?s=biryani');
            this.recipeData=response.data.meals
        } catch (error) {
            console.error('Error fetching recipe:', error);
        }
    },
    data(){
        return {
            recipeData: [] //stores all the recipes
        }
    },
    methods:{
        // get all the recipes names from the first letter
        async getRecipeNames(recipe){
            try {
            const response = await Axios.get(`https://www.themealdb.com/api/json/v1/1/search.php?f=${recipe}`);
            console.log(response.data.meals)
            this.recipeData=response.data.meals
            } catch (error) {
            console.error('Error fetching recipe:', error);
            }
            console.log(this.recipeData)
        },
        // get the recipe from the name
        async getRecipe(recipe){
            try {
            const response = await Axios.get(`https://www.themealdb.com/api/json/v1/1/search.php?s=${recipe}`);
            console.log(response.data);
            this.recipeData=response.data.meals
        
            } catch (error) {
            console.error('Error fetching recipe:', error);
            }
        }
    }
};
</script>
