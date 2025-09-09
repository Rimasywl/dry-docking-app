<template>
  <div class="bg-white p-6 rounded-lg shadow">
    <h3 class="text-lg font-semibold mb-4">Attachments</h3>
    <div class="space-y-4">
      <div
        v-for="attachment in attachments"
        :key="attachment.id"
        class="flex items-center justify-between p-3 border rounded-lg">
        <div class="flex items-center gap-3">
          <img
            :src="attachment.icon"
            :alt="attachment.type"
            class="w-10 h-10" />
          <div>
            <p class="font-medium">{{ attachment.name }}</p>
            <p class="text-sm text-gray-500">{{ attachment.type }}</p>
          </div>
        </div>
        <button class="text-gray-400 hover:text-gray-600">
          <span class="material-icons">more_vert</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const attachments = [
  {
    id: 1,
    name: "Progress Report",
    type: "PDF Document",
    icon: "/pdf-icon.png",
  },
  {
    id: 2,
    name: "Technical Drawings",
    type: "CAD File",
    icon: "/cad-icon.png",
  },
];
</script>
