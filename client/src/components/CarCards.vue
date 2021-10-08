<template>
  <div>
    <div
      class="d-flex flex-wrap mb-6 justify-center align-stretch"
      color="grey lighten-2"
      flat
      tile
    >
      <div v-for="car in cars" :key="car.id" outlined tile class="ma-3">
        <CarCard :car="car" />
        <!-- @buycar="buyCar($event)" -->
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CarCard from '@/components/CarCard.vue';
export default {
  name: 'CarCards',

  components: {
    CarCard,
  },

  data: () => ({}),
  methods: {
    async buyCar(car) {
      try {
        await axios({
          url: `http://127.0.0.1:3000/cars/${car.id}`,
          method: 'PATCH',
          contentType: 'application/json',
          data: {
            title: `${car.title} RESERVED`,
          },
        });
        console.log(car);
        // return this.$emit('refresh', true);
      } catch (error) {
        console.error(error);
      }
    },
  },

  props: {
    cars: Array,
  },
};
</script>

<style lang="scss" scoped></style>
