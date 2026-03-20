<template>
  <div class="syrup"></div>
</template>

<script setup lang="ts">
  import { computed } from "vue";
  import { currentSyrup } from "../stores/beverage";
  const bgColor = computed(() => currentSyrup.value.color);
</script>

<style lang="scss" scoped>
@mixin syrup-layer($color) {
  background: repeating-linear-gradient(
    45deg,
    white,
    white 10px,
    $color 10px,
    $color 20px
  );
}
.syrup {
  transform: translateY(400%);
  @include syrup-layer(v-bind(bgColor));
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}
</style>
