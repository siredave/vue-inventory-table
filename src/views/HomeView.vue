<template>
 <div class="p-4 mb-6 text-white rounded-lg shadow-lg bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500">
  <h2 class="text-2xl font-bold text-center">
    <span class="text-white">Selected Items : </span> 
    <span class="text-yellow-200">{{ selectedItems.length }}</span>
  </h2>
</div>

  <div class="overflow-x-auto bg-white rounded-lg shadow-lg">
    <table class="min-w-full bg-white rounded-lg table-auto">
      <thead class="bg-gray-200">
        <tr class="text-sm text-left text-gray-600">
          <th class="px-6 py-3 border-b">Name</th>
          <th class="px-6 py-3 border-b">Price</th>
          <th class="px-6 py-3 border-b">Location</th>
          <th class="px-6 py-3 border-b">Owner</th>
          <th class="px-6 py-3 border-b">In Stock</th>
        </tr>
      </thead>
      <tbody>
        <tr 
          v-for="item in items" 
          :key="item.id" 
          @click="toggleItem(item)"
          :class="getItemClass(item) ? 'bg-blue-300' : ''"
          class="gap-2 transition duration-100 cursor-pointer hover:bg-gray-100"
        >
          <td class="px-6 py-4 border-b">{{ item.name }}</td>
          <td class="px-6 py-4 border-b">{{ item.price | currency }}</td>
          <td class="px-6 py-4 border-b">{{ item.location }}</td>
          <td class="px-6 py-4 border-b">{{ item.owner }}</td>
          <td class="px-6 py-4 border-b">{{ item.instock ? "Yes" : "No" }}</td>
        </tr>
      </tbody>
    </table>
  </div>

  <h2 v-if="selectedItems.length" class="mt-4 font-bold text-blue-600">Selected Items: 
    <span class="font-semibold text-gray-600">{{ selectedItems.map(item => item.name).join(', ') }}</span>
  </h2>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      items: [
        { id: 1, name: "Product F", price: 93.32, location: "Los Angeles", owner: "Grace", instock: false },
        { id: 2, name: "Gear H", price: 13.24, location: "New York", owner: "Hank", instock: true },
        { id: 3, name: "Widget A", price: 210.53, location: "San Diego", owner: "Eve", instock: false },
        { id: 4, name: "Gear H", price: 77.53, location: "San Diego", owner: "Frank", instock: true },
        { id: 5, name: "Widget A", price: 171.79, location: "Philadelphia", owner: "Charlie", instock: false },
        { id: 6, name: "Instrument I", price: 56.92, location: "Chicago", owner: "Charlie", instock: false },
        { id: 7, name: "Device C", price: 462.24, location: "Houston", owner: "Alice", instock: true },
        { id: 8, name: "Module J", price: 156.9, location: "Phoenix", owner: "Frank", instock: true },
        { id: 9, name: "Widget A", price: 85.82, location: "San Diego", owner: "Eve", instock: false },
        { id: 10, name: "Accessory G", price: 53.4, location: "New York", owner: "Charlie", instock: true },
        { id: 11, name: "Item E", price: 85.32, location: "Philadelphia", owner: "Frank", instock: false },
        { id: 12, name: "Widget A", price: 62.89, location: "San Diego", owner: "Diana", instock: true },
        { id: 13, name: "Tool D", price: 203.87, location: "Los Angeles", owner: "Jack", instock: false },
        { id: 14, name: "Module J", price: 277.24, location: "Dallas", owner: "Alice", instock: false },
        { id: 15, name: "Tool D", price: 474.94, location: "Dallas", owner: "Ivy", instock: false },
        { id: 16, name: "Product F", price: 192.6, location: "Dallas", owner: "Jack", instock: true },
        { id: 17, name: "Module J", price: 365.97, location: "Houston", owner: "Frank", instock: true },
        { id: 18, name: "Instrument I", price: 463.94, location: "San Antonio", owner: "Charlie", instock: false },
        { id: 19, name: "Tool D", price: 304.27, location: "New York", owner: "Charlie", instock: true },
        { id: 20, name: "Tool D", price: 204.37, location: "Houston", owner: "Charlie", instock: true }
      ],
      selectedItems: []
    };
  },
  methods: {
    addItem(item) {
      if (!this.selectedItems.includes(item)) {
        this.selectedItems.push(item);
      }
    },
    deleteItem(item) {
      this.selectedItems = this.selectedItems.filter(i => i !== item);
    },
    getItemClass(item) {
      return this.selectedItems.includes(item);
    },
    toggleItem(item) {
      if (this.selectedItems.includes(item)) {
        this.deleteItem(item);
      } else {
        this.addItem(item);
      }
    },
  },
};
</script>

<style scoped>
thead {
  background-color: #f3f4f6;
}
</style>
