<template>
  <div class="mb-6">
    <div class="flex justify-between items-center mb-4">
      <h1 class="text-2xl font-bold">My Dry Docks</h1>
      <div class="flex gap-2">
        <button class="px-4 py-2 bg-blue-500 text-white rounded-md">
          Minimal
        </button>
        <button class="px-4 py-2 border border-gray-300 rounded-md">
          Detailed
        </button>
      </div>
    </div>
    <div class="grid grid-cols-3 gap-4">
      <div
        v-for="(dock, index) in dryDocks"
        :key="index"
        class="bg-white p-4 rounded-lg shadow">
        <img
          :src="dock.image"
          :alt="dock.name"
          class="w-full h-40 object-cover rounded mb-3" />
        <div class="text-sm text-gray-600">{{ dock.status }}</div>
        <div class="font-medium">{{ dock.name }}</div>
        <div class="text-sm text-gray-500">{{ dock.date }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
const dryDocks = [
  {
    image: "/images/ship1.jpg",
    name: "Ocean Star",
    status: "Planning",
    date: "SEPT2020/DD1",
  },
  {
    image: "/images/ship2.jpg",
    name: "MV Glory",
    status: "Planning",
    date: "SEPT2020/DD1",
  },
  {
    image: "/images/ship3.jpg",
    name: "MV Happy",
    status: "Execution",
    date: "OCT2020/DD2",
  },
];
</script>
