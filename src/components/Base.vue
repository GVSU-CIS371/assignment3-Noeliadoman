<template>
  <div :style="baseStyle" class="baseBeverage">
    {{ base }}
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps({
  base: {
    type: String,
    required: true
  }
});

// Dynamically set the background color based on the base beverage
const baseStyle = computed(() => {
  switch (props.base) {
    case 'Coffee':
      return {
        backgroundColor: '#6F4E37',
        height: '100%',
        borderRadius: '0.05em 0.05em 2.2em 2.2em',
      };
    case 'Green Tea':
      return {
        backgroundColor: '#9ACD32',
        height: '100%',
        borderRadius: '0.05em 0.05em 2.2em 2.2em',
      };
    case 'Black Tea':
      return {
        backgroundColor: '#3B2F2F',
        height: '100%',
        borderRadius: '0.05em 0.05em 2.2em 2.2em',
      };
    default:
      return {};
  }
});
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
}
</style>
