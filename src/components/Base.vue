<template>
  <div class="baseBeverage"></div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import { currentBase } from "../stores/beverage";
const bgColor = computed(() => currentBase.value.color);
</script>

<style scoped>
.baseBeverage {
  background-color: v-bind(bgColor);
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
}
</style>

