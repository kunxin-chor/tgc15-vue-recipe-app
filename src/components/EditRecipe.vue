<template>
    <div>
        <h1>Edit Recipe</h1>
        <div>
            <label>Title</label>
            <input type="text" v-model="title" class="form-control"/>
        </div>
        <div>
            <label>Ingredients</label>
            <input type="text" 
                   class="form-control"
                   placeholder="Seperate each ingredient with a comma"
                   v-model="ingredients"/>
        </div>
        <button v-on:click="updateRecipe" class="my-3">Update</button>
    </div>
</template>

<script>

// BE SURE TO CHANGE THE API TO THE HEROKU VERSION WHEN YOU DEPLOYED YOUR VUE PROJECT
const BASE_API_URL="https://3000-blush-donkey-bpbrtfz9.ws-us25.gitpod.io/"
import axios from 'axios'
export default {
    data:function(){
        return {
            id:"",
            title: "",
            ingredients:""
        }
    },
    created:async function() {
        let response = await axios.get(BASE_API_URL + "recipes/" + this.recipeId)
        this.title = response.data.title;
        this.ingredients = response.data.ingredients
        this.id = response.data_id;
    },
    props:['recipeId'],
    methods: {
        "updateRecipe":async function() {
            await axios.patch(BASE_API_URL + "recipes/" + this.recipeId,{
                'title': this.title,
                'ingredients': this.ingredients.split(',')
            });
            this.$emit('recipe-updated')
        }
    }
}
</script>