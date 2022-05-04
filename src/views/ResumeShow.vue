<template>
  <div class="home">
    <h2>{{ message }}</h2>
  </div>
  <div class="card-columns">
    <div class="card col-md-3 mx-3" style="max-width: 18rem">
      <img
        src="https://assets.fxnetworks.com/cms/prod/2021/10/07/web_cast_dannydevito_its-always-sunny-in-philadelphia_570x698.jpg"
        class="rounded mx-auto d-block"
        alt="user.name"
      />
      <div class="card-body">
        <h5 class="card-title">{{ user.name }}</h5>
        <p class="card-text">He is Luke</p>
      </div>
      <div class="card-body">
        <a href="#" class="card-link">Card link</a>
        <br />
        <a href="#" class="card-link">Another link</a>
      </div>
    </div>
  </div>
  <div class="card">
    <div class="card-header">About Me</div>
    <div class="card-body">
      <blockquote class="blockquote mb-0">
        <p>I am Luke</p>
      </blockquote>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Meeeep",
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

<style>
.card {
  border-color: blueviolet;
}
img {
  max-width: 50%;
  height: auto;
}
</style>
