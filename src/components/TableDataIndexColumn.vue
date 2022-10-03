<script setup>
defineProps(["indexData"]);
</script>

<template>
  <div class="index-row" v-for="indexLabel in indexData" :key="indexLabel._id">
    {{ indexLabel.labels.en }}
  </div>
</template>
