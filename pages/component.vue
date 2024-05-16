<script setup>
const id = ref(1)
</script>

<template>
  <div class="flex flex-col gap-2">
    <p>Example of data fetching inside a component:</p>
    <p><UButton @click="id--">Previous</UButton> - <UButton @click="id++">Next</UButton></p>
    <!--components/TheQuote.vue-->
    <TheQuote :id="id" />
    <NuxtLink class="underline" to="/">Back to Home</NuxtLink>
  </div>
</template>
