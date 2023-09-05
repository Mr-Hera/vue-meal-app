<template>
    <a
        :href="href"
        class="px-3 py-2 rounded border-2 text-white border-red-600 bg-red-500 hover:bg-red-600 hover:text-white transition-colors"
        target="_blank"
    >
        <slot>YouTube</slot>
    </a>
</template>

<script setup>
    const props = defineProps({
        href: String
    })
</script>

<style>

</style>