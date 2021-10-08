<template>
  <v-app>
    <LogoBar></LogoBar>
    <v-main>
      <CarCards :cars="allCars"></CarCards>
    </v-main>
  </v-app>
</template>

<script>
// IMPORT
import axios from 'axios';
import LogoBar from '@/components/LogoBar.vue';
import CarCards from '@/components/CarCards.vue';

export default {
  name: 'App',
  data: () => ({
    allCars: [],
  }),

  components: {
    LogoBar,
    CarCards,
  },

  methods: {
    async getCars() {
      try {
        const { data } = await axios.get('http://localhost:3000/cars');
        this.allCars = data;
        console.log(this.allCars);
      } catch (error) {
        console.error(error);
      }
      // @refresh="getCars()"
      // Um die daten zu refreshen
    },
  },

  created() {
    this.getCars();
  },
};
</script>
