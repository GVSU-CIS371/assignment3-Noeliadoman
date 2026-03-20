<template>
  <!-- Only render if syrup is not "No Syrup" -->
  <div v-if="syrup !== 'No Syrup'" class="syrup" :style="syrupStyle"></div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps({
  syrup: {
    type: String,
    required: true
  }
});

// Change color based on syrup type
const syrupStyle = computed(() => {
  switch (props.syrup) {
    case 'Vanilla':
      return { backgroundColor: '#F3E5AB', height: '20%', zIndex: 400 };
    case 'Caramel':
      return { backgroundColor: '#C68E17', height: '20%', zIndex: 400 };
    case 'Hazelnut':
      return { backgroundColor: '#D2B48C', height: '20%', zIndex: 400 };
    default:
      return {};
  }
});
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  position: relative;
  width: 100%;
  animation: pour-tea 2s 1s forwards;
}
</style>
