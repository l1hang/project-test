<template>
  <div id="app" ref="app">
    <timeFilp />
    <button @click="clickAll" v-if="!isAll">全屏</button>
    <!-- <CardHover /> -->
  </div>
</template>

<script>
import timeFilp from "./components/timeFilp.vue";
// import CardHover from "./components/CardHover.vue";
export default {
  components: {
    timeFilp,
    // CardHover,
  },
  name: "App",
  data() {
    return {
      isAll: false,
    };
  },
  methods: {
    clickAll() {
      let element = document.documentElement;
      if (element.requestFullscreen) {
        element.requestFullscreen();
      } else if (element.mozRequestFullScreen) {
        /* Firefox */
        element.mozRequestFullScreen();
      } else if (element.webkitRequestFullscreen) {
        /* Chrome, Safari and Opera */
        element.webkitRequestFullscreen();
      } else if (element.msRequestFullscreen) {
        /* IE/Edge */
        element.msRequestFullscreen();
      }
      this.isAll = true;
    },
    checkFullScreen() {
      this.isAll = document.fullscreenElement !== null;
    },
  },
  mounted() {
    document.addEventListener("fullscreenchange", this.checkFullScreen);
  },
  beforeDestroy() {
    document.removeEventListener("fullscreenchange", this.checkFullScreen);
  },
};
</script>

<style>
body {
  width: 100%;
  height: 100%;
  background: linear-gradient(
    to right,
    rgba(191, 91, 91, 0.3),
    rgba(130, 201, 130, 0.3),
    rgba(222, 196, 196, 0.3)
  );
}
#app {
  width: 1000px;
  height: 100%;
  margin: 300px auto;
  position: relative;
}
button {
  position: absolute;
  right: 0;
  top: 0;
  z-index: 999;
}
</style>
