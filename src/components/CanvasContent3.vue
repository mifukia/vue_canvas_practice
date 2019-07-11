<template>
  <div class="canvasArea">
    <canvas id="canvas2" width="400" height="300"></canvas>
  </div>
</template>

<script>
export default {
  name: "CanvasContent3",
  data() {
    return {
      files: ["/img/000.png", "/img/001.png", "/img/002.png"],
      margin: 10,
      nextX: 10
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
      this.canvas = document.getElementById("canvas2");
      this.stage = new createjs.Stage(this.canvas);
      this.addBitmap();
    },
    addBitmap() {
      const queue = new createjs.LoadQueue(true); // [1]インスタンスの作成

      this.manifest = this.files.map(file => {
        const myBitmap = new createjs.Bitmap(file);
        myBitmap.y = 20;
        this.stage.addChild(myBitmap);
        return { src: file, data: myBitmap };
      });

      queue.addEventListener("fileload", this.draw); // [2]読み込み待ち
      queue.loadManifest(this.manifest); // [3]読み込み開始
    },
    draw(eventObject) {
      const item = eventObject.item;
      const myBitmap = item.data;
      const myImage = eventObject.result;
      // this.myBitmap.x = (this.canvasWidth - myImage.width) / 2;
      // this.myBitmap.y = (this.canvasHeight - myImage.height) / 2;
      myBitmap.x = this.nextX;
      this.nextX += myImage.width + this.margin;
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
