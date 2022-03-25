<template>
  <div>
    <svg
      xmlns:xlink="http://www.w3.org/1999/xlink"
      id="wave"
      style="transform:rotate(0deg); transition: 0.3s"
      viewBox="0 0 1440 120"
      version="1.1"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        style="transform:translate(0, 0px); opacity:1"
        fill="rgb(245, 245, 245)"
        d="M0,36L34.3,46C68.6,56,137,76,206,76C274.3,76,343,56,411,46C480,36,549,36,617,44C685.7,52,754,68,823,70C891.4,72,960,60,1029,54C1097.1,48,1166,48,1234,56C1302.9,64,1371,80,1440,86C1508.6,92,1577,88,1646,88C1714.3,88,1783,92,1851,84C1920,76,1989,56,2057,52C2125.7,48,2194,60,2263,56C2331.4,52,2400,32,2469,24C2537.1,16,2606,20,2674,24C2742.9,28,2811,32,2880,34C2948.6,36,3017,36,3086,30C3154.3,24,3223,12,3291,20C3360,28,3429,56,3497,64C3565.7,72,3634,60,3703,64C3771.4,68,3840,88,3909,86C3977.1,84,4046,60,4114,46C4182.9,32,4251,28,4320,32C4388.6,36,4457,48,4526,56C4594.3,64,4663,68,4731,72C4800,76,4869,80,4903,82L4937.1,84L4937.1,120L4902.9,120C4868.6,120,4800,120,4731,120C4662.9,120,4594,120,4526,120C4457.1,120,4389,120,4320,120C4251.4,120,4183,120,4114,120C4045.7,120,3977,120,3909,120C3840,120,3771,120,3703,120C3634.3,120,3566,120,3497,120C3428.6,120,3360,120,3291,120C3222.9,120,3154,120,3086,120C3017.1,120,2949,120,2880,120C2811.4,120,2743,120,2674,120C2605.7,120,2537,120,2469,120C2400,120,2331,120,2263,120C2194.3,120,2126,120,2057,120C1988.6,120,1920,120,1851,120C1782.9,120,1714,120,1646,120C1577.1,120,1509,120,1440,120C1371.4,120,1303,120,1234,120C1165.7,120,1097,120,1029,120C960,120,891,120,823,120C754.3,120,686,120,617,120C548.6,120,480,120,411,120C342.9,120,274,120,206,120C137.1,120,69,120,34,120L0,120Z"
      />
    </svg>
    <div class="part">
      <h1><fa class="icon" icon="code" />Projets</h1>
      <div class="list">
        <ProjectCard
          v-for="(card, i) in data"
          class="emitCard"
          :key="i"
          :imgColor="card.imgColor"
          :name="card.name"
          :shortDescription="card.shortDescription"
          :finishDate="card.finishDate"
          :workTime="card.workTime"
          :link="card.link"
          :url="card.url"
          :index="i"
        />
      </div>
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
#wave {
  margin-bottom: -10px;
}

.part {
  /*
  background: hsl(199, 100%, 65%);
  */
  background: rgb(245, 245, 245);

  margin-top: 0;
  padding-bottom: 25px;
}

.part .icon {
  color: hsl(199, 100%, 65%);
}

.part h1 {
  padding-top: 0;
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
  gap: 50px 20px;
}

@media screen and (max-width: 600px) {
  .part h1 {
    padding-top: 25px;
  }

  .list {
    display: flex;
    flex-direction: column;
    justify-content: center;
    flex-wrap: wrap;
    align-items: center;
    align-content: center;
    gap: 50px 0;
  }
}
</style>
