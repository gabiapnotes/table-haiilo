<script setup>
import TableDataRow from "./TableDataRow.vue";

defineProps(["data", "indexData"]);
</script>

<template>
  <div
    class="body-row"
    v-for="(info, index) in data"
    :id="`${indexData[index]._id}_question_row`"
    :key="`${indexData[index]._id}_question_row`"
  >
    <TableDataRow :column-index="index" :data-column="info.scores" />
  </div>
</template>
