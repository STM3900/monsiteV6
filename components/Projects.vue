<template>
  <div class="part">
    <h1><fa class="icon" icon="code" />Projets</h1>
    <div class="list">
      <article v-for="(project, i) in data" :key="i" class="profileCard">
        <aside>
          <img :src="project.img" alt="" />
        </aside>

        <h2>{{ project.name }}</h2>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  name: "Projects",
  data() {
    return {
      data: [
        {
          name: "MusicHours",
          url: "musichours",
          category: "projet perso",
          link: "https://theomigeat.com/MusicHours/",
          img: "https://theomigeat.com/medias/images/MusicHoursLogo.png",
          background: "https://theomigeat.com/medias/images/MusicHours.png",
          finishDate: "24/12/2020",
          workTime: "72h19m",
          description:
            "MusicHours est un site vous permettant, à partir d'une ville de votre choix, d'avoir une musique et un thème s'adaptant à l'heure et à la météo de celle-ci !",
          objectives: [
            "Expérimenter de nouvelles choses en JS",
            "Surpasser mes limites en CSS",
            "Se connecter à une API et l'utiliser"
          ],
          languages: ["HTML / CSS", "JS", "VSCode / GitHub"]
        },
        {
          name: "Lazublog",
          url: "lazublog",
          category: "projet perso",
          link: "https://theomigeat.com/LazuBlog/",
          img: "https://theomigeat.com/medias/images/lazulogo.png",
          background: "https://theomigeat.com/medias/images/lazublog.jpg",
          finishDate: "20/03/2020",
          workTime: "30h40m",
          description:
            'Conçu pour la sortie du jeu "Animal Crossing : New Horizon" Lazublog est un petit blog où je partage mon aventure sur le jeu, avec une pointe de fiction !',
          objectives: [
            "Apprendre à utiliser une base de données (ajout, modification, et suppression de contenu)",
            "Mettre à l'œuvre ce que j'ai pu apprendre durant mon stage (animations en css et javascript)",
            "Me remettre à l'écriture"
          ],
          languages: ["HTML / CSS", "JS", "SQL", "PHP", "VSCode / GitHub"]
        },
        {
          name: "Breaking Bot",
          url: "breakingbot",
          category: "projet perso",
          link: "https://mrgove10.itch.io/breaking-bots",
          img: "https://theomigeat.com/medias/images/BrLogo.png",
          background: "https://theomigeat.com/medias/images/Br.jpg",
          finishDate: "09/02/2020",
          workTime: "2 Jours Non-Stop",
          description:
            "Créé pendant la Scientific Game Jam de 2020, dans une équipe de 8, Breacking Bot nous met dans la peau de Stein, le premier robot géologuue qui doit dater les gisements métaliques en cherchant et analysant un minerai datable dans les roches Monazite avant que celui-ci soit hors service !",
          objectives: [
            "Faire un jeu fonctionnel en moins de 48h",
            "Rencontrer des personnes talentueuses dans des dommaines autre que l'informatique",
            "Passer un moment inoubliable"
          ],
          languages: ["C#", "Unity", "VSCode / GitHub"]
        },
        {
          name: "Apocalypse Not Now",
          url: "ann",
          category: "projet perso",
          link: "https://manfredhq.itch.io/apocalypsenotnow",
          img: "https://theomigeat.com/medias/images/ANNLogo.png",
          background: "https://theomigeat.com/medias/images/ANN.jpg",
          finishDate: "02/02/2020",
          workTime: "2 Jours Non-Stop",
          description:
            "Créé pendant la Global Game Jam de 2020, dans une équipe de 5, Apocalypse Not Now est un jeu dont le but est de surmontrer les nombreux cataclysmes étant présent sur la Terre",
          objectives: [
            "Faire un jeu fonctionnel en seulement 48h",
            "Permettre de savoir si mon niveau en C# / Unity s'est amélioré"
          ],
          languages: ["C#", "Unity", "VSCode / GitHub"]
        }
      ]
    };
  },
  mounted() {}
};
</script>

<style scoped>
.part {
  background: #fdfffc;
}

.part h1 {
  margin-bottom: 50px;
}

.list {
  margin-top: 25px;
  width: 100%;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
  align-content: center;
  gap: 50px 0;
}

.list article {
  width: 300px;
  /*
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  box-shadow: 0 20px 40px -14px rgba(0, 0, 0, 0.25);
  border: solid 1px rgb(50, 50, 50);
  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  */

  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  border-radius: 5px;
  transition: 0.3s;
}

.list article aside {
  position: absolute;
  width: 300px;

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
}

.list article img {
  position: absolute;
  height: 70px;
  border: solid #fdfffc 6px;
  border-radius: 50%;
}

.list article h2 {
  font-size: 23px;
  padding-top: 40px;
  padding-bottom: 25px;
  padding-left: 20px;
  padding-right: 20px;
  text-align: center;
  color: rgb(50, 50, 50);
}

.list article p {
  padding: 20px;
}
</style>
