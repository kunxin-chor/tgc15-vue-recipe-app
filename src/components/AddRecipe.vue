<template>
    <div>
        <h1>Add Recipe</h1>
        <div>
            <label>Title</label>
            <input type="text" v-model="title"/>
        </div>
        <div>
            <label>Ingredients</label>
            <input type="text" 
                   placeholder="Seperate each ingredient with a comma"
                   v-model="ingredients"/>
        </div>
        <button v-on:click="addNew">Add New</button>
    </div>
</template>

<script>
export default {
    data:function(){
        return {
            title: "",
            ingredients:""
        }
    }
}
</script>