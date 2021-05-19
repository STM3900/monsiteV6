<template>
  <div class="content">
    <h1>
      <font-awesome-icon class="icon" :icon="['fas', 'clipboard-list']" />
      Compétences
    </h1>
  </div>
</template>

<script>
export default {
  name: "Competences"
};
</script>

<style scoped>
[class^="gb-"]:not(.gb-base-icon) {
  font-family: "Quicksand", sans-serif !important;
}

div {
  height: 100vh;
  width: 100%;

  color: white;
  background: #001e3d;
  padding-top: 5rem;
}

div h1 {
  font-size: 4rem;
}

div .container section h2 {
  font-size: 3rem;
  margin-bottom: 3rem;
}
</style>
