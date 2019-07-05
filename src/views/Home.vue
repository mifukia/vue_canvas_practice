<template>
  <div class="home">
    <canvas-content />
  </div>
</template>

<script>
// @ is an alias to /src
import CanvasContent from "@/components/CanvasContent.vue";

export default {
  name: "home",
  components: {
    CanvasContent
  }
};
</script>
