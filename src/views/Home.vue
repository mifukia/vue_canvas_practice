<template>
  <div class="home">
    <h1>キャンバス（create.js）で色々やってみる</h1>
    <h2>素のjavascriptで描いた星型のシェイプ</h2>
    <canvas-content />
    <h2>create.jsで描いた星型のシェイプに動きを加えてみる</h2>
    <canvas-content2 />
    <h2>create.jsでbitmap画像を表示させてみる</h2>
    <canvas-content3 />
    <h2>create.jsでシェイプの追加と、ドラッグアンドドロップで動かせるようにしてみる</h2>
    <canvas-content4 />
  </div>
</template>

<script>
// @ is an alias to /src
import CanvasContent from "@/components/CanvasContent.vue";
import CanvasContent2 from "@/components/CanvasContent2.vue";
import CanvasContent3 from "@/components/CanvasContent3.vue";
import CanvasContent4 from "@/components/CanvasContent4.vue";

export default {
  name: "home",
  components: {
    CanvasContent,
    CanvasContent2,
    CanvasContent3,
    CanvasContent4
  }
};
</script>
<style scoped lang="scss">
h1 {
  padding: 100px 0;
}
</style>
