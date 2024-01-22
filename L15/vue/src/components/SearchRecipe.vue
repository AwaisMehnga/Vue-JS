<template>  
    <div class='search'>
        <input 
            list='sug' 
            class='recipeInput' 
            type="text" 
            v-model="recipeName"
            placeholder='Enter Recipe...' 
            @input="()=>{recipeName.length==1 && getRecipeNames(this.recipeName)}"
        />
        <datalist id='sug'>
            <option 
                v-for="(recipe, index) in recipeData" 
                :key="index" 
                :value="recipe.strMeal"
            ></option>
        </datalist>

        <button 
            class='recipeBTN' 
            @click="()=>{getRecipe(this.recipeName)}"
        >Recipe</button>
    </div>
</template>

<script>
    export default{
        props:['getRecipeNames','getRecipe','recipeData'],
        data(){
            return{
                recipeName:''
            }
        }
    }
</script>