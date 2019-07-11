<template>
  <div class="canvasArea">
    <canvas id="canvas" width="480" height="360"></canvas>
  </div>
</template>

<script>
export default {
  name: "CanvasContent2",
  data() {
    return {
      stage: "",
      myShape: "",
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
      this.canvas = document.getElementById("canvas");
      this.stage = new createjs.Stage(this.canvas);
      this.createShape();
      //this.drawCircle(this.myShape.graphics);
      this.drawPolyStar(this.myShape.graphics);
      this.setTween(this.myShape);
      createjs.Ticker.addEventListener("tick", this.stage);
    },
    createShape() {
      this.myShape = new createjs.Shape();
      this.setRandom();
      this.myShape.y = 0 - this.radius; //this.canvas.height / 2;
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
        .drawPolyStar(0, 0, this.radius, 5, 0.6, -90);
      this.stage.update();
    },
    rotate() {
      this.myShape.rotation += 5;
      this.stage.update();
    },
    setTween(target) {
      createjs.Tween.get(target, {
        loop: true
      })
        .to(
          {
            y: this.canvasHeight - this.radius,
            rotation: 360
          },
          5000,
          createjs.Ease.bounceOut
        )
        .wait(1000)
        .to({ alpha: 0 }, 2500, createjs.Ease.circIn)
        .call(this.setRandom);
    },
    setRandom() {
      this.myShape.x = Math.random() * this.canvasWidth;
      this.drawPolyStar(this.myShape.graphics);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.canvasArea {
  margin-top: 50px;
}
canvas {
  border: 1px solid #ccc;
}
</style>
