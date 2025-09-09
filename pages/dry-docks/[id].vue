<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Navigation Tabs -->
    <div class="max-w-7xl mx-auto px-8 py-4">
      <div class="bg-white rounded-lg shadow">
        <div class="flex space-x-1 border-b">
          <button
            v-for="tab in tabs"
            :key="tab.name"
            @click="activeTab = tab.name"
            :class="[
              'px-6 py-4 font-medium transition-colors',
              activeTab === tab.name
                ? 'border-b-2 border-blue-500 text-blue-500 bg-blue-50'
                : 'text-gray-500 hover:text-gray-700 hover:bg-gray-50',
            ]">
            {{ tab.label }}
          </button>
        </div>
      </div>
    </div>

    <!-- Header with blue background -->
    <div class="bg-[#2196F3] p-8">
      <div class="max-w-7xl mx-auto">
        <div class="flex items-start justify-between gap-6">
          <!-- Left Section -->
          <div class="flex items-start gap-6">
            <!-- Ship Image -->
            <div
              class="w-36 h-36 bg-white rounded-lg overflow-hidden flex-shrink-0">
              <img
                :src="dryDock.image || '/ocean-star.jpg'"
                :alt="dryDock.name"
                class="w-full h-full object-cover" />
            </div>

            <!-- Header Content -->
            <div class="flex-1">
              <div class="text-white/90 text-lg mb-1">{{ dryDock.name }}</div>
              <h1 class="text-white text-4xl font-bold mb-3">
                {{ dryDock.dockNo }}
              </h1>
              <p class="text-white/80 text-lg">{{ dryDock.description }}</p>
            </div>
          </div>

          <!-- Start Button -->
          <button
            class="bg-white px-6 py-3 rounded-lg text-blue-600 font-medium hover:bg-blue-50 transition-colors shadow-sm">
            Start Dry Dock
          </button>
        </div>
      </div>
    </div>

    <!-- Project Information -->
    <div class="max-w-7xl mx-auto px-8 py-6">
      <div class="bg-white rounded-lg shadow p-6">
        <div class="grid grid-cols-3 gap-8">
          <!-- Left Column -->
          <div class="space-y-6">
            <div>
              <div class="text-gray-500 text-sm mb-1">Dry Dock No</div>
              <div class="text-gray-900 font-medium">{{ dryDock.dockNo }}</div>
            </div>
            <div>
              <div class="text-gray-500 text-sm mb-1">Account Code</div>
              <div class="text-gray-900 font-medium">ABC-123</div>
            </div>
            <div>
              <div class="text-gray-500 text-sm mb-1">Currency</div>
              <div class="text-gray-900 font-medium">USD</div>
            </div>
          </div>

          <!-- Middle Column -->
          <div class="space-y-6">
            <div>
              <div class="text-gray-500 text-sm mb-1">Description</div>
              <div class="text-gray-900 font-medium">
                {{ dryDock.description }}
              </div>
            </div>
            <div>
              <div class="text-gray-500 text-sm mb-1">Responsible Rank</div>
              <div class="text-gray-900 font-medium">Roshan Ahluwalia/CE</div>
            </div>
          </div>

          <!-- Right Column -->
          <div class="space-y-6">
            <div>
              <div class="text-gray-500 text-sm mb-1">Company</div>
              <div class="text-gray-900 font-medium">UHC Pvt. Ltd.</div>
            </div>
            <div>
              <div class="text-gray-500 text-sm mb-1">Budget</div>
              <div class="text-gray-900 font-medium">200,000$</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Project Information 2-->
    <div class="max-w-7xl mx-auto px-8 py-6">
      <div class="bg-white rounded-lg shadow p-6">
        <div class="grid grid-cols-3 gap-8">
          <!-- Left Column -->
          <div class="space-y-6">
            <div>
              <div class="text-gray-500 text-sm mb-1">Planned Start Date</div>
              <div class="text-gray-900 font-medium">01/01/2020</div>
            </div>
            <div>
              <div class="text-gray-500 text-sm mb-1">Actual End Date</div>
              <div class="text-gray-900 font-medium">01/01/2020</div>
            </div>
          </div>

          <!-- Middle Column -->
          <div class="space-y-6">
            <div>
              <div class="text-gray-500 text-sm mb-1">Planned End Date</div>
              <div class="text-gray-900 font-medium">01/01/2020</div>
            </div>
          </div>

          <!-- Right Column -->
          <div class="space-y-6">
            <div>
              <div class="text-gray-500 text-sm mb-1">Actual Start Date</div>
              <div class="text-gray-900 font-medium">01/01/2020</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Shipyard and Status Section -->
    <div class="max-w-7xl mx-auto px-8 py-6">
      <div class="grid grid-cols-2 gap-8">
        <!-- Shipyard Section -->
        <div class="bg-white rounded-lg shadow p-6">
          <div class="mb-6">
            <h3 class="text-lg font-medium mb-4">Shipyard</h3>
            <div class="relative">
              <select
                v-model="selectedShipyard"
                class="w-full bg-white border border-gray-300 rounded-lg px-4 py-2.5 appearance-none cursor-pointer">
                <option value="" disabled>Select a shipyard</option>
                <option
                  v-for="shipyard in shipyards"
                  :key="shipyard"
                  :value="shipyard">
                  {{ shipyard }}
                </option>
              </select>
              <div
                class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none">
                <svg
                  class="w-5 h-5 text-gray-400"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24">
                  <path
                    strokeLinecap="round"
                    strokeLinejoin="round"
                    strokeWidth="2"
                    d="M19 9l-7 7-7-7" />
                </svg>
              </div>
            </div>
            <div
              v-if="!selectedShipyard"
              class="mt-4 p-3 bg-orange-50 text-orange-600 rounded-lg">
              No Shipyard Selected
            </div>
            <button
              class="mt-4 w-full bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition-colors">
              SELECT SHIPYARD
            </button>
          </div>
        </div>

        <!-- Priority and Status Section -->
        <div class="bg-white rounded-lg shadow p-6">
          <div class="space-y-6">
            <!-- Priority -->
            <div>
              <h3 class="text-lg font-medium mb-4">Priority</h3>
              <div class="relative">
                <select
                  v-model="selectedPriority"
                  class="w-full bg-white border border-gray-300 rounded-lg px-4 py-2.5 appearance-none cursor-pointer">
                  <option value="High">High</option>
                  <option value="Medium">Medium</option>
                  <option value="Low">Low</option>
                </select>
                <div
                  class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none">
                  <svg
                    class="w-5 h-5 text-gray-400"
                    fill="none"
                    stroke="currentColor"
                    viewBox="0 0 24 24">
                    <path
                      strokeLinecap="round"
                      strokeLinejoin="round"
                      strokeWidth="2"
                      d="M19 9l-7 7-7-7" />
                  </svg>
                </div>
              </div>
            </div>

            <!-- Status -->
            <div>
              <h3 class="text-lg font-medium mb-4">Status</h3>
              <div class="flex gap-4">
                <button
                  v-for="status in ['Planning', 'Execution', 'Completed']"
                  :key="status"
                  @click="selectedStatus = status"
                  :class="[
                    'flex-1 px-4 py-2 rounded-lg border transition-colors',
                    selectedStatus === status
                      ? 'bg-blue-50 border-blue-500 text-blue-500'
                      : 'border-gray-300 text-gray-700 hover:border-gray-400',
                  ]">
                  {{ status }}
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-8">
      <!-- Cost Summary -->
      <div class="mt-6">
        <h2 class="text-xl font-semibold mb-4">Cost Summary</h2>
        <div class="grid grid-cols-4 gap-6">
          <!-- Estimates Section -->
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Budget</h3>
            <p class="text-2xl font-bold">200,000$</p>
          </div>
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Yard Estimates</h3>
            <p class="text-2xl font-bold">300$</p>
          </div>
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Owner Estimates</h3>
            <p class="text-2xl font-bold">500$</p>
          </div>
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Total Estimates</h3>
            <p class="text-2xl font-bold">50,000$</p>
          </div>

          <!-- Actual Costs Section -->
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Actual Yard Costs</h3>
            <p class="text-2xl font-bold">400$</p>
          </div>
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Actual Owner Costs</h3>
            <p class="text-2xl font-bold">300$</p>
          </div>
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Total Costs</h3>
            <p class="text-2xl font-bold">60,000$</p>
          </div>
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-gray-500 text-sm mb-2">Variance</h3>
            <p class="text-2xl font-bold flex items-center">
              500
              <svg
                class="w-4 h-4 text-red-500 ml-1"
                fill="currentColor"
                viewBox="0 0 20 20">
                <path d="M10 3l4 4H6l4-4z" />
              </svg>
            </p>
          </div>
        </div>
      </div>

      <!-- Charts Section -->
      <div class="mt-8">
        <div class="grid grid-cols-2 gap-6">
          <!-- Status Chart -->
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-6">Status</h3>
            <div class="relative h-64">
              <StatusChart />
              <!-- Legend -->
              <div
                class="absolute bottom-0 left-0 right-0 flex flex-wrap gap-4 justify-center">
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-blue-500"></div>
                  <span class="text-sm text-gray-600">Open 64</span>
                </div>
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-green-500"></div>
                  <span class="text-sm text-gray-600">In Progress 50</span>
                </div>
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-pink-500"></div>
                  <span class="text-sm text-gray-600">On Hold 68</span>
                </div>
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-cyan-500"></div>
                  <span class="text-sm text-gray-600">Complete 40</span>
                </div>
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-amber-600"></div>
                  <span class="text-sm text-gray-600">132</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Yard Stay Chart -->
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-6">Yard Stay</h3>
            <div class="relative h-64">
              <YardStayChart />
              <!-- Legend -->
              <div
                class="absolute bottom-0 left-0 right-0 flex flex-wrap gap-4 justify-center">
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-blue-500"></div>
                  <span class="text-sm text-gray-600">In Dock 80808</span>
                </div>
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-green-500"></div>
                  <span class="text-sm text-gray-600">Repair 80808</span>
                </div>
                <div class="flex items-center gap-2">
                  <div class="w-3 h-3 rounded-full bg-pink-500"></div>
                  <span class="text-sm text-gray-600">0</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Comparison Chart -->
      <div class="mt-8 mb-8">
        <ComparisonChart />
      </div>

      <!-- Main Content based on active tab -->
      <div class="space-y-6">
        <div v-if="activeTab === 'specifications'">
          <SpecificationsList />
        </div>
        <div v-if="activeTab === 'tasks'">
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-4">Tasks</h3>
            <p class="text-gray-500">
              Task management content will be displayed here
            </p>
          </div>
        </div>
        <div v-if="activeTab === 'sourcing'">
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-4">Sourcing</h3>
            <p class="text-gray-500">
              Sourcing information will be displayed here
            </p>
          </div>
        </div>
        <div v-if="activeTab === 'execution'">
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-4">Execution</h3>
            <p class="text-gray-500">
              Execution details will be displayed here
            </p>
          </div>
        </div>
        <div v-if="activeTab === 'reporting'">
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-4">Reporting</h3>
            <p class="text-gray-500">
              Reports and analytics will be displayed here
            </p>
          </div>
        </div>
        <div v-if="activeTab === 'claims'">
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-lg font-semibold mb-4">Claims</h3>
            <p class="text-gray-500">
              Claims management will be displayed here
            </p>
          </div>
        </div>
        <PurchaseOrdersTable v-if="activeTab === 'purchaseOrders'" />
        <AttachmentsList v-if="activeTab === 'attachments'" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRoute } from "vue-router";
import StatusChart from "~/components/StatusChart.vue";
import YardStayChart from "~/components/YardStayChart.vue";
import ComparisonChart from "~/components/ComparisonChart.vue";
import SpecificationsList from "~/components/SpecificationsList.vue";
import AttachmentsList from "~/components/AttachmentsList.vue";
import PurchaseOrdersTable from "~/components/PurchaseOrdersTable.vue";

const route = useRoute();
const dryDockId = route.params.id;

// Navigation tabs
const tabs = [
  { name: "specifications", label: "Specifications" },
  { name: "tasks", label: "Tasks" },
  { name: "sourcing", label: "Sourcing" },
  { name: "execution", label: "Execution" },
  { name: "reporting", label: "Reporting" },
  { name: "claims", label: "Claims" },
  { name: "purchaseOrders", label: "Purchase Orders" },
  { name: "attachments", label: "Attachments" },
];

const activeTab = ref("specifications");

// Shipyard data
const shipyards = ref(["Shipyard A", "Shipyard B", "Shipyard C"]);
const selectedShipyard = ref("");

// Priority and Status
const selectedPriority = ref("Medium");
const selectedStatus = ref("Planning");

// Sample data - in real app, this would come from API
const dryDock = ref({
  name: "OCEAN STAR",
  dockNo: "SEPT2020/DD1",
  description: "DD Required to change BWT",
  image: "/ocean-star.jpg",
  manager: "Raden Akmal/MS",
  startDate: "01/09/2020",
  endDate: "05/09/2020",
  status: "Planning",
  accountCode: "ABC-123",
  company: "UHC Pvt. Ltd.",
  responsibleRank: "Roshan Ahluwalia/CE",
  currency: "USD",
  budget: "200,000$",
});

const costSummary = {
  estimates: {
    budget: "200,000$",
    yard: "300$",
    owner: "500$",
    total: "50,000$",
  },
  actual: {
    yard: "400$",
    owner: "300$",
    total: "60,000$",
    variance: "500",
  },
};

const getStatusClass = (status) => {
  const classes = {
    Planning: "text-yellow-600",
    Execution: "text-green-600",
    Completed: "text-blue-600",
    "In Progress": "text-orange-600",
  };
  return `${classes[status] || "text-gray-600"}`;
};
</script>
