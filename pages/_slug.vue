<template>
  <div v-if="data" class="part">
    <div
      class="background"
      :style="`background-image: url(${data.background})`"
    >
      <h1>{{ data.name }}</h1>
    </div>
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
.background {
  margin-top: 25px;
  width: 100%;
  height: 350px;
  background: red;

  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: flex-end;
  align-content: center;

  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.background h1 {
  padding: 20px;
  color: white;
  font-size: 50px;
  font-weight: normal;
}
</style>
