<template>
  <div>
    <Home/>
    <About/>
    <Parcours/>
  </div>
</template>

<script>
import Home from "../components/Home";
import About from "../components/About";
import Parcours from "../components/Parcours";

export default {
  components: { Home, About, Parcours }
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

  .content{
    padding-right: 20rem;
    padding-left: 20rem;
  }
</style>