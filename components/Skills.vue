<template>
  <div class="part">
    <h1><fa class="icon" icon="clipboard-list" />Compétences et langages</h1>
    <p class="note">(Mesurées en nombre d'heures pratiquées hors entreprise)</p>
    <article>
      <section v-for="(item, i) in skills" :key="i">
        <aside>
          <fa
            class="icon-skill"
            :icon="item.icon"
            :style="{ color: item.color }"
          />
          <span v-if="item.favorite && hoverTab.length > 0">
            <span
              :class="hoverTab[i].isHover ? 'tooltip tooltip-hover' : 'tooltip'"
            >
              Compétence favorite
            </span>
            <fa
              class="icon-star"
              icon="star"
              @mouseover="hoverTab[i].isHover = true"
              @mouseleave="hoverTab[i].isHover = false"
            />
          </span>
        </aside>
        <h2>{{ item.label }}</h2>
        <p>
          {{ item.hours }}<span v-if="item.numProjects">h</span>
          <span v-if="item.numProjects"
            >- {{ item.numProjects + getProjects(item.numProjects) }}</span
          >
        </p>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  name: "Skills",
  props: {
    skills: Array
  },
  data() {
    return {
      hoverTab: []
    };
  },
  mounted() {
    // Pas forcément la manière la plus opti, mais ça le fait
    for (let i = 0; i < this.skills.length; i++) {
      this.hoverTab.push({ isHover: false });
    }
  },
  methods: {
    getProjects: numProjects => {
      let pluriel = false;
      if (typeof numProjects === "string") {
        pluriel = true;
      } else if (numProjects > 1) {
        pluriel = true;
      }

      return pluriel ? " projets effectués" : " projet effectué";
    }
  }
};
</script>

<style scoped>
.part {
  background: #fdfffc;
  margin-bottom: 25px;
}

.part .note {
  margin-bottom: 25px;
  color: rgb(100, 100, 100);
  font-style: italic;
  font-size: 14px;
}

.part .icon {
  color: hsl(199, 100%, 65%);
}

article {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  align-content: center;
  gap: 30px 20px;
}

article section {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  align-content: center;

  width: 350px;

  padding: 20px;
  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  border-radius: 5px;
}

article section aside {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  align-content: center;
  width: 100%;
}

article section .icon-skill {
  font-size: 25px;
  margin-bottom: 10px;
}

article section .icon-star {
  font-size: 14px;
  color: #fabb05;
  transition: 0.3s;
}

article section .icon-star:hover {
  transform: rotate(5deg);
}

article section h2 {
  font-size: 20px;
  font-weight: normal;
}

article section p {
  font-size: 16px;
  color: rgb(100, 100, 100);
}

.tooltip {
  color: rgb(175, 175, 175);
  font-size: 14px;
  transition: 0.3s;
  opacity: 0;
}

.tooltip-hover {
  opacity: 1;
}

@media screen and (max-width: 600px) {
  article section {
    width: 100%;
  }

  article section .icon-skill {
    font-size: 22px;
  }

  article section .icon-star {
    font-size: 12px;
  }

  article section h2 {
    font-size: 18px;
  }

  article section p {
    font-size: 14px;
  }

  .tooltip {
    font-size: 12px;
  }

  .part .note {
    font-size: 12px;
  }
}
</style>
