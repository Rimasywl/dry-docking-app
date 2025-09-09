<template>
  <div class="p-6">
    <!-- My Dry Docks Section -->
    <div class="mb-8">
      <h2 class="text-xl font-semibold mb-4">My Dry Docks</h2>
      <div class="grid grid-cols-3 gap-4">
        <NuxtLink
          v-for="(dock, index) in myDryDocks"
          :key="index"
          :to="`/dry-docks/${dock.id}`"
          class="bg-white rounded-lg shadow overflow-hidden hover:shadow-lg transition-shadow cursor-pointer">
          <img
            :src="dock.image"
            :alt="dock.name"
            class="w-full h-48 object-cover" />
          <div class="p-4">
            <div class="text-sm text-gray-500 mb-1">{{ dock.name }}</div>
            <div class="font-medium mb-1">{{ dock.status }}</div>
            <div class="text-sm text-gray-500">{{ dock.dockNo }}</div>
          </div>
        </NuxtLink>
      </div>
    </div>

    <!-- All Dry Docks Section -->
    <div class="bg-white rounded-lg shadow">
      <div class="p-4 border-b flex justify-between items-center">
        <h2 class="text-xl font-semibold">All Dry Docks</h2>
        <div class="flex items-center gap-4">
          <div class="flex items-center gap-2">
            <input
              type="text"
              placeholder="Cari..."
              class="px-3 py-2 border rounded-md w-64" />
            <select class="px-3 py-2 border rounded-md w-32">
              <option>Processing...</option>
            </select>
          </div>
          <button class="px-4 py-2 bg-blue-500 text-white rounded-md">
            Add
          </button>
          <button class="px-4 py-2 border border-gray-300 rounded-md">
            Export
          </button>
        </div>
      </div>
      <div class="overflow-x-auto">
        <table class="w-full">
          <thead class="bg-gray-50">
            <tr>
              <th
                class="px-6 py-3 text-left text-sm font-medium text-gray-500 whitespace-nowrap">
                Dry Dock No.
              </th>
              <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                Description
              </th>
              <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                Manager (User)
              </th>
              <th class="px-6 py-3"></th>
            </tr>
          </thead>
          <tbody class="divide-y divide-gray-200">
            <tr
              v-for="item in dryDocks"
              :key="item.id"
              class="hover:bg-gray-50 cursor-pointer"
              @click="navigateToDetail(item.id)">
              <td class="px-6 py-4 text-sm whitespace-nowrap">
                {{ item.dockNo }}
              </td>
              <td class="px-6 py-4 text-sm">{{ item.description }}</td>
              <td class="px-6 py-4 text-sm">{{ item.manager }}</td>
              <td class="px-6 py-4 text-sm">
                <button class="text-gray-400 hover:text-gray-600" @click.stop>
                  <span class="material-icons">more_vert</span>
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <!-- Recent Specs Section -->
    <div class="mt-8 bg-white rounded-lg shadow">
      <div class="p-4 border-b flex justify-between items-center">
        <h2 class="text-xl font-semibold">recentSpecs</h2>
        <div class="flex items-center gap-4">
          <div class="flex items-center gap-2">
            <input
              type="text"
              placeholder="Cari..."
              class="px-3 py-2 border rounded-md w-64" />
          </div>
          <button class="px-4 py-2 bg-blue-500 text-white rounded-md">
            Add
          </button>
        </div>
      </div>
      <div class="relative" style="height: 600px">
        <div class="absolute inset-0 overflow-auto">
          <table class="w-full whitespace-nowrap">
            <thead class="bg-gray-50 sticky top-0 z-10">
              <tr>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  DryDock No,
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Description
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Manager/User
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  planned Start Date
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  planned End Date
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Actual Start Date
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Actual End Date
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Status
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  No of Specs
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Total Budget
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Total Estimates
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Variance
                </th>
                <th
                  class="px-6 py-3 text-left text-sm font-medium text-gray-500">
                  Shipyard Name
                </th>
                
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200">
              <tr
                v-for="spec in recentSpecs"
                :key="spec.id"
                class="hover:bg-gray-50">
                <td class="px-6 py-4 text-sm font-medium">{{ spec.no }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.description }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.manager }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.plannedStartDate }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.plannedEndDate }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.actiualStartDate }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.actualEndDate }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.status }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.noneofspecs }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.totalbudget }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.totalestimates }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.variance }}</td>
                <td class="px-6 py-4 text-sm">{{ spec.shipyardname }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.overflow-auto {
  scrollbar-width: thin;
  scrollbar-color: #888 #f1f1f1;
}

.overflow-auto::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

.overflow-auto::-webkit-scrollbar-track {
  background: #f1f1f1;
}

.overflow-auto::-webkit-scrollbar-thumb {
  background-color: #888;
  border-radius: 3px;
}

.overflow-auto::-webkit-scrollbar-thumb:hover {
  background-color: #555;
}

/* Make table header sticky and ensure proper layout */
table {
  border-collapse: separate;
  border-spacing: 0;
}

thead th {
  background: #f9fafb;
  min-width: 150px;
}

td {
  min-width: 150px;
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>

<script setup>
import { useRouter } from "vue-router";
const router = useRouter();

const navigateToDetail = (id) => {
  router.push(`/dry-docks/${id}`);
};

const myDryDocks = [
  {
    id: "SEPT2020DD1-1",
    image: "/ocean-star.jpg",
    name: "Ocean Star",
    status: "Planning",
    dockNo: "SEPT2020/DD1",
  },
  {
    id: "SEPT2020DD1-2",
    image: "/mv-glory.jpg",
    name: "MV Glory",
    status: "Planning",
    dockNo: "SEPT2020/DD1",
  },
  {
    id: "OCT2020DD2-1",
    image: "/mv-happy.jpg",
    name: "MV Happy",
    status: "Execution",
    dockNo: "OCT2020/DD2",
  },
];

const dryDocks = [
  {
    id: 1,
    dockNo: "SEPT2020/DD1",
    description: "DD Required to change BWT",
    manager: "0cean Star",
  },
  {
    id: 2,
    dockNo: "OCT2020/DD2",
    description: "DD Needed to change OIL TANK",
    manager: "MV Glory",
  },
  {
    id: 3,
    dockNo: "OCT2020/DD2",
    description: "DD Required to change BWT",
    manager: "MV Happy",
  },
  {
    id: 4,
    dockNo: "OCT2020/DD2",
    description: "DD Needed to change OIL TANK",
    manager: "MV Judas",
  },
  {
    id: 5,
    dockNo: "OCT2020/DD2",
    description: "DD to repair crates",
    manager: "Emma Stone",
  },
];

const recentSpecs = [
  {
    id: 1,
    no: "SEPT2020/DD1",
    description: "roshan",
    manager: "Engine",
    plannedStartDate: "SEPT2020/DD1",
    plannedEndDate: "05/09/2020",
    actiualStartDate: "01/09/2020",
    actualEndDate: "05/09/2020",
    status: "In Progress",
    noneofspecs: "50.00",
    totalbudget: "200,000$",
    totalestimates: "300$",
    variance: "50,000$",
    shipyardname: "kempell",
  },
  {
    id: 2,
    no: "SEPT2020/DD1",
    description: "roshan",
    manager: "Engine",
    plannedStartDate: "SEPT2020/DD1",
    plannedEndDate: "05/09/2020",
    actiualStartDate: "01/09/2020",
    actualEndDate: "05/09/2020",
    status: "In Progress",
    noneofspecs: "50.00",
    totalbudget: "200,000$",
    totalestimates: "300$",
    variance: "50,000$",
    shipyardname: "kempell",
  },
  {
    id: 3,
    no: "SEPT2020/DD1",
    description: "roshan",
    manager: "Engine",
    plannedStartDate: "SEPT2020/DD1",
    plannedEndDate: "05/09/2020",
    actiualStartDate: "01/09/2020",
    actualEndDate: "05/09/2020",
    status: "In Progress",
    noneofspecs: "50.00",
    totalbudget: "200,000$",
    totalestimates: "300$",
    variance: "50,000$",
    shipyardname: "kempell",
  },
  {
    id: 4,
    no: "SEPT2020/DD1",
    description: "roshan",
    manager: "Engine",
    plannedStartDate: "SEPT2020/DD1",
    plannedEndDate: "05/09/2020",
    actiualStartDate: "01/09/2020",
    actualEndDate: "05/09/2020",
    status: "In Progress",
    noneofspecs: "50.00",
    totalbudget: "200,000$",
    totalestimates: "300$",
    variance: "50,000$",
    shipyardname: "kempell",
  },
  {
    id: 5,
    no: "SEPT2020/DD1",
    description: "roshan",
    manager: "Engine",
    plannedStartDate: "SEPT2020/DD1",
    plannedEndDate: "05/09/2020",
    actiualStartDate: "01/09/2020",
    actualEndDate: "05/09/2020",
    status: "In Progress",
    noneofspecs: "50.00",
    totalbudget: "200,000$",
    totalestimates: "300$",
    variance: "50,000$",
    shipyardname: "kempell",
  },
];

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
