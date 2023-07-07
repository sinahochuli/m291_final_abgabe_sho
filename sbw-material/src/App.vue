<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav>
  <!-- in router/index.js werden Pfade mit Komponentent verbunden -->
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/reservations">Reservierungen</RouterLink>
    <RouterLink to="/about">Über</RouterLink>
  </nav>

  <RouterView />
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

button {
  border-bottom: 2px solid #42b983;
  background-color: #42b983;
  border: none;
  color: white;
  border-radius: 1.2em;
  padding: 0.4em;
  margin: 1em;
}

input[type="text"],
input[type="date"],
select {
  padding: 0.4em;
  border: none;
  border-bottom: 2px solid #42b983;
  font: inherit;
}

label {
  text-align: right;
}

label::after {
  content: ":";
}</style>
