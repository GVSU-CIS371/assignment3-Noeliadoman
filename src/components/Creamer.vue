<template>
  <!-- Only render if creamer is not "No Creamer" -->
  <div v-if="creamer !== 'No Creamer'" class="froth" :style="frothStyle">
    <div v-for="n in 5" :key="n" class="foam" :style="foamStyle"></div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps({
  creamer: {
    type: String,
    required: true
  }
});

// Adjust the froth color and height based on creamer type
const frothStyle = computed(() => {
  switch (props.creamer) {
    case 'Milk':
      return { backgroundColor: '#FFFDD0', height: '18%' };
    case 'Cream':
      return { backgroundColor: '#FFF8DC', height: '20%' };
    case 'Half & Half':
      return { backgroundColor: '#F5F5DC', height: '19%' };
    default:
      return {};
  }
});

// Optional: foam color can match froth for consistency
const foamStyle = computed(() => {
  switch (props.creamer) {
    case 'Milk':
      return { backgroundColor: '#F5F5DC' };
    case 'Cream':
      return { backgroundColor: '#FAF0E6' };
    case 'Half & Half':
      return { backgroundColor: '#EEE8AA' };
    default:
      return {};
  }
});
</script>

<style lang="scss" scoped>
.froth {
  overflow: visible;
  transform: translateY(400%);
  position: relative;
  width: 100%;
  animation: pour-tea 2s 2s forwards;
}

.foam {
  display: block;
  border-radius: 50%;
  height: 40px;
  width: 40px;
  position: absolute;
}

.foam:nth-child(1) { top: 0px; left: -3px; }
.foam:nth-child(2) { top: 0px; left: 55px; }
.foam:nth-child(3) { width: 30px; height: 30px; border-radius: 40px; top: 3px; left: 30px; }
.foam:nth-child(4) { width: 30px; height: 30px; border-radius: 45px; top: 5px; right: -2px; }
.foam:nth-child(5) { top: 2px; right: 10px; }
</style>