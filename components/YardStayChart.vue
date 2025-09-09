<template>
  <div class="w-full h-full flex items-center justify-center">
    <!-- Donut chart shape using SVG -->
    <svg
      viewBox="0 0 100 100"
      class="w-full h-full max-w-[240px] transform -rotate-90">
      <!-- Background circle -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        stroke="#f0f0f0"
        stroke-width="10" />

      <!-- In Dock segment (blue) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.inDock"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(80808)} ${totalLength}`"
        stroke-dashoffset="0" />

      <!-- Repair segment (green) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.repair"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(80808)} ${totalLength}`"
        :stroke-dashoffset="-getSegmentLength(80808)" />

      <!-- Zero segment (pink) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.zero"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(0)} ${totalLength}`"
        :stroke-dashoffset="-getSegmentLength(161616)" />
    </svg>
  </div>
</template>

<script setup>
const totalLength = 282; // Circumference of the circle (2 * π * radius)

const chartColors = {
  inDock: "#3B82F6", // blue
  repair: "#22C55E", // green
  zero: "#EC4899", // pink
};

const getSegmentLength = (value) => {
  const total = 80808 + 80808 + 0; // Sum of all values
  return (value / total) * totalLength;
};
</script>
