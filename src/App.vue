<template>
  <div>
    <!-- Beverage Display -->
    <div class="mug">
      <Base :base="currentBase" />
      <Creamer v-if="currentCreamer !== 'No Creamer'" :creamer="currentCreamer" />
      <Syrup v-if="currentSyrup !== 'No Syrup'" :syrup="currentSyrup" />
    </div>

    <!-- Temperature -->
    <h3>Temperature</h3>
    <ul>
      <li v-for="temp in temps" :key="temp">
        <label>
          <input type="radio" name="temperature" :value="temp" v-model="currentTemp" />
          {{ temp }}
        </label>
      </li>
    </ul>

    <!-- Creamer -->
    <h3>Creamer</h3>
    <ul>
      <li v-for="c in creamers" :key="c">
        <label>
          <input type="radio" name="creamer" :value="c" v-model="currentCreamer" />
          {{ c }}
        </label>
      </li>
    </ul>

    <!-- Syrup -->
    <h3>Syrup</h3>
    <ul>
      <li v-for="s in syrups" :key="s">
        <label>
          <input type="radio" name="syrup" :value="s" v-model="currentSyrup" />
          {{ s }}
        </label>
      </li>
    </ul>

    <!-- Base Beverage -->
    <h3>Base Beverage</h3>
    <ul>
      <li v-for="b in bases" :key="b">
        <label>
          <input type="radio" name="base" :value="b" v-model="currentBase" />
          {{ b }}
        </label>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed, defineComponent } from 'vue';

/* ------------------ State ------------------ */
const temps = ['Hot', 'Cold'];
const currentTemp = ref('Hot');

const creamers = ['No Creamer', 'Milk', 'Cream', 'Half & Half'];
const currentCreamer = ref('No Creamer');

const syrups = ['No Syrup', 'Vanilla', 'Caramel', 'Hazelnut'];
const currentSyrup = ref('No Syrup');

const bases = ['Coffee', 'Green Tea', 'Black Tea'];
const currentBase = ref('Coffee');

/* ------------------ Components ------------------ */

// Base Component
const Base = defineComponent({
  props: { base: String },
  setup(props) {
    const styleObject = computed(() => {
      switch (props.base) {
        case 'Coffee': return { backgroundColor: '#6F4E37', height: '80px', borderRadius: '50%' };
        case 'Green Tea': return { backgroundColor: '#9ACD32', height: '80px', borderRadius: '50%' };
        case 'Black Tea': return { backgroundColor: '#3B2F2F', height: '80px', borderRadius: '50%' };
        default: return {};
      }
    });
    return { styleObject };
  },
  template: `<div :style="styleObject" class="layer">{{ base }}</div>`
});

// Creamer Component
const Creamer = defineComponent({
  props: { creamer: String },
  setup(props) {
    const styleObject = computed(() => {
      switch (props.creamer) {
        case 'Milk': return { backgroundColor: '#FFFDD0', height: '20px', marginTop: '-20px' };
        case 'Cream': return { backgroundColor: '#FFF8DC', height: '20px', marginTop: '-20px' };
        case 'Half & Half': return { backgroundColor: '#F5F5DC', height: '20px', marginTop: '-20px' };
        default: return {};
      }
    });
    return { styleObject };
  },
  template: `<div :style="styleObject" class="layer">{{ creamer }}</div>`
});

// Syrup Component
const Syrup = defineComponent({
  props: { syrup: String },
  setup(props) {
    const styleObject = computed(() => {
      switch (props.syrup) {
        case 'Vanilla': return { backgroundColor: '#F3E5AB', height: '10px', marginTop: '-10px' };
        case 'Caramel': return { backgroundColor: '#C68E17', height: '10px', marginTop: '-10px' };
        case 'Hazelnut': return { backgroundColor: '#D2B48C', height: '10px', marginTop: '-10px' };
        default: return {};
      }
    });
    return { styleObject };
  },
  template: `<div :style="styleObject" class="layer">{{ syrup }}</div>`
});
</script>

<style scoped>
.mug {
  width: 120px;
  height: 150px;
  border: 2px solid #333;
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  margin: 20px auto;
}

.layer {
  width: 100px;
  margin: auto;
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
