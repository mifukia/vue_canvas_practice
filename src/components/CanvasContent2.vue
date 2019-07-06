<template>
  <div class="canvasArea">
    <canvas id="canvas" width="240" height="180"></canvas>
  </div>
</template>

<script>
export default {
  name: "CanvasContent2",
  data() {
    return {
      stage: "",
      myShape: ""
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.canvas = document.getElementById("canvas");
      this.stage = new createjs.Stage(canvas);
      this.createShape();
      //this.drawCircle(this.myShape.graphics);
      this.drawPolyStar(this.myShape.graphics);
    },
    createShape() {
      this.myShape = new createjs.Shape();
      this.myShape.x = this.canvas.width / 2;
      this.myShape.y = this.canvas.height / 2;
      this.stage.addChild(this.myShape);
    },
    drawCircle(myGraphics) {
      myGraphics
        .beginStroke("blue")
        .beginFill("#00FFFF")
        .drawCircle(0, 0, 40);
      this.stage.update();
    },
    drawPolyStar(myGraphics) {
      const randamNumber = Math.floor(Math.random() * 0xffffff);
      const randamColor = createjs.Graphics.getRGB(randamNumber);
      myGraphics
        .beginStroke("blue")
        .beginFill(randamColor)
        .drawPolyStar(0, 0, 40, 5, 0.6, -90);
      this.stage.update();
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
