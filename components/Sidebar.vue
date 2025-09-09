<template>
  <div class="bg-blue-500 text-white w-64 min-h-screen p-4">
    <div class="mb-8">
      <h1 class="text-2xl font-bold">Dry Dock</h1>
    </div>

    <nav>
      <ul class="space-y-2">
        <li>
          <NuxtLink
            to="/dashboard"
            class="flex items-center space-x-3 p-2 rounded hover:bg-blue-600 transition-colors">
            <span class="material-icons">dashboard</span>
            <span>Dashboard</span>
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            to="/specification-groups"
            class="flex items-center space-x-3 p-2 rounded hover:bg-blue-600 transition-colors">
            <span class="material-icons">description</span>
            <span>Specification Groups</span>
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            to="/work-order"
            class="flex items-center space-x-3 p-2 rounded hover:bg-blue-600 transition-colors">
            <span class="material-icons">assignment</span>
            <span>Work Order Master</span>
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            to="/checklist"
            class="flex items-center space-x-3 p-2 rounded hover:bg-blue-600 transition-colors">
            <span class="material-icons">check_circle</span>
            <span>Checklist</span>
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            to="/dry-docks"
            class="flex items-center space-x-3 p-2 rounded hover:bg-blue-600 transition-colors">
            <span class="material-icons">anchor</span>
            <span>Dry Docks</span>
          </NuxtLink>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup>
// No additional setup needed for now
</script>
