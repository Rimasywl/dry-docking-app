<template>
  <div class="bg-white rounded-lg shadow">
    <div class="p-4 flex justify-between items-center border-b">
      <h2 class="text-xl font-semibold">All Dry Docks</h2>
      <div class="flex items-center gap-4">
        <div class="flex items-center gap-2">
          <input
            type="text"
            placeholder="Search..."
            class="px-3 py-2 border rounded-md" />
          <select class="px-3 py-2 border rounded-md">
            <option>Processing...</option>
          </select>
        </div>
        <button class="px-4 py-2 bg-blue-500 text-white rounded-md">Add</button>
        <button class="px-4 py-2 border border-gray-300 rounded-md">
          Export
        </button>
      </div>
    </div>
    <div class="overflow-x-auto">
      <table class="min-w-full">
        <thead>
          <tr class="bg-gray-50">
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Dry Dock No.
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Description
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Manager (User)
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Planned Start Date
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Planned End Date
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Status
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              No of Specs
            </th>
            <th class="px-6 py-3"></th>
          </tr>
        </thead>
        <tbody class="divide-y divide-gray-200">
          <tr
            v-for="item in tableData"
            :key="item.id"
            class="hover:bg-gray-50 cursor-pointer"
            @click="navigateToDetail(item.id)">
            <td class="px-6 py-4 text-sm">{{ item.dockNo }}</td>
            <td class="px-6 py-4 text-sm">{{ item.description }}</td>
            <td class="px-6 py-4 text-sm">{{ item.manager }}</td>
            <td class="px-6 py-4 text-sm">{{ item.startDate }}</td>
            <td class="px-6 py-4 text-sm">{{ item.endDate }}</td>
            <td class="px-6 py-4 text-sm">
              <span :class="getStatusClass(item.status)">{{
                item.status
              }}</span>
            </td>
            <td class="px-6 py-4 text-sm">{{ item.specs }}</td>
            <td class="px-6 py-4 text-sm text-right">
              <button class="text-gray-500 hover:text-gray-700" @click.stop>
                <span class="material-icons">more_vert</span>
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { navigateTo } from "#app";

const navigateToDetail = (id) => {
  navigateTo(`/dry-docks/${id}`);
};

const tableData = [
  {
    id: 1,
    dockNo: "SEPT2020/DD1",
    description: "DD Required to change BWT",
    manager: "Raden Akmal/MS",
    startDate: "01/09/2020",
    endDate: "05/09/2020",
    status: "Planning",
    specs: "50.00",
  },
  {
    id: 2,
    dockNo: "SEPT2020/DD1",
    description: "DD Required to change BWT",
    manager: "Raden DS",
    startDate: "01/09/2020",
    endDate: "05/09/2020",
    status: "Planning",
    specs: "50.50",
  },
  {
    id: 3,
    dockNo: "OCT2020/DD2",
    description: "DD Needed to change OIL TANK",
    manager: "Mark Wilson",
    startDate: "01/10/2020",
    endDate: "05/10/2020",
    status: "Execution",
    specs: "34.50",
  },
  {
    id: 4,
    dockNo: "OCT2020/DD2",
    description: "DD to repair crates",
    manager: "Mark Wilson",
    startDate: "01/10/2020",
    endDate: "05/10/2020",
    status: "Execution",
    specs: "3.00",
  },
];

const getStatusClass = (status) => {
  const classes = {
    Planning: "text-yellow-600",
    Execution: "text-green-600",
    Completed: "text-blue-600",
  };
  return `${classes[status] || "text-gray-600"}`;
};
</script>
