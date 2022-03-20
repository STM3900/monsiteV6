<template>
  <div v-if="data" class="slug">
    <nav ref="nav" @click="goHome">
      <fa class="icon-menu" icon="home" />
      <p>Retour</p>
    </nav>
    <header class="background">
      <h1>{{ data.name }}</h1>
      <p>
        {{ data.category }}
        <span v-if="data.link"
          >- <a :href="data.link">{{ testIfGitHub(data.link) }}</a></span
        >
      </p>
      <img
        v-if="checkIfColor"
        :src="require(`~/assets/background/${data.background}.${testQubi()}`)"
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
    <article v-if="data.markdownFolder" class="markdown">
      <nuxt-content :document="markdown" />
    </article>
    <article v-if="data.description" class="description">
      <h2>Description du projet</h2>
      <p style="white-space: pre-line;">
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
    <article v-if="data.technicalDescription">
      <h2>Description avancée</h2>
      <p style="white-space: pre-line;">
        {{ data.technicalDescription }}
      </p>
    </article>
    <article v-if="data.difficulties">
      <h2>Difficultés et axes d'amélioration</h2>
      <p style="white-space: pre-line;">
        {{ data.difficulties }}
      </p>
    </article>
    <article v-if="data.conclusion">
      <h2>Conclusion</h2>
      <p style="white-space: pre-line;">
        {{ data.conclusion }}
      </p>
    </article>

    <article class="button-group">
      <button v-if="checkIfExist(-1)" @click="changeProject(-1)">
        projet suivant
      </button>
      <button v-if="checkIfExist(1)" @click="changeProject(+1)">
        projet précedent
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
      data: null,
      activeTab: []
    };
  },
  async asyncData({ redirect, $content, route }) {
    // Bon c'est pas le meilleur code du monde mais il est la quoi

    const rawDataAsync = MASTER_JSON;
    let markdown = "";

    try {
      const index = rawDataAsync.findIndex(x => x.url === route.params.slug);
      const goodData = rawDataAsync[index];
      if (goodData == undefined) {
        redirect("/");
      } else {
        const path = goodData.markdownFolder + "/" + goodData.markdownFolder;
        markdown = await $content(path).fetch();
      }
    } catch (e) {
      console.error(e);
      redirect("/");
    }

    return {
      markdown
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
    this.createActiveTab();
    setTimeout(() => {
      this.$refs["nav"].classList.add("show");
    }, 500);
  },
  methods: {
    testQubi() {
      let format = "jpg";
      if (this.data.name == "Qubi") {
        format = "gif";
      }

      return format;
    },
    testIfGitHub(url) {
      return url.includes("github") ? "Voir le repo GitHub" : "Aller au site";
    },
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
      let url = null;

      url = this.activeTab[this.findIndex(this.activeTab) + temp].url;

      this.$refs["nav"].style.display = "none";
      this.$router.push(`/${url}`);
    },
    checkIfExist(e) {
      return this.activeTab[this.findIndex(this.activeTab) + e];
    },
    goHome() {
      this.$refs["nav"].style.display = "none";
      this.$router.push("/");
    },
    createActiveTab() {
      for (let i = 0; i < this.rawData.length; i++) {
        if (this.rawData[i].url) {
          this.activeTab.push(this.rawData[i]);
        }
      }
    },
    test() {
      alert("ouais");
    }
  },
  head() {
    if (this.data) {
      return {
        title: `Théo Migeat | ${this.data.name}`,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: "description",
            name: "description",
            content: this.data.shortDescription
          }
        ]
      };
    }
  }
};
</script>

<style>
.nuxt-content h2 {
  margin-top: 20px;
  margin-bottom: 10px;
}

.nuxt-content img {
  width: 100%;
  border-radius: 5px;

  margin-top: 20px;
  margin-bottom: 20px;
}

.nuxt-content p {
  white-space: pre-wrap;
  word-break: break-word;
  line-height: 1.5;

  margin-bottom: 10px;
}
</style>

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

nav .icon-menu {
  display: none;
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
  align-items: flex-start;
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

@media screen and (max-width: 940px) {
  .list {
    flex-direction: column;
    gap: 25px 0px;
  }
}

@media screen and (max-width: 600px) {
  nav {
    padding: 10px 15px 10px 10px;
  }

  nav:hover {
    padding: 10px 15px 10px 10px;
  }

  nav .icon-menu {
    display: block;
    color: rgb(50, 50, 50);
  }

  nav p {
    display: none;
  }

  .slug {
    padding-left: 10%;
    padding-right: 10%;
  }

  .slug h1 {
    font-size: 32px;
  }

  article h2 {
    font-size: 20px;
  }

  header article {
    flex-direction: column;
  }

  header img {
    height: 250px;
  }

  header article section {
    width: 100%;
    font-size: 14px;
  }

  p {
    font-size: 14px;
  }
}

@media screen and (max-width: 460px) {
  nav {
    padding: 10px 10px 10px 5px;
  }

  nav:hover {
    padding: 10px 10px 10px 5px;
  }
}

@media screen and (max-width: 390px) {
  .button-group {
    flex-direction: column;
  }

  .button-group button {
    width: 100%;
    font-size: 13px;
  }

  header img {
    height: 200px;
  }
}
</style>
