<template>
  <div class="flex min-h-screen">
    <Sidebar />
    <div class="flex-1">
      <NavBar />
      <main class="container mx-auto px-4 py-8">
        <slot />
      </main>
      <AppFooter />
    </div>
  </div>
</template>

<script setup>
// Add material icons link
useHead({
  link: [
    {
      rel: "stylesheet",
      href: "https://fonts.googleapis.com/icon?family=Material+Icons",
    },
  ],
});
</script>
