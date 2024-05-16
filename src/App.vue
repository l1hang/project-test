<template>
  <div id="app" ref="app">
    <timeFilp />
    <button @click="clickAll" v-if="!isAll">全屏</button>
  </div>
</template>

<script>
import timeFilp from "./components/timeFilp.vue";
export default {
  components: {
    timeFilp,
  },
  name: "App",
  data() {
    return {
      isAll: false,
    };
  },
  methods: {
    clickAll(){
      let element = document.documentElement;
      if (element.requestFullscreen) {
        element.requestFullscreen();
      } else if (element.mozRequestFullScreen) { /* Firefox */
        element.mozRequestFullScreen();
      } else if (element.webkitRequestFullscreen) { /* Chrome, Safari and Opera */
        element.webkitRequestFullscreen();
      } else if (element.msRequestFullscreen) { /* IE/Edge */
        element.msRequestFullscreen();
      }
      this.isAll = true;
    },
    checkFullScreen(){
      this.isAll = document.fullscreenElement !== null;
    }
  },
  mounted() {
    document.addEventListener('fullscreenchange', this.checkFullScreen);
  },
  beforeDestroy() {
    document.removeEventListener('fullscreenchange', this.checkFullScreen);
  }
};
</script>

<style>
body {
  width: 100%;
  height: 100%;
  background: linear-gradient(to right, rgba(244, 103, 103, 0.3), rgba(108, 241, 108, 0.3), rgba(124, 124, 236, 0.3));
}
#app{
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