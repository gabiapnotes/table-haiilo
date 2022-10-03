<script setup>
import TableCellScore from "./TableCellScore.vue";
defineProps(["dataColumn", "columnIndex"]);
</script>

<template>
  <div
    class="body-cell"
    v-for="(data, index) in dataColumn[0]"
    :key="`${data.filter_id}_${columnIndex}_${index}`"
    :id="`${data.filter_id}_${columnIndex}_${index}`"
  >
    <TableCellScore :score="data.value" />
  </div>
</template>
