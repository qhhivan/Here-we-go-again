<template>
  <v-app>
    <v-main>
      <v-container>
        <p class="text-h2 text-center">Viel Erfolg!</p>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
// IMPORT
import axios from 'axios';

export default {
  name: 'App',
  data: () => ({
    allCars: [],
  }),

  methods: {
    async getCars() {
      try {
        const { data } = await axios.get('http://localhost:3000/cars');
        this.allCars = data;
        console.log(this.allCars);
      } catch (error) {
        console.error(error);
      }
    },
  },

  created () {
    this.getCars();
  },
};
</script>
