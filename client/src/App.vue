<template>
  <v-app>
    <v-main>
      <v-container>
        <LogoBar/>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
// IMPORT
import axios from 'axios';
import LogoBar from '@/components/LogoBar.vue';

export default {
  name: 'App',
  data: () => ({
    allCars: [],
  }),

  components: {
    LogoBar,
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
    },
  },

  created() {
    this.getCars();
  },
};
</script>
