<template>
  <div class="home">
    <canvas-content3 />
  </div>
</template>

<script>
// @ is an alias to /src
import CanvasContent from "@/components/CanvasContent.vue";
import CanvasContent2 from "@/components/CanvasContent2.vue";
import CanvasContent3 from "@/components/CanvasContent3.vue";

export default {
  name: "home",
  components: {
    CanvasContent,
    CanvasContent2,
    CanvasContent3
  }
};
</script>
