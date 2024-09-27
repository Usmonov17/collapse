<template>
  <div class="border-dotted border-2 border-black p-4">
    <table class="w-full">
      <thead class="bg-gray-200">
        <tr>
          <th v-for="(column, i) in tableColumn" :key="i" class="px-6 py-3 text-left">
            {{ column.section }}
          </th>
          <th class="px-6 py-3 text-left">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in tableData" :key="index" class="border-b border-gray-300">
          <td v-for="column in tableColumn" :key="column.key" class="p-4">
            <div v-if="column.key === 'tags'">
              <span v-for="tag in item[column.key].split(', ')" :key="tag" :class="getTagStyle(tag)" class="mx-1">
                {{ tag }}
              </span>
            </div>
            <div v-else>
              <span v-if="column.key === 'name'" class="text-blue-600">{{ item[column.key] }}</span>
              <span v-else>{{ item[column.key] }}</span>
            </div>
          </td>
          <td class="px-6 py-4 flex gap-x-4">
            <button class="text-blue-600 ">
              Invite - {{ item.name }}
            </button>
            <button class="text-red-600" @click="$emit('deleteItem', index)">
              Delete
            </button>
            <button class="text-blue-600 flex items-center gap-x-1">
              More actions
              <img src="../../assets/images/dropdown.svg" alt="">
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const props = defineProps({
  tableData: Array,
  tableColumn: Array,
});

const tagStyles = {
  NICE: 'bg-green-100 text-green-800 px-2 py-1 rounded border border-[1px] border-green-500',
  DEVELOPER: 'bg-blue-100 text-blue-800 px-2 py-1 rounded border border-[1px] border-blue-500',
  LOSER: 'bg-red-100 text-red-800 px-2 py-1 rounded border border-[1px] border-red-500',
  COOL: 'bg-green-100 text-green-800 px-2 py-1 rounded border border-[1px] border-green-500',
  TEACHER: 'bg-blue-100 text-blue-800 px-2 py-1 rounded border border-[1px] border-blue-500',
};

const getTagStyle = (tag) => {
  return tagStyles[tag]
};
</script>
