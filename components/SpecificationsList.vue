<template>
  <div class="bg-white p-6 rounded-lg shadow">
    <div class="flex justify-between mb-6">
      <h3 class="text-lg font-semibold">Specifications</h3>
      <div class="flex gap-2">
        <input
          type="text"
          placeholder="Search"
          class="px-3 py-2 border rounded-md" />
        <button class="bg-blue-500 text-white px-4 py-2 rounded-md">
          Add New Specification
        </button>
      </div>
    </div>

    <div class="space-y-4">
      <div
        v-for="spec in specifications"
        :key="spec.id"
        class="border rounded-lg p-4">
        <div class="flex items-start gap-4">
          <img
            :src="spec.image"
            :alt="spec.title"
            class="w-16 h-16 object-cover rounded" />
          <div class="flex-1">
            <h4 class="font-medium mb-1">{{ spec.title }}</h4>
            <p class="text-sm text-gray-600">{{ spec.description }}</p>
          </div>
          <button class="text-gray-400 hover:text-gray-600">
            <span class="material-icons">more_vert</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const specifications = [
  {
    id: 1,
    image: "/spec1.jpg",
    title: "Monthly results of Auxiliary engine",
    description: "Technical specifications and performance metrics",
  },
  {
    id: 2,
    image: "/spec2.jpg",
    title: "4 Stroke Regular Check and Operation 01 Main",
    description: "Technical Report and Inspection Report",
  },
  // Add more specifications as needed
];
</script>

