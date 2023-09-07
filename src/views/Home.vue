<template>
    <div class="flex flex-col p-8 items-center">
        <!-- comment -->
    
        <pre>Here we explore a food meal app where you can search a meal by a name, a letter or an ingredient</pre>
        <pre>Coded in Vue Js</pre>
        <pre>Coded by Randell Hera</pre>
        <mark><a href="mailto:randellhera@gmail.com">Send Email</a></mark>
        <q title="Checkout my Github"><a href="mailto:randellhera@gmail.com">Github</a></q>
        🚀

        <!-- <pre>{{ ingredients }}</pre> -->
    </div>
</template>

<script setup>
    import { computed, onMounted, ref } from "vue";
    import store from '../store'
    import axiosClient from '../axiosClient.js'

    // const meals = computed(() => store.state.meals)
    const ingredients = ref([]);

    onMounted(async() => {
        const res = await axiosClient.get('/list.php?i=list')
        console.log(res.data)
        ingredients.value = res.data
    })
</script>

<style>

</style>