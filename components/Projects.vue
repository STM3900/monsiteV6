<template>
  <div class="part">
    <h1><fa class="icon" icon="code" />Projets</h1>

    <div class="list">
      <ProjectCard
        v-for="(card, i) in data"
        class="emitCard"
        :key="i"
        :imgColor="card.imgColor"
        :name="card.name"
        :description="card.description"
        :finishDate="card.finishDate"
        :workTime="card.workTime"
        :link="card.link"
        :url="card.url"
        :index="i"
      />
    </div>
  </div>
</template>

<script>
import ProjectCard from "./ProjectCard";
import MASTER_JSON from "~/assets/json/MASTER_JSON";

export default {
  name: "Projects",
  components: { ProjectCard },
  data() {
    return {
      data: MASTER_JSON
    };
  }
};
</script>

<style scoped>
.part {
  background: #fdfffc;
}

.part h1 {
  margin-bottom: 60px;
}

.list {
  margin-top: 25px;
  width: 100%;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
  align-content: center;
  gap: 50px 0;
}
</style>
