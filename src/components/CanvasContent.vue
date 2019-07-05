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
  computed: {
    context2D() {
      return this.canvasElement.getContext("2d");
    }
  },
  methods: {
    canvasInit() {
      this.canvasElement = document.getElementById("myCanvas");
      this.draw(this.context2D);
    },
    draw(context) {
      context.beginPath();
      context.strokeStyle = "#0000ff";
      context.fillStyle = "#00ffff";
      context.closePath();
      // this.drawRect(context, 10, 10, 100, 100);
      this.drawStar(context, 100, 100, 5, 80, 30);
      context.fill();
      context.stroke();
    },
    drawRect(context, nX, nY, nWidth, nHeight) {
      context.moveTo(nX, nY);
      context.lineTo(nX + nWidth, nY);
      context.lineTo(nX + nWidth, nY + nHeight);
      context.lineTo(nX, nY + nHeight);
      context.lineTo(nX, nY);
    },
    drawStar(context, nX, nY, numVertex, longRadius, shortRadius) {
      const nTheta = Math.PI / numVertex;
      let nRadians = -Math.PI / 2;

      context.moveTo(nX, nY - longRadius);

      for (let i = 1; i <= numVertex; i++) {
        nRadians += nTheta;
        context.lineTo(
          shortRadius * Math.cos(nRadians) + nX,
          shortRadius * Math.sin(nRadians) + nY
        );
        nRadians += nTheta;
        context.lineTo(
          longRadius * Math.cos(nRadians) + nX,
          longRadius * Math.sin(nRadians) + nY
        );
      }
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
