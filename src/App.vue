<template>
<calc />
</template>

<script>
import calc from './components/calc.vue';

export default {
  name: 'App',
  components: {
    calc
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Jost:ital@0;1&family=Roboto+Condensed:ital,wght@0,100..900;1,100..900&display=swap');
body {
  background-color: black;
  font-family: "Jost", sans-serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
}
.center {
  max-width: 1200px; /* Устанавливаем максимальную ширину контейнера */
  width: 100%; /* Ширина контейнера занимает всю доступную ширину */
  margin: 0 auto; /* Автоматически центрируем контейнер по горизонтали */
}
</style>
