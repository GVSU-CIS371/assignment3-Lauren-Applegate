<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'" />
    <ul>
      <li>

        <section class="option-row">
          <template v-for="temp in temps" :key="temp">
            <label>
              <input
                type="radio"
                name="temperature"
                :id="`r${temp}`"
                :value="temp"
                v-model="currentTemp"
              />
              {{ temp }}
            </label>
          </template>
        </section>

        <section class="option-row">
          <template v-for="base in bases" :key="base.id">
            <label>
              <input 
                type="radio" 
                name="base" 
                :value="base.id" 
                v-model="selectedBase" 
              />
              {{ base.name }}
            </label>
          </template>
        </section>

        <section class="option-row">
          <template v-for="cream in creamers" :key="cream.id">
            <label>
              <input 
                type="radio" 
                name="creamer" 
                :value="cream.id" 
                v-model="selectedCreamer" 
              />
              {{ cream.name }}
            </label>
          </template>
        </section>

        <section class="option-row">
          <template v-for="syrup in syrups" :key="syrup.id">
            <label>
              <input 
                type="radio" 
                name="syrup"
                :value="syrup.id" 
                v-model="selectedSyrup" 
              />
              {{ syrup.name }}
            </label>
          </template>
        </section>


      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue"
import Beverage from "./components/Beverage.vue";
import { temps, bases, creamers, syrups, currentTemp } from "./stores/beverage";
const selectedBase = ref(bases.value[0].id);
const selectedCreamer = ref(creamers.value[0].id);
const selectedSyrup = ref(syrups.value[0].id);
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
