<template>
  <div class="part">
    <aside>
      <h1><fa class="icon" icon="user-circle" />Bonjour !</h1>
      <p>
        Je suis un étudiant en quatrième année à l'Epsi et alternant à
        STMicroelectronics, je suis passionné par le développement web, où je
        prends plaisir à concevoir et réaliser des sites avec de plus en plus de
        fonctionnalités !
      </p>
    </aside>
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
