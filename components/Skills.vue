<template>
  <div class="part">
    <h1><fa class="icon" icon="clipboard-list" />Compétences (pas fini)</h1>
    <ul>
      <li v-for="(item, i) in skills" :key="i">{{ item }}</li>
    </ul>
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

.part .icon {
  color: hsl(199, 100%, 60%);
}

ul {
  width: 100%;
  margin-top: 25px;

  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
  align-content: center;
}

li {
  width: 50%;
  color: rgb(50, 50, 50);
}
</style>
