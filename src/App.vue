<template>
  <!-- Image and text -->
  <nav class="navbar navbar-light bg-light">
    <a class="navbar-brand" href="#">
      <img src="./assets/super-original-logo.png" width="60" height="45" class="d-inline-block align-top" alt="" />
      Resumes-R-Us
    </a>
    <router-link to="/my-resume/:id">My Resume</router-link>
    <router-link to="/resumes">Resumes</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: "Josefin Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
