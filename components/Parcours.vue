<template>
  <div class="content">
    <h1>
      <font-awesome-icon class="icon" :icon="['fas', 'scroll']" /> Parcours /
      Expériences
    </h1>
    <article class="container">
      <section>
        <h2>Scolaire</h2>
        <!-- Latest update -->
        <vue-timeline-update
          date="2018 - en cours"
          title="Master en informatique"
          description="EPSI Grenoble"
          category="école"
          icon="school"
          color="blue"
        />

        <!-- Another update -->
        <vue-timeline-update
          date="2015 - 2018"
          title="Baccalauréat STI2D"
          description="Lycée Polyvalent Vaucanson <br> <span style='font-size: 1.5rem;'><i>Mention assez bien<i></span>"
          category="lycée"
          icon="school"
          color="blue"
        />
      </section>
      <section>
        <h2>Professionel</h2>
        <!-- Latest update -->
        <vue-timeline-update
          date="Sep 2020 - en cours"
          title="Stage en développement web"
          description="Agence Cerf à Lunettes"
          category="stage"
          icon="code"
          color="blue"
        />

        <!-- Latest update -->
        <vue-timeline-update
          date="Jan - Fev 2020"
          title="Stage en développement web"
          description="Agence Cerf à Lunettes"
          category="stage"
          icon="code"
          color="blue"
        />

        <!-- Another update -->
        <vue-timeline-update
          date="Mai - Jun 2019"
          title="Stage en développement web"
          description="Auphys Technologie "
          category="stage"
          icon="code"
          color="blue"
        />
      </section>
    </article>
  </div>
</template>

<script>
export default {
  name: "Parcours"
};
</script>

<style scoped>
[class^="gb-"]:not(.gb-base-icon) {
  font-family: "Quicksand", sans-serif !important;
}

div {
  width: 100%;

  color: white;
  background: #061729;
  padding-bottom: 5rem;
}

div h1 {
  font-size: 4rem;
}

div .container section h2 {
  font-size: 3rem;
  margin-bottom: 3rem;
}

div .container {
  margin-top: 6rem;
  margin-left: 3rem;
  margin-right: 3rem;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  align-content: center;
}

div .container section {
  width: 45%;
  background: #0a223b;
  padding: 3rem;
  border-radius: 5px;
}
</style>
