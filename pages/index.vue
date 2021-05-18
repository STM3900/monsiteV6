<template>
  <div>
    <Header />
    <Presentation />
    <GlobalPath />
    <Skills />
    <Projects />
    <Contact />
  </div>
</template>

<script>
import Header from "../components/Header";
import Presentation from "../components/Presentation";
import GlobalPath from "../components/GlobalPath";
import Skills from "../components/Skills";
import Projects from "../components/Projects";
import Contact from "../components/Contact";

export default {
  components: {
    Header,
    Presentation,
    GlobalPath,
    Skills,
    Projects,
    Contact
  }
};
</script>

<style>
body {
  margin: 0;
  font-family: "Quicksand", sans-serif;
}

.part {
  padding-left: 20%;
  padding-right: 20%;
}

.part h1 {
  padding-top: 25px;
}
</style>
