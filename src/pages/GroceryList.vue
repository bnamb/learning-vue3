<template>
      <div class="m-auto mt-16">
      <h1 class="text-5xl text-center my-4 text-gray-700">Grocery List: {{groceryCount}} items</h1>
      <p class="text-gray-700 mb-5 text-center">Add another item to the grocery list, or take one away.</p>
      <ul>
        <li v-for="(item, index) in groceryItems" :key="item.name"> 
            <div class="flex justify-between text-gray-700"> {{item.name}} <button @click="removeItem(index)">x</button> </div>
        </li>
      </ul>
      <!-- <input v-model.trim="newItem"> -->
      <form class="mt-5 mb-10 flex" @submit.prevent="addItem">
        <input class="border rounded flex-auto" v-model="newItem" placeholder="Type Grocery Item Here" />
        <button class="border rounded bg-gradient-to-tr from-yellow-200 via-pink-200 to-pink-400 text-gray-700">Add Item</button>
      </form>
    </div>
</template>

<script>
export default {
    computed: {
      groceryCount() {
        return this.groceryItems.length;
      },
    },
    methods: {
        addItem(){
            if(this.newItem !== "") { this.groceryItems.push({name: this.newItem}); 
            this.newItem=''}
        },
        removeItem(index) {
            this.groceryItems = this.groceryItems.filter((item, i) => i != index)
        }
    },
    data() {
        return {
            newItem: "",
            groceryItems:[
                { name: "Eggs"}, 
                { name: "Milk"}, 
                { name: "Broccoli"}, 
                { name: "Apples"}, 
                ],
        };
    }
}
</script>

<style>

</style>