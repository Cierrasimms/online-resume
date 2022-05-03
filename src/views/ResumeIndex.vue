<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
  <div v-for="person in persons" v-bind:key="person.id">
    <h2>{{ person.name }}</h2>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      persons: [],
    };
  },
  created: function () {
    this.indexResume();
  },
  methods: {
    indexResume: function () {
      axios.get("https://swapi.dev/api/people/").then((response) => {
        // console.log(response.data.results);
        this.persons = response.data.results;
        console.log(this.persons);
      });
    },
  },
};
</script>

<style></style>
