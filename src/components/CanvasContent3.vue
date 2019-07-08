<template>
  <div class="canvasArea">
    <canvas id="canvas" width="240" height="180"></canvas>
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
      this.addBitmap();
      this.stage.addChild(this.myBitmap);
      createjs.Ticker.addEventListener("tick", this.stage);
    },
    addBitmap() {
      this.myBitmap = new createjs.Bitmap("/img/pen.png");
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
