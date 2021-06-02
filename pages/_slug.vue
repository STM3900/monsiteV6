<template>
  <div v-if="data" class="slug">
    <nav ref="nav" @click="goHome">Retour</nav>
    <header class="background">
      <h1>{{ data.name }}</h1>
      <p>
        Projet perso - <a v-if="data.link" :href="data.link">Aller au site</a>
      </p>
      <img
        v-if="checkIfColor"
        :src="require(`~/assets/background/${data.background}.jpg`)"
        alt=""
      />
      <div
        v-else
        class="background-colored"
        :style="
          data.background.includes('linear-gradient')
            ? 'background: ' + data.background + ';'
            : 'background-image: ' + data.background + ';'
        "
      ></div>
      <article>
        <section>
          Terminé le <b>{{ data.finishDate }}</b>
        </section>
        <section>
          Réalisé en <b>{{ data.workTime }}</b>
        </section>
        <section>
          Fait en <b>{{ data.languages.join(", ") }}</b>
        </section>
      </article>
    </header>
    <article class="description">
      <h2>Description du projet</h2>
      <p>
        {{ data.description }}
      </p>
    </article>
    <article class="list">
      <section>
        <h2>Principaux objectifs</h2>
        <ul>
          <li v-for="(item, i) in data.objectives" :key="i">
            {{ item }}
          </li>
        </ul>
      </section>
      <section>
        <h2>Outils utilisés</h2>
        <ul>
          <li v-for="(item, i) in data.softwares" :key="i">
            {{ item }}
          </li>
        </ul>
      </section>
    </article>
    <article>
      <h2>Description technique</h2>
      <p>
        {{ data.technicalDescription }}
      </p>
    </article>
    <article>
      <h2>Difficultés et axes d'amélioration</h2>
      <p>
        {{ data.difficulties }}
      </p>
    </article>
    <article>
      <h2>Conclusion</h2>
      <p>
        {{ data.conclusion }}
      </p>
    </article>

    <article class="button-group">
      <button v-if="checkIfExist(-1)" @click="changeProject(-1)">
        projet précedent
      </button>
      <button v-if="checkIfExist(1)" @click="changeProject(+1)">
        projet suivant
      </button>
    </article>
  </div>
</template>

<script>
import MASTER_JSON from "../assets/json/MASTER_JSON";
export default {
  transition: "slide-bottom",
  data() {
    return {
      rawData: MASTER_JSON,
      data: null
    };
  },
  computed: {
    checkIfColor() {
      return (
        !this.data.background.includes("#") ||
        !this.data.background.includes("linear-gradient")
      );
    }
  },
  mounted() {
    this.checkUrl();
    setTimeout(() => {
      this.$refs["nav"].classList.add("show");
    }, 500);
  },
  methods: {
    findIndex(json) {
      return json.findIndex(x => x.url === this.$route.params.slug);
    },
    checkUrl() {
      try {
        this.data = this.rawData[this.findIndex(this.rawData)];
        if (this.data == undefined) {
          this.$router.push("/");
        }
      } catch (error) {
        console.error(error);
        this.$router.push("/");
      }
    },
    changeProject(destination) {
      let temp = destination;
      let ok = false;
      let url = null;
      while (!ok) {
        if (this.rawData[this.findIndex(this.rawData) + temp].url) {
          ok = true;
          url = this.rawData[this.findIndex(this.rawData) + temp].url;
        }
        temp += destination;
      }
      this.$refs["nav"].style.display = "none";
      this.$router.push(`/${url}`);
    },
    checkIfExist(e) {
      return this.rawData[this.findIndex(this.rawData) + e];
    },
    goHome() {
      this.$refs["nav"].style.display = "none";
      this.$router.push("/");
    }
  }
};
</script>

<style scoped>
nav {
  position: fixed;
  top: 50px;
  left: 0;
  background: rgb(240, 240, 240);
  padding: 10px 15px 10px 30px;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
  transition: 0.3s;
  opacity: 0;
}

.show {
  opacity: 1;
}

nav:hover {
  cursor: pointer;
  padding-left: 27px;
}

.slug {
  padding-left: 20%;
  padding-right: 20%;
}

header {
  margin-top: 25px;
  width: 100%;
}

header img {
  width: 100%;
  height: 350px;
  object-fit: cover;
  border-radius: 5px;
}

.background-colored {
  width: 100%;
  height: 250px;
  border-radius: 5px;
}

header h1 {
  /* haut | droit | bas | gauche */
  padding: 10px 10px 10px 0;
  color: rgb(50, 50, 50);
  font-size: 40px;
  padding-bottom: 0;
}

header p {
  margin-top: 0;
  margin-bottom: 8px;
}

header a {
  color: black;
}

header article {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  align-content: center;
  margin-top: 25px;
  margin-bottom: 15px;
  gap: 15px 25px;
}

header article section {
  padding: 20px;
  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  border-radius: 5px;
}

article {
  margin-top: 30px;
  margin-bottom: 30px;
}

article h2 {
  margin-bottom: 10px;
  color: rgb(25, 25, 25);
}

.description {
  width: 75%;
}

.list {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: flex-start;
  align-content: center;

  gap: 10px 70px;
}

.button-group {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  align-content: center;
  gap: 10px 20px;
}

.button-group button {
  font-family: "Quicksand", sans-serif;
  padding: 10px 20px;
  font-size: 14px;
  background: none;
  border: none;
  background: rgb(240, 240, 240);
  transition: 0.3s;
  border-radius: 5px;
}

.button-group button:hover {
  cursor: pointer;
  transform: rotate(1deg);
  background: rgb(235, 235, 235);
}

.button-group button:active {
  transform: rotate(0deg) scale(0.98);
}
</style>