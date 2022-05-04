<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>{{ user.name }}</h2>
    <p>{{ user.mass }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      currentUser: {},
      user: {},
    };
  },
  created: function () {
    this.resumeShow();
  },
  methods: {
    resumeShow: function () {
      axios.get("https://swapi.dev/api/people/1/").then((response) => {
        console.log(response.data);
        this.user = response.data;
      });
    },
  },
};
</script>

<style></style>
