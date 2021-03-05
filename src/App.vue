<template>
  <v-app>

    <v-main class="justify-center bg-image">
      <portfolio/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import Portfolio from './views/Portfolio.vue';

export default Vue.extend({
  name: 'App',

  components: {
    Portfolio,
  },
});
</script>

<style lang="scss">
  .bg-image{
    background-image: url('./assets/images/bg.png');
    background-position: 50%;
    background-size: cover;
    background-repeat: no-repeat;
  }
</style>
