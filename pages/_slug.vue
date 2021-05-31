<template>
  <div v-if="data" class="slug">
    <header class="background">
      <h1>{{ data.name }}</h1>
      <p>Projet perso - <a :href="data.link">Aller au site</a></p>
      <hr />
      <img :src="data.background" alt="" />
      <article>
        <section>Terminé le {{ data.finishDate }}</section>
        <section>Réalisé en {{ data.workTime }}</section>
        <section>Fait en Javascript</section>
      </article>
    </header>
    <h2>Description du projet</h2>
    <p>
      MusicHours est un site vous permettant, à partir d'une ville de votre
      choix, d'avoir une musique et un thème s'adaptant à l'heure et à la météo
      de celle-ci !
    </p>
    <h2>Principaux objectifs</h2>
    <ul>
      <li>Expérimenter de nouvelles choses en JS</li>
      <li>Surpasser mes limites en CSS</li>
      <li>Se connecter à une API et l'utiliser</li>
    </ul>
    <h2>Outils utilisés</h2>
    <ul>
      <li>VSCode / GitHub</li>
      <li>Jsp un logiciel comme ça</li>
      <li>Ont est là</li>
    </ul>
    <h2>Description technique</h2>
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Enim vitae
      adipisci nostrum ratione quia quaerat temporibus dicta. Velit eius
      sapiente dolorum quo recusandae. Nihil vero tempore corporis aliquam
      inventore quibusdam.
    </p>
    <h2>Difficultés et axes d'amélioration</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloremque odit
      delectus assumenda perferendis, sint numquam, consectetur dignissimos
      sapiente placeat, id accusamus dolore repellendus expedita veniam optio.
      Quisquam porro ullam veniam!
    </p>
    <h2>Conclusion</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Repellat ullam
      illo voluptatibus ducimus, consequuntur harum dicta magni atque totam,
      exercitationem voluptatum dignissimos pariatur blanditiis dolor vel nobis
      possimus et laborum!
    </p>
    <button v-if="checkIfExist(-1)" @click="changeProject(-1)">
      projet précedent
    </button>
    <button v-if="checkIfExist(1)" @click="changeProject(+1)">
      projet suivant
    </button>
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
  mounted() {
    this.checkUrl();
  },
  methods: {
    findIndex(json) {
      return json.findIndex(x => x.url === this.$route.params.slug);
    },
    checkUrl() {
      try {
        console.log(this.rawData);
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
      this.$router.push(`/${url}`);
    },
    checkIfExist(e) {
      return this.rawData[this.findIndex(this.rawData) + e];
    }
  }
};
</script>

<style scoped>
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
}

header h1 {
  /* haut | droit | bas | gauche */
  padding: 10px 10px 10px 0;
  color: rgb(75, 75, 75);
  font-size: 40px;
  font-weight: normal;
  padding-bottom: 0;
}

header p {
  margin-top: 0;
  margin-bottom: 8px;
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
</style>
