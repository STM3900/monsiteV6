<template>
  <div>
    <Home />
    <About />
    <Parcours />
    <Test />
    <Competences />
  </div>
</template>

<script>
import Home from "../components/Home";
import About from "../components/About";
import Parcours from "../components/Parcours";
import Test from "../components/Test";
import Competences from "../components/Competences";

export default {
  components: { Home, About, Parcours, Test, Competences }
};
</script>

<style>
html {
  font-size: 62.5%;
}

body {
  margin: 0;
  font-family: "Quicksand", sans-serif;
  max-width: 100vw;
}

.content {
  padding-right: 20rem;
  padding-left: 20rem;
}
</style>
