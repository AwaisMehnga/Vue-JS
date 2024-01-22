<template>
     <div class='Recipe' v-if="recipeData.length > 0">
            <!-- left side  -->
            <div class='leftSide'>
                <div class='thumb'>
                    <img  :src="recipeData[0].strMealThumb" alt="" />
                    <br />
                    <!-- youtube link -->
                    <a class="ExLinks" :href="recipeData[0].strYoutube">Watch On Youtube</a>
                    <p>
                    <!-- country -->
                    <span>{{recipeData[0].strArea}}</span>
                    </p>
                </div>
                <!-- ingredients table -->
                <div >
                    <table class='ing'>
                    <thead>
                        <tr>
                        <th>Ingredient</th>
                        <th>Measure</th>
                        </tr>
                    </thead>
                    <tbody>     
                        <tr v-for="i in 20" :key="i">
                            <td v-if="recipeData[0][`strIngredient${i}`]">
                                {{ recipeData[0][`strIngredient${i}`]}}
                            </td>
                            <td v-if="recipeData[0][`strMeasure${i}`]">
                                {{ recipeData[0][`strMeasure${i}`]}}
                            </td>
                        </tr>
                    </tbody>
                    </table>
                </div>
            </div>

            <!-- right side -->
            <div class='rightSide'>
              <h2>
                Instructions
              </h2>
              <div class="Instructions">
                <p 
                    v-for="(paragraph, index) in recipeData[0].strInstructions.split('\r\n')" 
                    :key="index"
                >{{ paragraph }}</p>
              </div>
            </div>
        </div>
</template>
<script>
export default{
    props:['recipeData'],
    data(){
        return{

        }
    }
}
</script>