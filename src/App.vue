<script setup>
//import "@/assets/css/pico.min.css";
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <main class="container">
    <header class="header-margin">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/courses">Subject</RouterLink>
        <RouterLink to="/enrollments">registr</RouterLink>
        <RouterLink to="/mycourse">My Subject</RouterLink>
      </nav>
    </header>

    <RouterView />
  </main>
</template>

<style scoped>
.header-margin {
  padding-top: 0.8em;
  padding-bottom: 0.8em;
  background-color: black;
}

nav > a {
  padding-left: 0.5em;
  padding-right: 0.5em;
  color: white;
  text-decoration: none;

  display: inline-block;
  width: 100px;
  height: 55px;

  color: White;

  /* centering text */
  text-align: center;    /* horizontally */
  line-height: 55px;     /* vertically */
   
  text-decoration: none;
}
</style>
