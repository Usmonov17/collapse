<template>
  <div class="w-full h-[100vh] flex flex-col items-center">
    <div class="flex flex-col w-[30%] bg-gray-200 mt-10">
      <!-- Models bo'limi -->
      <div>
        <div
          class="flex items-center px-2 py-1 gap-x-4 w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300"
          @click="openFunc('models')">
          <img src="../assets/images/dropdown.svg" alt="" class="w-3 transition"
            :class="isModel ? 'rotate-0' : 'rotate-[-90deg]'">
          <span class="text-[24px]">Models</span>
        </div>

        <!-- Data Warehouse bo'limi -->
        <div v-if="isModel" @click="openFunc('data')">
          <div
            class="flex items-center px-2 py-1 gap-x-4 w-full cursor-pointer pl-[10%] border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300">
            <img src="../assets/images/dropdown.svg" alt="" class="w-3 transition"
              :class="isData ? 'rotate-0' : 'rotate-[-90deg]'">
            <span class="text-[24px]">Data Warehouse</span>
          </div>
          <div v-if="isData" class="flex flex-col">
            <span
              class="text-[24px] pl-[30%] w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300">Report
              Samples</span>
            <span
              class="text-[24px]  pl-[30%] w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300">Sales
              Performance</span>
          </div>
        </div>
      </div>

      <!-- Statistics bo'limi -->
      <div>
        <div
          class="flex items-center px-2 py-1 gap-x-4 w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300"
          @click="openFunc('stats')">
          <img src="../assets/images/dropdown.svg" alt="" class="w-3 transition"
            :class="isStats ? 'rotate-0' : 'rotate-[-90deg]'">
          <span class="text-[24px]">Statistics</span>
        </div>
        <div v-if="isStats" class="flex flex-col">
          <span
            class="text-[24px]  pl-[30%] w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300">Company
            statistics</span>
          <span
            class="text-[24px]  pl-[30%] w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300">Other
            statistics</span>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue';
const isModel = ref(false);
const isData = ref(false);
const isStats = ref(false);

const openFunc = (section) => {
  if (section === 'models') {
    isModel.value = !isModel.value;
  } else if (section === 'data') {
    isData.value = !isData.value
  } else if (section === 'stats') {
    isStats.value = !isStats.value
  }
}
</script>