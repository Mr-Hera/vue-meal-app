<template>
    <div class="p-8 pb-0">
        <input
          class="rounded border-2 border-gray-200 w-full mb-5 focus:ring-orange-500 focus:border-orange-500"
          placeholder="Search for Meals..."
          type="text"
          v-model="keyword"
          @change="searchMeals"
        />
    </div>
    <Meals :meals="meals" />
</template>

<script setup>
    import { computed, ref, onMounted } from 'vue'
    import store from '../store'
    import { useRoute } from 'vue-router'

    import YouTubeButton from '../components/YouTubeButton.vue'
    import MealItem from '../components/MealItem.vue'
    import Meals from '../components/Meals.vue'

    const keyword = ref('')
    const meals = computed(() => store.state.searchedMeals)
    const route = useRoute();

    function searchMeals() {
        if(keyword.value) {
            store.dispatch('searchMeals', keyword.value)
        } else {
            store.commit('setSearchedMeals', [])
        }
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