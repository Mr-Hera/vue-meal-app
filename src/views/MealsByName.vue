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
        <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
            <router-link to="#">
                <img :src="meal.strMealThumb" :alt="meal.strTMeal" class="rounded-t-xl h-48 w-full object-cover" />
            </router-link>
            <div class="p-3">
                <h3 class="font-bold">{{ meal.strMeal }}</h3>
                <p class="mb-4">
                    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Perferendis, autem ipsam ut tenetur 
                    dolor nemo laudantium quo culpa natus obcaecati voluptatem accusantium, repellendus veritatis vero ab corrupti, numquam velit modi!
                </p>
                <div class="flex items-center justify-between">
                    <a
                      :href="meal.strYoutube"
                      class="px-3 py-2 rounded border-2 text-white border-red-600 bg-red-500 hover:bg-red-600 hover:text-white transition-colors"
                      target="_blank"
                    >
                        YouTube
                    </a>
                    <!-- <router-link
                      class="px-3 py-2 rounded border-2 text-white border-purple-600 bg-purple-500 hover:bg-purple-600 hover:text-white transition-colors"
                      target="_blank"
                      to="#"
                    >
                        View
                    </router-link> -->
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { computed, ref, onMounted } from 'vue'
    import store from '../store'
    import { useRoute } from 'vue-router'

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