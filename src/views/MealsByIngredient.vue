<template>
    <Meals :meals="meals" />
</template>

<script setup>
import { computed, onMounted } from "vue";
import { useRoute } from "vue-router";
import store from "../store";
import Meals from '../components/Meals.vue'

const meals = computed(() => store.state.mealsByIngredient)
const route = useRoute()

onMounted(() => {
    store.dispatch('searchMealsByIngredient', route.params.ingredient)
})
</script>

<style>

</style>