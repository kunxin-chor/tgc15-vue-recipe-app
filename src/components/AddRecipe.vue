<template>
    <div>
        <h1>Add Recipe</h1>
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
        <button v-on:click="addNew" class="my-3">Add New</button>
    </div>
</template>

<script>

// BE SURE TO CHANGE THE API TO THE HEROKU VERSION WHEN YOU DEPLOYED YOUR VUE PROJECT
const BASE_API_URL="https://3000-blush-donkey-bpbrtfz9.ws-us25.gitpod.io/"
import axios from 'axios'
export default {
    data:function(){
        return {
            title: "",
            ingredients:""
        }
    },
    methods: {
        "addNew":async function() {
            await axios.post(BASE_API_URL + "recipes",{
                'title': this.title,
                'ingredients': this.ingredients.split(',')
            });
            this.$emit('new-recipe-created')
        }
    }
}
</script>