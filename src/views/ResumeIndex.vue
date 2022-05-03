<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      people: [],
    };
  },
  created: function () {
    this.indexResume();
  },
  methods: {
    indexResume: function () {
      axios.get("https://swapi.dev/api/people/").then((response) => {
        // console.log(response.data.results);
        this.people = response.data.results;
        console.log(this.people);
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style></style>
