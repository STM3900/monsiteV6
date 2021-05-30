<template>
  <div class="part">
    <h1><fa class="icon" icon="address-book" />Parcours / Expériences</h1>
    <article>
      <section>
        <h2>Scolaire</h2>
        <timeline>
          <timeline-title
            v-for="(item, i) in schoolTab"
            :key="i"
            class="timeline-title-custom"
            bg-color="hsl(199, 100%, 65%)"
          >
            <h4>
              {{ item.beginDate }} -
              {{ item.endDate ? item.endDate : "Présent" }}
            </h4>
            <h3>{{ item.label }}</h3>
            <h5>{{ item.school }}</h5>
          </timeline-title>
        </timeline>
      </section>
      <section>
        <h2>Professionel</h2>
        <timeline>
          <timeline-title
            v-for="(item, j) in workTab"
            :key="j"
            class="timeline-title-custom"
            bg-color="hsl(199, 100%, 75%)"
          >
            <h4>
              {{ item.beginDate }} -
              {{ item.endDate ? item.endDate : "Présent" }}
            </h4>
            <h3>{{ item.label }}</h3>
            <h5>{{ item.work }}</h5>
          </timeline-title>
        </timeline>
      </section>
    </article>
  </div>
</template>

<script>
import { Timeline, TimelineItem, TimelineTitle } from "vue-cute-timeline";

export default {
  name: "GlobalPath",
  components: { Timeline, TimelineItem, TimelineTitle },
  props: {
    schoolTab: Array,
    workTab: Array
  }
};
</script>

<style scoped>
div {
  background: #fdfffc;
}

.part .icon {
  color: hsl(199, 100%, 65%);
}

.timeline-title-custom {
  display: block;
  font-family: "Quicksand", sans-serif;
}

.timeline-title-custom:hover {
  cursor: auto;
}

article {
  margin-top: 25px;
  margin-bottom: 100px;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  align-content: center;
}

article section {
  width: 50%;
}

article section h2 {
  padding-bottom: 10px;
  color: rgb(50, 50, 50);
}

article section h3 {
  font-size: 20px;
}

article section h4 {
  font-size: 16px;
  font-weight: normal;
}

article section h5 {
  font-size: 14px;
  font-weight: normal;
  color: rgb(150, 150, 150);
}

/*
    <timeline>
      <timeline-title>title</timeline-title>
      <timeline-item bg-color="#9dd8e0">item1</timeline-item>
      <timeline-item :hollow="true">item2</timeline-item>
    </timeline>
*/
</style>
