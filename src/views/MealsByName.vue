<template>
    <div class="p-8 pb-0">
        <input
          class="rounded border-2 border-gray-200 w-full"
          placeholder="Search for Meals..."
          type="text"
          v-model="keyword"
          @change="searchMeals"
        />
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
        <!-- <meal-item></meal-item> -->
        <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
    </div>
</template>

<script setup>
    import { computed, ref, onMounted } from 'vue'
    import store from '../store'
    import { useRoute } from 'vue-router'

    import YouTubeButton from '../components/YouTubeButton.vue'
    import MealItem from '../components/MealItem.vue'

    const keyword = ref('')
    const meals = computed(() => store.state.searchedMeals)
    const route = useRoute();

    function searchMeals() {
        store.dispatch('searchMeals', keyword.value)
    }

    onMounted(() => {
        keyword.value = route.params.name

        if(keyword.value) {
            searchMeals()
        }
    })
</script>

<style>

</style>