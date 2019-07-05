<template>
  <div class="canvasArea">
    <canvas id="myCanvas" width="240" height="180"></canvas>
  </div>
</template>

<script>
export default {
  name: "CanvasContent",
  mounted() {
    this.canvasInit();
  },
  methods: {
    canvasInit() {
      const canvasElement = document.getElementById("myCanvas");
      const context2D = canvasElement.getContext("2d");
      context2D.fillRect(10, 10, 100, 100);
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
  border: 1px solid #333;
}
</style>
