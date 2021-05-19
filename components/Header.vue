<template>
  <div>
    <Particles class="particle" id="tsparticles" :options="particleConfig" />
    <header>
      <h1>Théo Migeat</h1>
      <p>Étudiant et développeur front-end</p>
      <section>
        <a
          v-for="(icon, i) in iconName"
          :key="i"
          :href="iconLink[i]"
          :target="i != 2 ? '_blank' : ''"
          @mouseover="setActiveLabel(i)"
          @mouseleave="isHover = false"
          ><fa class="icon" :icon="icon"
        /></a>
      </section>
      <p :class="isHover ? 'icon-label-hover' : 'icon-label'">
        {{ iconLabel[index] }}
      </p>
    </header>
    <svg class="wave" viewBox="0 0 1440 170">
      <path
        fill="#fdfffc"
        d="M0,51L60,65.2C120,79,240,108,360,110.5C480,113,600,91,720,79.3C840,68,960,68,1080,82.2C1200,96,1320,125,1440,127.5C1560,130,1680,108,1800,87.8C1920,68,2040,51,2160,45.3C2280,40,2400,45,2520,42.5C2640,40,2760,28,2880,39.7C3000,51,3120,85,3240,87.8C3360,91,3480,62,3600,51C3720,40,3840,45,3960,62.3C4080,79,4200,108,4320,110.5C4440,113,4560,91,4680,73.7C4800,57,4920,45,5040,39.7C5160,34,5280,34,5400,34C5520,34,5640,34,5760,36.8C5880,40,6000,45,6120,42.5C6240,40,6360,28,6480,31.2C6600,34,6720,51,6840,53.8C6960,57,7080,45,7200,59.5C7320,74,7440,113,7560,110.5C7680,108,7800,62,7920,59.5C8040,57,8160,96,8280,104.8C8400,113,8520,91,8580,79.3L8640,68L8640,170L8580,170C8520,170,8400,170,8280,170C8160,170,8040,170,7920,170C7800,170,7680,170,7560,170C7440,170,7320,170,7200,170C7080,170,6960,170,6840,170C6720,170,6600,170,6480,170C6360,170,6240,170,6120,170C6000,170,5880,170,5760,170C5640,170,5520,170,5400,170C5280,170,5160,170,5040,170C4920,170,4800,170,4680,170C4560,170,4440,170,4320,170C4200,170,4080,170,3960,170C3840,170,3720,170,3600,170C3480,170,3360,170,3240,170C3120,170,3000,170,2880,170C2760,170,2640,170,2520,170C2400,170,2280,170,2160,170C2040,170,1920,170,1800,170C1680,170,1560,170,1440,170C1320,170,1200,170,1080,170C960,170,840,170,720,170C600,170,480,170,360,170C240,170,120,170,60,170L0,170Z"
      ></path>
    </svg>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      iconName: [
        ["fab", "linkedin-in"],
        ["fab", "github"],
        "envelope",
        "file-alt"
      ],
      iconLink: [
        "https://www.linkedin.com/in/theo-migeat/",
        "https://github.com/STM3900",
        "mailto:theo.migeat@epsi.fr",
        "medias/fichiers/Cv_Théo_Migeat.pdf"
      ],
      iconLabel: ["LinkedIn", "Github", "Envoyer un mail", "Voir mon CV"],
      index: 0,
      isHover: false,
      particleConfig: {
        fpsLimit: 120,
        interactivity: {
          detectsOn: "canvas",
          events: {
            onHover: {
              enable: true,
              mode: "repulse"
            },
            resize: true
          },
          modes: {
            repulse: {
              distance: 100,
              duration: 0.4
            }
          }
        },
        particles: {
          color: {
            value: "#ffffff"
          },
          links: {
            color: "#ffffff",
            distance: 100,
            enable: true,
            opacity: 0.5,
            width: 1
          },
          collisions: {
            enable: true
          },
          move: {
            direction: "right",
            enable: true,
            outMode: "out",
            random: true,
            speed: 0.2,
            straight: false
          },
          number: {
            density: {
              enable: true,
              value_area: 800
            },
            value: 20
          },
          opacity: {
            value: 0.8
          },
          shape: {
            type: "circle"
          },
          size: {
            random: true,
            value: 5
          }
        },
        detectRetina: true
      }
    };
  },
  methods: {
    setActiveLabel(index) {
      this.isHover = true;
      this.index = index;
    }
  }
};
</script>

<style scoped>
div {
  height: 90vh;
  width: 100%;
  background: linear-gradient(0deg, #00d2ff 0%, #3a47d5 100%);
}

.particle {
  position: absolute;

  animation-name: fade;
  animation-duration: 1s;
  animation-timing-function: ease;
}

.wave {
  position: absolute;
  bottom: 10vh;
}

header {
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  align-content: center;

  animation-duration: 1s;
  animation-name: fadeHeader;
  animation-timing-function: ease;
}

header h1 {
  color: white;
  font-size: 75px;
  font-weight: normal;
  z-index: 99999;
}

header p {
  color: white;
  font-size: 20px;
  font-style: italic;
  margin-bottom: 25px;
  z-index: 99999;
}

header section {
  color: white;
  z-index: 99999;
}

.icon {
  font-size: 30px;
  margin-right: 15px;
  margin-left: 15px;
  margin-bottom: 10px;
  transition: 0.3s;
}

.icon:hover {
  transform: rotate(10deg);
}

.icon-label {
  margin-bottom: 150px;
  font-style: normal;
  font-size: 16px;

  transition: 0.3s;
  opacity: 0;
  z-index: -1;
}

.icon-label-hover {
  margin-bottom: 150px;
  font-style: normal;
  font-size: 16px;

  transition: 0.3s;
  opacity: 1;
  z-index: 1;
}

header section a {
  color: white;
}

@keyframes fade {
  0% {
    opacity: 0;
    transform: scale(0.98);
  }

  50% {
    opacity: 0;
    transform: scale(0.98);
  }

  100% {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes fadeHeader {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>
