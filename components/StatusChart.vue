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

      <!-- Open segment (blue) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.open"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(64)} ${totalLength}`"
        stroke-dashoffset="0" />

      <!-- In Progress segment (green) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.inProgress"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(50)} ${totalLength}`"
        :stroke-dashoffset="-getSegmentLength(64)" />

      <!-- On Hold segment (pink) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.onHold"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(68)} ${totalLength}`"
        :stroke-dashoffset="-getSegmentLength(114)" />

      <!-- Complete segment (cyan) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.complete"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(40)} ${totalLength}`"
        :stroke-dashoffset="-getSegmentLength(182)" />

      <!-- Additional segment (amber) -->
      <circle
        cx="50"
        cy="50"
        r="45"
        fill="none"
        :stroke="chartColors.additional"
        stroke-width="10"
        :stroke-dasharray="`${getSegmentLength(132)} ${totalLength}`"
        :stroke-dashoffset="-getSegmentLength(222)" />
    </svg>
  </div>
</template>

<script setup>
const totalLength = 282; // Circumference of the circle (2 * π * radius)

const chartColors = {
  open: "#3B82F6", // blue
  inProgress: "#22C55E", // green
  onHold: "#EC4899", // pink
  complete: "#06B6D4", // cyan
  additional: "#D97706", // amber
};

const getSegmentLength = (value) => {
  const total = 64 + 50 + 68 + 40 + 132; // Sum of all values
  return (value / total) * totalLength;
};
</script>
