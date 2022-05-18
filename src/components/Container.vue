<template>
  <div>
    <h1 @click="teste">clique aqui</h1>
    <div id="container">
      <VueDragResize
        ref="VueDragResize"
        :isActive="true"
        w="auto"
        h="auto"
        v-on:resizing="resize"
        v-on:dragging="resize"
        :parentLimitation="true"
        :y="rectTop"
        :x="rectLeft"
      >
        <h3>Hello World!</h3>
        <p>{{ top }} х {{ left }}</p>
        <!-- <p>{{ width }} х {{ height }}</p> -->
      </VueDragResize>
    </div>
  </div>
</template>

<script>
import VueDragResize from "vue-drag-resize";

export default {
  name: "vue-drag-resize",

  components: {
    VueDragResize,
  },

  data() {
    return {
      rectLeft: 200,
      rectTop: 350,
      width: 0,
      height: 0,
      top: 0,
      left: 0,
    };
  },

  methods: {
    teste() {
      this.rectLeft = 0;
      setTimeout(() => {
        this.rectTop = 0;
      });

      this.$forceUpdate();
    },
    resize(newRect) {
      this.width = newRect.width;
      this.height = newRect.height;
      this.top = newRect.top;
      this.left = newRect.left;
    },
  },
  mounted() {
    this.$nextTick(() => {
      this.top = 300;
      this.left = 200;
    });
  },
};
</script>

<style scoped>
#container {
  background: royalblue;
  width: 800px;
  height: 500px;
  position: relative;
}
</style>