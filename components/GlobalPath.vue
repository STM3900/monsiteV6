<template>
  <div class="part">
    <h1><fa class="icon" icon="address-book" />Parcours / Expériences</h1>
    <article>
      <section>
        <h2>Scolaire</h2>
        <timeline>
          <timeline-title>
            <h4>2018 - Present</h4>
            <h3>Master en informatique</h3>
            <h5>Epsi Grenoble la pire école</h5>
          </timeline-title>
          <timeline-item bg-color="#9dd8e0">item1</timeline-item>
          <timeline-item :hollow="true">item2</timeline-item>
        </timeline>
      </section>
      <section>
        <h2>Professionel</h2>
      </section>
    </article>
  </div>
</template>

<script>
import { Timeline, TimelineItem, TimelineTitle } from "vue-cute-timeline";

export default {
  name: "GlobalPath",
  components: { Timeline, TimelineItem, TimelineTitle }
};
</script>

<style scoped>
div {
  background: #fdfffc;
}

div h1 .icon {
  margin-right: 20px;
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
  flex-grow: 1;
}

article section h2 {
  padding-bottom: 10px;
}

/*
    <timeline>
      <timeline-title>title</timeline-title>
      <timeline-item bg-color="#9dd8e0">item1</timeline-item>
      <timeline-item :hollow="true">item2</timeline-item>
    </timeline>
*/
</style>
