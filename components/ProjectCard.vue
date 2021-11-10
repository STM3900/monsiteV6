<template>
  <article
    ref="card"
    :class="isShowed ? 'show' : ''"
    @mousemove="handleMove"
    @mouseleave="leave"
    @mousedown="clicked"
    @mouseout="out"
    @mouseup="up"
    @click="showProject"
  >
    <aside>
      <img
        v-if="!checkIfColor"
        :src="require(`~/assets/img/${imgColor}.png`)"
        alt=""
      />
      <div v-else class="color" :style="'background: ' + imgColor + ';'">
        <fa class="icon-project" icon="code" />
      </div>
    </aside>
    <div class="content">
      <h2>{{ name }}</h2>
      <p class="finish-date">
        Terminé le <b>{{ finishDate }}</b>
      </p>
      <p class="work-time">
        Fait en <b>{{ workTime }}</b>
      </p>
      <section>
        <p>{{ shortDescription }}</p>
        <nav>
          <button
            v-show="link"
            @click="goToWebSite"
            :style="url ? '' : 'margin-bottom: 0px;'"
            @mouseover="isHover1 = true"
            @mouseleave="isHover1 = false"
          >
            <fa class="icon-card" icon="external-link-alt" />
            {{ testIfGitHub(link) }}
          </button>
          <button
            v-if="url"
            @click="$router.push(url)"
            @mouseover="isHover2 = true"
            @mouseleave="isHover2 = false"
          >
            En savoir plus
          </button>
        </nav>
      </section>
    </div>
  </article>
</template>

<script>
export default {
  name: "ProjectCard",
  props: {
    imgColor: String,
    name: String,
    shortDescription: String,
    finishDate: String,
    workTime: String,
    link: String,
    url: String,
    index: Number
  },
  data() {
    return {
      el: null,
      height: null,
      width: null,
      isShowed: false,
      isHover1: false,
      isHover2: false
    };
  },
  mounted() {
    /* Store the element in el */
    this.el = this.$refs.card;

    /* Get the height and width of the element */
    this.height = this.el.clientHeight;
    this.width = this.el.clientWidth;
  },
  computed: {
    checkIfColor() {
      return this.imgColor.includes("#");
    }
  },
  methods: {
    testIfGitHub(url) {
      return url.includes("github") ? "Voir le repo GitHub" : "Voir le site";
    },
    handleMove(e) {
      if (!this.isShowed) {
        /*
         * Get position of mouse cursor
         * With respect to the element
         * On mouseover
         */
        /* Store the x position */
        const xVal = e.layerX;
        /* Store the y position */
        const yVal = e.layerY;

        /*
         * Calculate rotation valuee along the Y-axis
         * Here the multiplier 20 is to
         * Control the rotation
         * You can change the value and see the results
         */
        const yRotation = 30 * ((xVal - this.width / 2) / this.width);

        /* Calculate the rotation along the X-axis */
        const xRotation = -30 * ((yVal - this.height / 2) / this.height);

        /* Generate string for CSS transform property */
        const string =
          "perspective(500px) scale(1.03) rotateX(" +
          xRotation +
          "deg) rotateY(" +
          yRotation +
          "deg)";

        /* Apply the calculated transformation */
        this.el.style.transform = string;
      }
    },
    leave() {
      if (!this.isShowed) {
        this.el.style.transform =
          "perspective(500px) scale(1) rotateX(0) rotateY(0)";
      }
    },
    clicked() {
      if (!this.isShowed) {
        this.el.style.transform =
          "perspective(500px) scale(0.98) rotateX(0) rotateY(0)";
      }
    },
    out() {
      this.el.style.transform =
        "perspective(500px) scale(1) rotateX(0) rotateY(0)";
    },
    up() {
      if (!this.isShowed) {
        this.el.style.transform =
          "perspective(500px) scale(1.03) rotateX(0) rotateY(0)";
      }
    },
    showProject() {
      if (!this.isHover1 && !this.isHover2) {
        this.isShowed = !this.isShowed;
        this.el.style.transform =
          "perspective(500px) scale(1) rotateX(0) rotateY(0)";
      }
    },
    goToWebSite() {
      window.open(this.link, "_blank");
    }
  }
};
</script>

<style scoped>
article {
  width: 300px;
  height: 95px;

  /* box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;*/
  border-radius: 5px;
  transition: all 0.3s, height 0.6s ease;
  background: white;
  box-shadow: 5px 5px 15px hsl(199, 100%, 45%),
    -5px -5px 15px hsl(199, 100%, 65%);
}

article:hover {
  box-shadow: 15px 15px 27px hsl(199, 100%, 45%),
    -15px -15px 27px hsl(199, 100%, 65%);
}

article div {
  height: 75px;
  overflow: hidden;
  transition: 0.3s;
  transition: 0.6s ease;
}

article div section {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  align-content: center;

  height: 300px;
  margin-left: 20px;
  margin-right: 20px;
}

article div section button {
  border: none;
  font-family: "Quicksand", sans-serif;
  font-size: 16px;
  width: 100%;
  /* haut | droit | bas | gauche */
  padding: 10px 20px;
  background: hsl(199, 100%, 65%);
  color: white;
  border-radius: 5px;
  transition: 0.3s;
}

article div section button:first-child {
  margin-bottom: 15px;
  background: rgb(240, 240, 240);

  color: rgb(50, 50, 50);
  border: solid 1px white;
  width: 100%;
}

nav {
  width: 100%;
}

.icon-card {
  margin-right: 5px;
  color: rgb(150, 150, 150);
}

article div section button:hover {
  cursor: pointer;
  transform: scale(0.99);
}

article div section button:first-child:hover {
  background: rgb(240, 240, 240);
}

article div section button:active {
  transform: scale(0.98);
}

.show {
  height: 500px;
  transition: all 0.3s, height 0.6s ease;
  margin-bottom: 10px;
}

.show .content {
  height: 500px;
  transition: 0.6s ease;
}

.show div section {
  transition: 0.3s;
}

article:hover {
  cursor: pointer;
}

article:active {
  transform: perspective(500px) scale(0.9) rotateX(0) rotateY(0);
}

article aside {
  position: absolute;
  width: 300px;

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
}

article img {
  position: absolute;
  height: 70px;
  border: solid #fdfffc 6px;
  border-radius: 50%;
  z-index: 99999;
  overflow: visible;
  background: white;
}

article .color {
  position: absolute;
  height: 70px;
  width: 70px;
  border: solid #fdfffc 6px;
  border-radius: 50%;
  z-index: 99999;
  overflow: visible;

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
}

article .color .icon-project {
  color: white;
  font-size: 22px;
}

article h2 {
  font-size: 20px;
  padding-top: 40px;
  padding-bottom: 25px;
  padding-left: 20px;
  padding-right: 20px;
  text-align: center;
  color: rgb(50, 50, 50);
  font-weight: normal;
}

article .finish-date {
  padding-left: 20px;
  padding-right: 20px;
  margin-top: 15px;
  margin-bottom: 0;
}

article .work-time {
  padding-left: 20px;
  padding-right: 20px;
  margin-bottom: 20px;
  margin-top: 3px;
}

@media screen and (max-width: 1175px) {
  article {
    width: 400px;
  }

  article aside {
    width: 400px;
  }
}

@media screen and (max-width: 1035px) {
  article {
    width: 350px;
  }

  article aside {
    width: 350px;
  }
}

@media screen and (max-width: 790px) {
  article {
    width: 100%;
  }

  article aside {
    width: 100%;
  }
}

@media screen and (max-width: 600px) {
  article {
    width: 100%;
    height: 75px;
  }

  article div section {
    margin-left: 30px;
  }

  article aside {
    width: 100px;
  }

  article img {
    height: 50px;
  }

  article h2 {
    font-size: 18px;
    padding-top: 30px;
    padding-left: 30px;
    text-align: left;
  }

  article .finish-date {
    padding-left: 30px;
    padding-right: 30px;
  }

  article .work-time {
    padding-left: 30px;
    padding-right: 30px;
  }

  article .color {
    height: 50px;
    width: 50px;
  }

  article .color .icon-project {
    font-size: 16px;
  }

  article div section {
    margin-right: 30px;
    height: 280px;
  }

  article div section button {
    font-size: 14px;
  }

  .show {
    height: 450px;
  }

  .show .content {
    height: 450px;
  }
}
</style>
