<template>
  <div>
    <Header />
    <Presentation />
    <GlobalPath :schoolTab="schoolTab" :workTab="workTab" />
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
  },
  data() {
    return {
      schoolTab: [
        {
          beginDate: 2018,
          label: "Master en informatique",
          school: "Epsi Grenoble"
        },
        {
          beginDate: 2015,
          endDate: 2018,
          label: "Baccalauréat STI2D",
          school: "Lycée Polyvalent Vaucanson"
        }
      ],
      workTab: [
        {
          beginDate: "Septembre 2020",
          label: "Alternance en vue.js",
          work: "Erplain"
        },
        {
          beginDate: "Janvier",
          endDate: "Février 2020",
          label: "Stage en développement web",
          work: "Agence Cerf à Lunettes"
        },
        {
          beginDate: "Mai",
          endDate: "Juin 2019",
          label: "Stage en développement web",
          work: "Auphys Technologie"
        }
      ]
    }
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

  background: -webkit-linear-gradient(0deg, #00d2ff 0%, #3a47d5 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.part .icon {
  margin-right: 20px;
  color: #00C3F6;
}
</style>
