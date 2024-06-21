<script setup>
import { ref, watch } from 'vue';

const movies = ref([]);

    const fetchMovies = async () => {
      try {
        const response = await fetch('https://chabloz.eu/movies');
        console.log(response);
        const data = await response.json();
        movies.value = data;
      } catch (error) {
        console.error('Erreur lors de la récupération des films:', error);
      }
    };

fetchMovies();

watch(movies, () => {
  console.log(movies.value);
})

</script>


<template>
<p>asdfasdfasdfasdfasdfa</p>
</template>


<style scoped>

</style>