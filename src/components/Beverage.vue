<template>
  <Mug>
    <!-- Show iced or hot layer -->
    <Cold v-if="isIced" />
    <Hot v-else />

    <!-- Contents with layered slots -->
    <Contents>
      <template v-slot:top>
        <!-- Only show creamer if selected -->
        <Creamer v-if="creamer !== 'No Creamer'" :creamer="creamer" />
      </template>
      <template v-slot:mid>
        <!-- Only show syrup if selected -->
        <Syrup v-if="syrup !== 'No Syrup'" :syrup="syrup" />
      </template>
      <template v-slot:bottom>
        <Base :base="base" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

type Props = {
  isIced: boolean;
  base: string;
  creamer: string;
  syrup: string;
};

const props = defineProps<Props>();

// Destructure for easier usage
const { isIced, base, creamer, syrup } = props;
</script>
