<template>
  <div class="bg-white p-6 rounded-lg shadow">
    <h3 class="text-xl font-semibold mb-6">Comparison</h3>

    <!-- Legend -->
    <div class="flex gap-6 mb-4">
      <div class="flex items-center gap-2">
        <div class="w-3 h-3 bg-blue-500 rounded"></div>
        <span class="text-sm text-gray-600">Total Costs</span>
      </div>
      <div class="flex items-center gap-2">
        <div class="w-3 h-3 bg-green-500 rounded"></div>
        <span class="text-sm text-gray-600">Total Estimates</span>
      </div>
      <div class="flex items-center gap-2">
        <div class="w-3 h-3 bg-pink-500 rounded"></div>
        <span class="text-sm text-gray-600">Total Budget</span>
      </div>
    </div>

    <!-- Chart Container -->
    <div class="relative h-[300px]">
      <!-- Y-axis labels -->
      <div
        class="absolute left-0 top-0 bottom-8 w-12 flex flex-col justify-between text-sm text-gray-500">
        <span>300</span>
        <span>250</span>
        <span>200</span>
        <span>150</span>
        <span>100</span>
        <span>50</span>
        <span>0</span>
      </div>

      <!-- Chart Area -->
      <div class="ml-12 h-full">
        <div class="h-full flex items-end gap-4">
          <!-- General -->
          <div class="flex-1 flex items-end justify-center gap-2">
            <div class="w-8 bg-blue-500 h-[35%]"></div>
            <div class="w-8 bg-green-500 h-[40%]"></div>
            <div class="w-8 bg-pink-500 h-[10%]"></div>
            <div class="absolute -bottom-8 text-sm text-gray-500">General</div>
          </div>

          <!-- Equipment for Crew -->
          <div class="flex-1 flex items-end justify-center gap-2">
            <div class="w-8 bg-blue-500 h-[60%]"></div>
            <div class="w-8 bg-green-500 h-[95%]"></div>
            <div class="w-8 bg-pink-500 h-[15%]"></div>
            <div class="absolute -bottom-8 text-sm text-gray-500 text-center">
              Equipment for Crew
            </div>
          </div>

          <!-- Hull -->
          <div class="flex-1 flex items-end justify-center gap-2">
            <div class="w-8 bg-blue-500 h-[20%]"></div>
            <div class="w-8 bg-green-500 h-[25%]"></div>
            <div class="w-8 bg-pink-500 h-[5%]"></div>
            <div class="absolute -bottom-8 text-sm text-gray-500">Hull</div>
          </div>

          <!-- Machiney Main Components -->
          <div class="flex-1 flex items-end justify-center gap-2">
            <div class="w-8 bg-blue-500 h-[20%]"></div>
            <div class="w-8 bg-green-500 h-[25%]"></div>
            <div class="w-8 bg-pink-500 h-[5%]"></div>
            <div class="absolute -bottom-8 text-sm text-gray-500 text-center">
              Machiney Main Components
            </div>
          </div>

          <!-- Ship Common Systems -->
          <div class="flex-1 flex items-end justify-center gap-2">
            <div class="w-8 bg-blue-500 h-[20%]"></div>
            <div class="w-8 bg-green-500 h-[25%]"></div>
            <div class="w-8 bg-pink-500 h-[5%]"></div>
            <div class="absolute -bottom-8 text-sm text-gray-500 text-center">
              Ship Common Systems
            </div>
          </div>

          <!-- Fasting -->
          <div class="flex-1 flex items-end justify-center gap-2">
            <div class="w-8 bg-blue-500 h-[20%]"></div>
            <div class="w-8 bg-green-500 h-[25%]"></div>
            <div class="w-8 bg-pink-500 h-[5%]"></div>
            <div class="absolute -bottom-8 text-sm text-gray-500">Fasting</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Details Popup -->
    <div
      v-if="selectedItem"
      class="absolute bg-white p-4 rounded-lg shadow-lg border">
      <h4 class="font-medium mb-2">{{ selectedItem.name }}</h4>
      <div class="space-y-1">
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 bg-blue-500 rounded"></div>
          <span class="text-sm"
            >Total Costs: {{ selectedItem.totalCosts }}</span
          >
        </div>
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 bg-green-500 rounded"></div>
          <span class="text-sm"
            >Total Estimates: {{ selectedItem.totalEstimates }}</span
          >
        </div>
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 bg-pink-500 rounded"></div>
          <span class="text-sm"
            >Total Budget: {{ selectedItem.totalBudget }}</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const selectedItem = ref(null);

const chartData = [
  {
    name: "General",
    totalCosts: "180,00",
    totalEstimates: "300,00",
    totalBudget: "9,40",
  },
  {
    name: "Equipment for Crew",
    totalCosts: "180,00",
    totalEstimates: "300,00",
    totalBudget: "9,40",
  },
  {
    name: "Hull",
    totalCosts: "180,00",
    totalEstimates: "300,00",
    totalBudget: "9,40",
  },
  {
    name: "Machiney Main Components",
    totalCosts: "180,00",
    totalEstimates: "300,00",
    totalBudget: "9,40",
  },
  {
    name: "Ship Common Systems",
    totalCosts: "180,00",
    totalEstimates: "300,00",
    totalBudget: "9,40",
  },
  {
    name: "Fasting",
    totalCosts: "180,00",
    totalEstimates: "300,00",
    totalBudget: "9,40",
  },
];
</script>
