<template>
  <div class="text-center">
    <h1 class="text-4xl font-bold mb-8">Nuxt 3 starter ✅</h1>
    <p class="mb-4">Counter: {{ counter.count }}</p>
    <button
      @click="counter.inc()"
      class="bg-blue-500 text-white px-4 py-2 rounded">
      Increment
    </button>
  </div>
</template>

<script setup>
const counter = useCounter();
</script>
