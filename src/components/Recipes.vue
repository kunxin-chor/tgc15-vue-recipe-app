<template>
    <div>
        <h1>All Recipes</h1>
        <table class="table">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Title</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="r in recipes" v-bind:key="r._id">
                    <td>{{r._id}}</td>
                    <td>{{r.title}}</td>
                    <td>
                        <button v-on:click="update(r._id)"
                         class="btn btn-primary btn-sm">Edit</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    
</template>

<script>

const BASE_API_URL="https://3000-blush-donkey-bpbrtfz9.ws-us25.gitpod.io/"

import axios from 'axios'
export default {
    created:async function() {
        let response = await axios.get(BASE_API_URL + 'recipes');
        this.recipes = response.data
    },
    data:function(){
        return {
            'recipes':[]
        }
    },
    methods:{
        'update':function(recipeId) {
            this.$emit('update-recipe', recipeId)
        }
    }
}
</script>