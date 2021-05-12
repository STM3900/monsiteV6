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
div {
  height: 50vh;
}
</style>
