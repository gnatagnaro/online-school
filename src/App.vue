<template>
  <div id="app">
    <nav class="router-style">
      <router-link to="/">Домашняя страница</router-link> |
      <router-link to="/about">Оставьте заявку</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}

.router-style {
  text-align: center;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #3172b9;
}
</style>
