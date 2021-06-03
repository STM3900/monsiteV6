<template>
  <div class="part">
    <h1><fa class="icon" icon="user-circle" />Bonjour !</h1>
    <p>
      Je suis un étudiant en troisième année, à l'Epsi et alternant chez
      Erplain, je suis passionné par le web, où je prends plaisir à concevoir et
      réaliser des sites internet avec de plus en plus de fonctionnalités !
    </p>
  </div>
</template>

<script>
export default {
  name: "Presentation"
};
</script>

<style scoped>
div {
  background: #fdfffc;
  padding-bottom: 25px;
  padding-top: 5px;
}

div h1 {
  padding-top: 0;
}

div p {
  text-align: left;
  margin-top: 25px;
}

.part .icon {
  color: hsl(199, 100%, 65%);
}

/* responsive */

@media screen and (max-width: 600px) {
  div h1 {
    margin-top: 25px;
  }
}
</style>
