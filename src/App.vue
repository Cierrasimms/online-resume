<template>
  <nav class="navbar navbar-light bg-light">
    <a class="navbar-brand" href="">
      <img
        src="https://purepng.com/public/uploads/thumbnail/google-stadia-logo-hd4.png"
        width="50"
        height="50"
        class="d-inline-block align-top"
        alt=""
      />
      My Resume
    </a>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
