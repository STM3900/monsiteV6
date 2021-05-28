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
      <img v-if="checkIfColor" :src="imgColor" alt="" />
      <div v-else class="color" :style="'background: ' + imgColor + ';'">
        <fa class="icon-project" icon="code" />
      </div>
    </aside>
    <div>
      <h2>{{ name }}</h2>
      <p class="finish-date">
        Terminé le <b>{{ finishDate }}</b>
      </p>
      <p class="work-time">
        Fait en <b>{{ workTime }}</b>
      </p>
      <section>
        <p>{{ description }}</p>
        <nav>
          <button @click="goToWebSite">Voir le site</button>
          <button>En savoir plus</button>
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
    description: String,
    finishDate: String,
    workTime: String,
    link: String,
    index: Number
  },
  data() {
    return {
      el: null,
      height: null,
      width: null,
      isShowed: false
    };
  },
  mounted() {
    /* Store the element in el */
    this.el = this.$refs.card;
    console.log(this.el.clientWidth);

    /* Get the height and width of the element */
    this.height = this.el.clientHeight;
    this.width = this.el.clientWidth;
  },
  computed: {
    checkIfColor() {
      return this.imgColor.includes(".");
    }
  },
  methods: {
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
          "perspective(500px) scale(1.05) rotateX(" +
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
          "perspective(500px) scale(1.05) rotateX(0) rotateY(0)";
      }
    },
    showProject() {
      this.isShowed = !this.isShowed;
      this.el.style.transform =
        "perspective(500px) scale(1) rotateX(0) rotateY(0)";
      this.$emit("toggle", this.index, this.isShowed);
    },
    goToWebSite() {
      window.location = this.link;
    }
  }
};
</script>

<style scoped>
article {
  width: 300px;
  height: 95px;

  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  border-radius: 5px;
  transition: all 0.3s, height 0.6s ease;
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
  background: rgb(50, 50, 50);
  color: white;
  border-radius: 5px;
  transition: 0.3s;
}

article div section button:first-child {
  margin-bottom: 15px;
  background: white;
  color: rgb(50, 50, 50);
  border: solid 1px white;
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

.show div {
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
  font-size: 23px;
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
</style>
