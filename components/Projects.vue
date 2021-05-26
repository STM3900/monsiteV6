<template>
  <div class="part">
    <h1><fa class="icon" icon="code" />Projets</h1>
    <div class="list">
      <article v-for="(project, i) in data" :key="i">
        <img :src="project.background" alt="" />
        <h2>{{ project.name }}</h2>
        <p>{{ project.description }}</p>
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
          name: "MusicHours 1",
          url: "musichours",
          category: "projet perso",
          link: "https://theomigeat.com/MusicHours/",
          img: "https://theomigeat.com/medias/images/MusicHoursLogo.png",
          background: "https://theomigeat.com/medias/images/MusicHours.png",
          finishDate: "24/12/19",
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
          name: "MusicHours 2",
          url: "musichours",
          category: "projet perso",
          link: "https://theomigeat.com/MusicHours/",
          img: "https://theomigeat.com/medias/images/MusicHoursLogo.png",
          background: "https://theomigeat.com/medias/images/MusicHours.png",
          finishDate: "24/12/19",
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
          name: "MusicHours 3",
          url: "musichours",
          category: "projet perso",
          link: "https://theomigeat.com/MusicHours/",
          img: "https://theomigeat.com/medias/images/MusicHoursLogo.png",
          background: "https://theomigeat.com/medias/images/MusicHours.png",
          finishDate: "24/12/19",
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
          name: "MusicHours 4",
          url: "musichours",
          category: "projet perso",
          link: "https://theomigeat.com/MusicHours/",
          img: "https://theomigeat.com/medias/images/MusicHoursLogo.png",
          background: "https://theomigeat.com/medias/images/MusicHours.png",
          finishDate: "24/12/19",
          workTime: "72h19m",
          description:
            "MusicHours est un site vous permettant, à partir d'une ville de votre choix, d'avoir une musique et un thème s'adaptant à l'heure et à la météo de celle-ci !",
          objectives: [
            "Expérimenter de nouvelles choses en JS",
            "Surpasser mes limites en CSS",
            "Se connecter à une API et l'utiliser"
          ],
          languages: ["HTML / CSS", "JS", "VSCode / GitHub"]
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

.list {
  margin-top: 25px;
  width: 100%;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
  align-content: center;
  gap: 40px 0;
}

.list article {
  width: 300px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);

  border-radius: 5px;
  transition: 0.3s;
}

.list article img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.list article h2 {
  font-size: 26px;
  padding: 20px;
}

.list article p {
  padding: 20px;
}
</style>
