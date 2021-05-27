<template>
  <div id="tilt" ref="card" @mousemove="handleMove" @mouseleave="leave">
    <!--  Container for our block  -->
  </div>
</template>

<script>
export default {
  name: "Test",
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
      const yRotation = 20 * ((xVal - this.width / 2) / this.width);

      /* Calculate the rotation along the X-axis */
      const xRotation = -20 * ((yVal - this.height / 2) / this.height);

      /* Generate string for CSS transform property */
      const string =
        "perspective(500px) scale(1.1) rotateX(" +
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
    }
  }
};
</script>

<style scoped>
html {
  display: flex;
  justify-content: center;
  align-items: center;
  align-content: center;
  height: 100%;
}

/* Styles for the tilt block */
#tilt {
  display: block;
  height: 200px;
  width: 300px;
  background-color: grey;
  margin: 0 auto;
  transition: box-shadow 0.1s, transform 0.1s;

  /*
    * Adding image to the background
    * No relation to the hover effect.
    */
  background-image: url(http://unsplash.it/300/200);
  background-size: 100%;
  background-repeat: no-repeat;
}

#tilt:hover {
  box-shadow: 0px 0px 30px rgba(0, 0, 0, 0.6);
  cursor: pointer;
}
</style>
