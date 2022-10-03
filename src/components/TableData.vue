<script setup>
import TableDataColumn from "./TableDataColumn.vue";

defineProps(["data"]);
</script>

<template>
  <div class="body-column" v-for="(info, index) in data" :key="index">
    <TableDataColumn :column-index="index" :data-column="info.scores" />
  </div>
</template>
