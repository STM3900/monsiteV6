<template>
  <div class="part">
    <h1><fa class="icon" icon="code" />Projets</h1>
    <div class="list">
      <ProjectCard
        v-for="(card, i) in data"
        :key="i"
        :img="card.img"
        :name="card.name"
      />
    </div>
  </div>
</template>

<script>
import ProjectCard from "./ProjectCard";

export default {
  name: "Projects",
  components: { ProjectCard },
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
  }
};
</script>

<style scoped>
.part {
  background: #fdfffc;
}

.part h1 {
  margin-bottom: 60px;
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

/* 
      <ProjectCard
        v-for="(card, i) in data"
        :key="i"
        :img="card.img"
        :name="card.name"
      />

      import ProjectCard from "./ProjectCard";
*/
</style>
