<template>
    <div class="flex flex-col p-8">
        <!-- comment -->
    
        <div class="flex justify-center gap-2 mt-2">
            <router-link
              v-for="letter of letters"
              :key="letter"
              :to="{ name: 'byLetter', params: { letter } }"
            >
                {{ letter }}
            </router-link>
        </div>

        <!-- <pre>{{ ingredients }}</pre> -->
    </div>
</template>

<script setup>
    import { computed, onMounted, ref } from "vue";
    import store from '../store'
    import axiosClient from '../axiosClient.js'

    // const meals = computed(() => store.state.meals)
    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('')
    const ingredients = ref([]);

    onMounted(async() => {
        const res = await axiosClient.get('/list.php?i=list')
        console.log(res.data)
        ingredients.value = res.data
    })
</script>

<style>

</style>