<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :creamer="currentCreamer"
      :syrup="currentSyrup"
      :base="currentBase"
    />

    <!-- Temperature -->
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>

    <!-- Creamer -->
    <ul>
      <li>
        <template v-for="c in creamers" :key="c">
          <label>
            <input
              type="radio"
              name="creamer"
              :value="c"
              v-model="currentCreamer"
            />
            {{ c }}
          </label>
        </template>
      </li>
    </ul>

    <!-- Syrup -->
    <ul>
      <li>
        <template v-for="s in syrups" :key="s">
          <label>
            <input
              type="radio"
              name="syrup"
              :value="s"
              v-model="currentSyrup"
            />
            {{ s }}
          </label>
        </template>
      </li>
    </ul>

    <!-- Base Beverage -->
    <ul>
      <li>
        <template v-for="b in bases" :key="b">
          <label>
            <input
              type="radio"
              name="base"
              :value="b"
              v-model="currentBase"
            />
            {{ b }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>
