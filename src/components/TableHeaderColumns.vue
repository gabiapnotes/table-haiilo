<script setup>
defineProps(["headers"]);
</script>
<template>
  <div
    ref="element"
    class="header-cell filter"
    v-for="header in headers"
    :key="header._id"
  >
    <span>{{ header.en }}</span>
  </div>
</template>
