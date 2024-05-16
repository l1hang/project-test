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
#app{
  width: 1000px;
  height: 1000px;
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