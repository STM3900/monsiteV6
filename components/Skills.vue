<template>
  <div class="part">
    <h1><fa class="icon" icon="clipboard-list" />Compétences (pas fini)</h1>
    <article>
      <section v-for="(item, i) in skills" :key="i">
        <fa class="icon-skill" :icon="item.icon" />
        <h2>{{ item.label }}</h2>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  name: "Skills",
  props: {
    skills: Array
  }
};
</script>

<style scoped>
div {
  background: #fdfffc;
}

.part h1 {
  margin-bottom: 25px;
}

.part .icon {
  color: hsl(199, 100%, 65%);
}

article {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  align-content: center;
}

article section {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
  align-content: center;
}

article section h2 {
  font-size: 20px;
  font-weight: normal;
}

article section .icon-skill {
  font-size: 25px;
}
</style>
