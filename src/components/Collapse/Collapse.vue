<template>
  <div class="w-full h-[100vh] flex flex-col items-center">
    <div class="flex flex-col w-[30%] bg-gray-200 mt-10">
      <TreeCollapse :data="menuData" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TreeCollapse from './TreeCollapse.vue';
const menuData = ref([
  {
    title: 'Models',
    child: [
      {
        title: 'Data Warehouse',
        child: [
          { title: 'Report Samples' },
          { title: 'Sales Performance' },
        ]
      }
    ]
  },
  {
    title: 'Statistics',
    child: [
      { title: 'Company statistics' },
      {
        title: 'Other statistics',
        child: [
          { title: 'Crocodile' }
        ]
      },
    ]
  }
]);
</script>
