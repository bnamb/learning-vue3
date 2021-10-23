<template>
<nav class="w-full bg-gradient-to-tr from-yellow-200 via-pink-200 to-pink-400 text-gray-700 px-4 py-3">
    <router-link class="mx-2" v-for="item in list" :key="item.to" :to="item.to" > {{item.title}} </router-link>
    <button class="my-2 px-2 font-bold" @click="$emit('open-login-modal')">Login</button>
</nav>
</template>

<script>
export default {
    data() {
        return {
            list: [
                {title: "Home", to:"/"},
                {title: "Grocery List", to:"/grocery-list"},
                {title: "Calendar", to:"/calendar"},
                {title: "Markdown", to:"/markdown"},
                {title: "Slider Carousel", to:"/slider"},
            ]
        }
    }
}
</script>

<style>

</style>