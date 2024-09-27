<template>
  <div>
    <div v-for="(data, i) in data" :key="i" class="flex flex-col">
      <div
        class="flex items-center px-2 py-1 gap-x-4 w-full cursor-pointer border-l-4 border-transparent hover:border-blue-500 hover:bg-gray-300"
        @click="openCollapse(i)">
        <img v-if="data.child" src="../../assets/images/dropdown.svg" alt="" class="w-3 transition"
          :class="opened[i] ? 'rotate-0' : 'rotate-[-90deg]'">
        <span class="text-[24px]">{{ data.title }}</span>
      </div>

      <div v-if="data.child && opened[i]" class="pl-[10%]">
        <TreeCollapse :data="data.child" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps({
  data: Array
});

const opened = ref([]);

onMounted(() => {
  props.data.forEach(() => {
    opened.value.push(false);
  });
});

const openCollapse = (i) => {
  opened.value[i] = !opened.value[i];
};
</script>
