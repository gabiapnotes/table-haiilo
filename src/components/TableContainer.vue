<script setup>
import { ref } from "vue";
import TableBody from "./TableBody.vue";
import TableHead from "./TableHead.vue";

defineProps(["headers", "data", "indexData", "searchValue"]);
defineEmits(["search"]);

const scrollPositionXHeader = ref(0);
const scrollPositionXBody = ref(0);

const scrollXHeader = (x) => {
  scrollPositionXHeader.value = x;
};

const scrollXBody = (x) => {
  scrollPositionXBody.value = x;
};
</script>

<template>
  <div class="table">
    <div class="table-header">
      <TableHead
        @scroll-x-body="scrollXBody"
        @search="(args) => $emit('search', args)"
        :headers="headers"
        :scroll-position-x="scrollPositionXHeader"
        :search-value="searchValue"
      />
    </div>
    <div class="table-body">
      <TableBody
        @scroll-x-header="scrollXHeader"
        :scroll-position-x="scrollPositionXBody"
        :data="data"
        :index-data="indexData"
      />
    </div>
  </div>
</template>
