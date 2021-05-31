<template>
  <div v-if="data" class="slug">
    <header class="background">
      <img :src="data.background" alt="" />
      <h1>{{ data.name }}</h1>
      <hr />
      <article>
        <section>Terminé le {{ data.finishDate }}</section>
        <section>Fait en {{ data.workTime }}</section>
        <section></section>
        <section></section>
      </article>
    </header>
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
        this.data = this.rawData[this.findIndex(this.rawData)];
        if (this.data == undefined) {
          this.$router.push("/");
        }
      } catch (error) {
        console.error(error);
        this.$router.push("/");
      }
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
  font-size: 35px;
  font-weight: normal;
}
</style>
