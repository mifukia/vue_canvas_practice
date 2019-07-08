<template>
  <div class="canvasArea">
    <canvas id="canvas" width="480" height="360"></canvas>
  </div>
</template>

<script>
export default {
  name: "CanvasContent3",
  data() {
    return {};
  },
  mounted() {
    this.init();
  },
  computed: {
    canvasHeight() {
      return this.canvas.height;
    },
    canvasWidth() {
      return this.canvas.width;
    }
  },
  methods: {
    init() {
      this.canvas = document.getElementById("canvas");
      this.stage = new createjs.Stage(canvas);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.canvasArea {
  margin-top: 100px;
}
canvas {
  border: 1px solid #ccc;
}
</style>
