<template>
  <div class="bg-white p-6 rounded-lg shadow">
    <div class="flex justify-between mb-6">
      <h3 class="text-lg font-semibold">Purchase Orders</h3>
      <button class="bg-blue-500 text-white px-4 py-2 rounded-md">
        Create Purchase Order
      </button>
    </div>

    <div class="overflow-x-auto">
      <table class="min-w-full">
        <thead>
          <tr class="bg-gray-50">
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              PO Number
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Description
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Amount
            </th>
            <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">
              Status
            </th>
            <th class="px-6 py-3"></th>
          </tr>
        </thead>
        <tbody class="divide-y divide-gray-200">
          <tr
            v-for="order in purchaseOrders"
            :key="order.id"
            class="hover:bg-gray-50">
            <td class="px-6 py-4 text-sm">{{ order.poNumber }}</td>
            <td class="px-6 py-4 text-sm">{{ order.description }}</td>
            <td class="px-6 py-4 text-sm">${{ order.amount }}</td>
            <td class="px-6 py-4 text-sm">
              <span :class="getStatusClass(order.status)">{{
                order.status
              }}</span>
            </td>
            <td class="px-6 py-4 text-sm">
              <button class="text-gray-400 hover:text-gray-600">
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
const purchaseOrders = [
  {
    id: 1,
    poNumber: "PO-2025-001",
    description: "Engine parts and maintenance",
    amount: "12,500",
    status: "Pending",
  },
  {
    id: 2,
    poNumber: "PO-2025-002",
    description: "Technical inspection services",
    amount: "8,750",
    status: "Approved",
  },
];

const getStatusClass = (status) => {
  const classes = {
    Pending: "text-yellow-600",
    Approved: "text-green-600",
    Rejected: "text-red-600",
  };
  return `${classes[status] || "text-gray-600"}`;
};
</script>
