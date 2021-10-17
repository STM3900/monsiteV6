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
          beginDate: "Septembre 2021",
          label: "Alternance en développement web",
          work: "STMicroelectronics"
        },
        {
          beginDate: "Septembre 2020",
          endDate: "Septembre 2021",
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
          color: "#41b883",
          favorite: true,
          hours: 209,
          numProjects: 5
        },
        {
          label: "Javascript",
          icon: ["fab", "js-square"],
          color: "#efd81d",
          favorite: true,
          hours: "+400",
          numProjects: "+10"
        },
        {
          label: "CSS / Intégration",
          icon: ["fab", "css3"],
          color: "#379ad6",
          favorite: true,
          hours: "+670",
          numProjects: "+40"
        },
        {
          label: "Angular",
          icon: ["fab", "angular"],
          color: "#d6002f",
          hours: 30,
          numProjects: 1
        },
        {
          label: "C, C++, C#",
          icon: ["fab", "cuttlefish"],
          color: "#9b4f97",
          hours: "+300",
          numProjects: 5
        },
        {
          label: "GitHub",
          icon: ["fab", "github"],
          color: "#5b217b",
          hours: "Utilisé pour chaque projet depuis 3 ans"
        },
        {
          label: "PHP",
          icon: ["fab", "php"],
          color: "#858ebb",
          hours: 200,
          numProjects: 5
        },

        {
          label: "Base de données",
          icon: "database",
          color: "#005e86",
          hours: 100,
          numProjects: 6
        },
        {
          label: "Python",
          icon: ["fab", "python"],
          color: "#356c9b",
          hours: 50,
          numProjects: 1
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

/* responsive */

@media screen and (max-width: 600px) {
  .part h1 {
    font-size: 22px;
  }

  div p {
    font-size: 14px;
  }

  .part .icon {
    margin-right: 10px;
  }
}
</style>
