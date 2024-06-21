<script setup>
  import { ref, computed } from 'vue';
  import TheHeader from './components/TheHeader.vue';
  import TheNav from './components/TheNav.vue';
  import AppMovies from './AppMovies.vue';
  import AppTemperature from './AppTemperature.vue';

  const routes = {
    '#movies': {
      component: AppMovies,
      label: 'Movies',
    },
    '#temperature': {
      component: AppTemperature,
      label: 'Temperature',
    }
  }

  const currentPath = ref(window.location.hash);
  updateCurrentPath();

  function updateCurrentPath() {
    const path = window.location.hash;
    currentPath.value = routes[path] ? path : '#temperature';
  }

  window.addEventListener('hashchange', updateCurrentPath);

  const currentView = computed(() => {
    return routes[currentPath.value].component;
  })
</script>

<template>
  <TheHeader>Bookmarks</TheHeader>
  <TheNav :routes="routes" :currentPath="currentPath"/>
  <main>
    <component :is="currentView" />
  </main>

</template>

<style>
* {
  font-family: Verdana, sans-serif;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
a {
  text-decoration: none;
  color: tomato;
}
a:hover {
  text-decoration: underline;
}
a:active {
  text-decoration: underline;
}
main {
  padding: 0 1rem;
}
</style>