<script setup>
    defineProps({
        title: String,
        description: String,
        imageUrl: String,
    })
</script>

<template>
    <div class="flex flex-col items-center text-center w-72">
        <img height="80" width="80" :src="imageUrl" alt="Info Image"/>
        <h2 class="mt-4 text-2xl font-medium">{{ title }}</h2>
        <p class="text-gray-400">{{ description }}</p>
    </div>
</template>