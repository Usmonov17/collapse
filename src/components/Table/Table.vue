<template>
  <div class="p-10 w-full h-[100vh]">
    <TableItems :tableData="tableData" :tableColumn="tableColumn" @deleteItem="deleteItem" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TableItems from './TableItems.vue';

const tableColumn = [
  { key: 'name', section: 'Name' },
  { key: 'age', section: 'Age' },
  { key: 'address', section: 'Address' },
  { key: 'tags', section: 'Tags' },
];

const tableData = ref([
  { name: 'John Brown', age: 32, address: 'New York No. 1 Lake Park', tags: 'NICE, DEVELOPER' },
  { name: 'Jim Green', age: 42, address: 'London No. 1 Lake Park', tags: 'LOSER' },
  { name: 'Joe Black', age: 32, address: 'Sidney No. 1 Lake Park', tags: 'COOL, TEACHER' },
]);

const deleteItem = (index) => {
  tableData.value.splice(index, 1);
};
</script>
