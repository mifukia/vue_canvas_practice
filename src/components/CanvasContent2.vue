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
      stage: ""
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.stage = new createjs.Stage("canvas");
      this.drawShape();
    },
    drawShape() {
      const myShape = new createjs.Shape();
      this.stage.addChild(myShape);
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
