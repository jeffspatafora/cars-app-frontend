<script>import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome!",
      cars: [],
      newCarParams: {}
    };
  },
  created: function () {
    this.carsIndex()
  },
  methods: {
    carsIndex: function () {
      console.log("index");
      axios.get("/cars.json").then(response => {
        console.log(response.data);
        this.cars = response.data;
      })
    }
  },
  carCreate: function () {

  }
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div>
      <!-- <p>Name: <input type="text" v-model="" /></p> -->
    </div>
    <div v-for="car in cars" v-bind:key="car.id">
      <h2>{{ car.make }} {{ car.model }}</h2>
      <!-- <p>{{ car.model }}</p> -->
      <p>{{ car.year }}</p>
      <p>{{ car.color }}</p>
      <img v-bind:src="car.image_url" />
      <hr>
    </div>
  </div>
</template>

<style>
img {
  width: 200px;
}
</style>