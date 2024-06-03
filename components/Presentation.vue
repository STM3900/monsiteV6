<template>
  <div class="part">
    <div class="border-part">
      <h1><fa class="icon" icon="user-circle" />Bonjour !</h1>
      <p>
        Je suis passionné de développement web, où je prends plaisir à concevoir
        et réaliser des sites variés. Titulaire d'un titre RNCP niveau 7 -
        Expert en informatique et systèmes d'information, je suis toujours
        curieux d'apprendre et d'explorer de nouvelles technologies !
      </p>
    </div>
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
  padding-bottom: 50px;
  padding-top: 5px;
}

div h1 {
  padding-top: 0;
  font-size: 32px;
}

div p {
  text-align: left;
  margin-top: 25px;
}

.part .icon {
  color: hsl(199, 100%, 65%);
}

aside {
  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  padding: 40px;
  border-radius: 20px;
}

/* responsive */

@media screen and (max-width: 600px) {
  div h1 {
    margin-top: 25px;
  }
}
</style>
