<script setup>
  import { ref } from 'vue';
  import BaseInputNumber from './components/BaseInputNumber.vue';

  const tempSI = ref(0);

  const tempCelsius = defineModel('celsius', {
    get() {
      return tempSI.value - 273.15;
    },
    set(value) {
      tempSI.value = value + 273.15;
    }
  });

  const tempFahrenheit = defineModel('fahrenheit', {
    get() {
      return tempSI.value * 9 / 5 - 459.67;
    },
    set(value) {
      tempSI.value = (value + 459.67) * 5 / 9;
    }
  });

  const tempKelvin = defineModel('kelvin', {
    get() {
      return tempSI.value;
    },
    set(value) {
      tempSI.value = value;
    }
  });
</script>

<template>
  <BaseInputNumber
    v-model="tempCelsius"
    unit="°C"
    step="0.5"
    name="celsius"
  />
  <BaseInputNumber
    v-model="tempFahrenheit"
    unit="°F"
    step="0.5"
    name="fahrenheit"
  />
  <BaseInputNumber
    v-model="tempKelvin"
    unit="K"
    step="0.5"
    name="kelvin"
  />
</template>

<style scoped>

</style>
