<template>
  <div class="home">
    <canvas-content2 />
  </div>
</template>

<script>
// @ is an alias to /src
import CanvasContent from "@/components/CanvasContent.vue";
import CanvasContent2 from "@/components/CanvasContent2.vue";

export default {
  name: "home",
  components: {
    CanvasContent,
    CanvasContent2,  
  }
};
</script>
