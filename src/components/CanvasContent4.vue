<template>
  <div class="canvasArea">
    <p>
      <button @click="addShape">add</button>
    </p>
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
      myShape.addEventListener("mousedown", this.startDrag);
      this.drawPolyStar(myShape.graphics);
      return myShape;
    },
    addShape() {
      //shapeを追加する(マイオリジナル)
      const myNewShape = this.createShape(
        this.canvasWidth / 2,
        this.canvasHeight / 2
      );
      this.stage.addChild(myNewShape);
      this.stage.update();
    },
    drawPolyStar(myGraphics) {
      const randamNumber = Math.floor(Math.random() * 0xffffff);
      const randamColor = createjs.Graphics.getRGB(randamNumber);
      myGraphics
        .beginStroke("blue")
        .beginFill(randamColor)
        .drawPolyStar(0, 0, this.radius, 5, 0.6, -90);
    },
    startDrag(eventObject) {
      //イベントリスナー追加
      const myShape = eventObject.target;
      myShape.addEventListener("pressmove", this.drag);
      myShape.addEventListener("pressup", this.stopDrag);
      //クリックした位置とシェイプの位置のずれを記憶する(*1)
      myShape.offset_x = myShape.x - eventObject.stageX;
      myShape.offset_y = myShape.y - eventObject.stageY;
    },
    stopDrag(eventObject) {
      //イベントリスナー削除
      const myShape = eventObject.target;
      myShape.removeEventListener("pressmove", this.drag);
      myShape.removeEventListener("pressup", this.stopDrag);
    },
    drag(eventObject) {
      //console.log(eventObject);
      const myShape = eventObject.target;
      //(*1)
      myShape.x = eventObject.stageX + myShape.offset_x;
      myShape.y = eventObject.stageY + myShape.offset_y;
      this.stage.update();
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
