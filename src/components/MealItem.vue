<template>
    <div class="bg-white shadow rounded-xl hover:scale-105 transition-all">
        <router-link :to="{ name: 'mealDetails', params: {id: meal.idMeal} }">
            <img :src="meal.strMealThumb" :alt="meal.strTMeal" class="rounded-t-xl h-48 w-full object-cover" />
        </router-link>
        <div class="p-3">
            <h3 class="font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4">
                Lorem ipsum dolor, sit amet consectetur adipisicing elit. Perferendis, autem ipsam ut tenetur 
                dolor nemo laudantium quo culpa natus obcaecati voluptatem accusantium, repellendus veritatis vero ab corrupti, numquam velit modi!
            </p>
            <div class="flex items-center justify-between">
                <YouTubeButton :href="meal.strYoutube" />
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
</template>

<script setup>

    import YouTubeButton from './YouTubeButton.vue'
    const { meal } = defineProps({
        meal: Object
    })
</script>

<style>

</style>