<template>
  <div class="part">
    <h1><fa class="icon" icon="id-card" />Contact</h1>
    <article>
      <section
        v-for="(item, i) in contacts"
        :key="i"
        @click="goToWebSite(item.link)"
      >
        <fa
          class="icon-contact"
          :icon="item.icon"
          :style="{ color: item.color }"
        />
        <h2>{{ item.label }}</h2>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      contacts: [
        {
          label: "LinkedIn",
          icon: ["fab", "linkedin-in"],
          color: "#007bb6",
          link: "https://www.linkedin.com/in/theo-migeat/"
        },
        {
          label: "theo.migeat@epsi.fr",
          icon: "envelope",
          color: "#006fc0",
          link: "mailto:theo.migeat@epsi.fr"
        },
        {
          label: "GitHub",
          icon: ["fab", "github"],
          color: "#5b217b",
          link: "https://github.com/STM3900"
        }
      ]
    };
  },
  methods: {
    goToWebSite(link) {
      link.includes("mailto")
        ? (window.location = link)
        : window.open(link, "_blank");
    }
  }
};
</script>

<style scoped>
.part {
  background: hsl(199, 100%, 65%);
  padding-bottom: 70px;
}

.part h1 {
  color: white;
  margin-bottom: 25px;
}

.part article {
  margin-top: 20px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  align-content: center;
  gap: 25px 25px;
}

.part article section {
  width: 30%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
  background: white;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 15px 15px 27px hsl(199, 100%, 45%),
    -15px -15px 27px hsl(199, 100%, 65%);
  transition: 0.3s;
}

.part article section:hover {
  cursor: pointer;
  transform: rotate(1deg);
}

.part article section:active {
  transform: rotate(1deg) scale(0.98);
}

.part article section h2 {
  font-size: 20px;
  color: rgb(50, 50, 50);
  font-weight: normal;
}

.part article section .icon-contact {
  font-size: 25px;
  margin-right: 10px;
}

@media screen and (max-width: 1050px) {
  .part article {
    flex-wrap: wrap;
    justify-content: flex-start;
  }

  .part article section {
    width: 48%;
  }
}

@media screen and (max-width: 866px) {
  .part article {
    flex-direction: column;
    gap: 25px 0;
  }

  .part article section {
    width: 100%;
    justify-content: space-between;
    flex-direction: row-reverse;
  }

  .part article section h2 {
    font-size: 18px;
  }

  .part article section .icon-contact {
    font-size: 20px;
    margin-right: 0;
  }
}
</style>
