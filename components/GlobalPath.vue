<template>
  <div class="part">
    <div class="border-part">
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
          <h2>Professionnel</h2>
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
          <h2>Professionnel bénévole</h2>
          <timeline>
            <timeline-title
              v-for="(item, j) in voluntaryTab"
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
  </div>
</template>

<script>
import { Timeline, TimelineItem, TimelineTitle } from "vue-cute-timeline";

export default {
  name: "GlobalPath",
  components: { Timeline, TimelineItem, TimelineTitle },
  props: {
    schoolTab: Array,
    workTab: Array,
    voluntaryTab: Array
  }
};
</script>

<style scoped>
div {
  background: #eb000000;
}

div h1 {
  font-size: 32px;
}

aside {
  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  padding: 20px 40px;
  border-radius: 20px;
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
  margin-bottom: 25px;

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

/* responsive */

@media screen and (max-width: 600px) {
  article section h2 {
    font-size: 18px;
  }

  article section h3 {
    font-size: 17px;
  }

  article section h4 {
    font-size: 14px;
  }

  article section h5 {
    font-size: 12px;
  }

  article {
    margin-top: 25px;
    margin-bottom: 25px;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    align-content: center;
  }

  article section {
    width: 100%;
  }
}
</style>
