<template>
  <article
    ref="card"
    @mousemove="handleMove"
    @mouseleave="leave"
    @mousedown="clicked"
    @mouseout="out"
    @mouseup="up"
  >
    <aside>
      <img :src="img" alt="" />
    </aside>
    <h2>{{ name }}</h2>
  </article>
</template>

<script>
export default {
  name: "ProjectCard",
  props: {
    img: String,
    name: String
  },
  data() {
    return {
      el: null,
      height: null,
      width: null
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
  methods: {
    handleMove(e) {
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
    },
    leave() {
      this.el.style.transform =
        "perspective(500px) scale(1) rotateX(0) rotateY(0)";
    },
    clicked() {
      this.el.style.transform =
        "perspective(500px) scale(0.98) rotateX(0) rotateY(0)";
    },
    out() {
      this.el.style.transform =
        "perspective(500px) scale(1) rotateX(0) rotateY(0)";
    },
    up() {
      this.el.style.transform =
        "perspective(500px) scale(1.05) rotateX(0) rotateY(0)";
    }
  }
};
</script>

<style scoped>
article {
  width: 300px;

  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  border-radius: 5px;
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
}

article h2 {
  font-size: 23px;
  padding-top: 40px;
  padding-bottom: 25px;
  padding-left: 20px;
  padding-right: 20px;
  text-align: center;
  color: rgb(50, 50, 50);
}

article p {
  padding: 20px;
}
</style>
