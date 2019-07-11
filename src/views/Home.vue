<template>
  <div class="home">
    <canvas-content />
    <canvas-content2 />
    <canvas-content3 />
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
