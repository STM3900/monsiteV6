<template>
  <div>
    <Home/>
    <About/>
  </div>
</template>

<script>
import Home from "../components/Home";
import About from "../components/About";

export default {
  components: { Home, About }
}
</script>

<style>
  html{
    font-size: 62.5%;
  }

  body{
    margin: 0;
    font-family: 'Quicksand', sans-serif;
    max-width: 100vw;
  }
</style>