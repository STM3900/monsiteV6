<template>
  <div @scroll.passive="handleScroll">
    <Header />
    <Presentation />
    <GlobalPath :schoolTab="schoolTab" :workTab="workTab" />
    <Skills :skills="skills" />
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
      ],
      skills: [
        {
          label: "Vue.js / Nuxt",
          icon: ["fab", "vuejs"],
          color: "#41b883"
        },
        {
          label: "Javascript",
          icon: ["fab", "js-square"],
          color: "#efd81d"
        },
        {
          label: "Angular",
          icon: ["fab", "angular"],
          color: "#d6002f"
        },
        {
          label: "C, C++, C#",
          icon: ["fab", "cuttlefish"],
          color: "#9b4f97"
        },
        {
          label: "PHP",
          icon: ["fab", "php"],
          color: "#858ebb"
        },
        {
          label: "MYSQL",
          icon: "database",
          color: "#005e86"
        },
        {
          label: "GitHub",
          icon: ["fab", "github"],
          color: "#5b217b"
        },
        {
          label: "CSS",
          icon: ["fab", "css3"],
          color: "#379ad6"
        }
      ]
    };
  }
};
</script>

<style>
.part h1 {
  padding-top: 25px;
  color: rgb(50, 50, 50);
}

.part .icon {
  margin-right: 20px;
}
</style>
