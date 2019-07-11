<template>
  <div class="canvasArea">
    <canvas id="canvas3" width="480" height="360"></canvas>
  </div>
</template>

<script>
export default {
  name: "CanvasContent4",
  data() {
    return {
      stage: "",
      radius: 40
    };
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
      this.canvas = document.getElementById("canvas3");
      this.stage = new createjs.Stage(this.canvas);
      const myShape = this.createShape(
        this.canvasWidth / 2,
        this.canvasHeight / 2
      );
      const myShape2 = this.createShape(180, 120);
      this.stage.addChild(myShape, myShape2);
      this.stage.update();
    },
    createShape(x, y) {
      const myShape = new createjs.Shape();
      myShape.x = x;
      myShape.y = y;
      myShape.addEventListener("pressmove", this.drag);
      this.drawPolyStar(myShape.graphics);
      return myShape;
    },
    drawPolyStar(myGraphics) {
      const randamNumber = Math.floor(Math.random() * 0xffffff);
      const randamColor = createjs.Graphics.getRGB(randamNumber);
      myGraphics
        .beginStroke("blue")
        .beginFill(randamColor)
        .drawPolyStar(0, 0, this.radius, 5, 0.6, -90);
    },
    drag(eventObject) {
      console.log(eventObject);
      const myShape = eventObject.target;
      myShape.x = eventObject.stageX;
      myShape.y = eventObject.stageY;
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
