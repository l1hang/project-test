<template>
<div id="g-container" @mousemove="handleMouseMove" @mouseout="handleMouseOut" :style="containerStyle">
    <div id="g-filter"></div>
    <div id="g-img" ref="img"></div>
</div>
</template>

<script>
export default {
  data() {
    return {
      containerStyle: {}
    }
  },
  methods: {
    handleMouseMove(event) {
      this.$refs.img.style.visibility = 'visible';

      const target = event.target;
      const rect = target.getBoundingClientRect();

      var offsetX = event.clientX - rect.left;
      var offsetY = event.clientY - rect.top;

      var percentX = (Math.min(Math.max(offsetX / rect.width, 0), 1) * 100).toFixed(2);
      var percentY = (Math.min(Math.max(offsetY / rect.height, 0), 1) * 100).toFixed(2);

      console.log('X: ' + percentX + '%');
      console.log('Y: ' + percentY + '%');

      this.containerStyle = {
        '--x': `${percentX}%`,
        '--y': `${percentY}%`
      };
    },
    handleMouseOut() {
      this.$refs.img.style.visibility = 'hidden';
    }
  }
}
</script>

<style scoped lang="less">
:root {
    --x: 0;
    --y: 0;
    // --pic: url("../assets/08-.jpg");
}
body {
    width: 100vw;
    height: 100vh;
    display: flex;
    cursor: pointer;
    background: #001;
}

#g-container {
    position: relative;
    margin: auto;
    width: 350px;
    height: 500px;
    border-radius: 30px;
    transition: all 0.1s;
    z-index: 3;

    &::after {
        content: "";
        position: absolute;
        inset: 50px;
        background: url("../assets/08-.jpg");
        background-size: cover;
        background-position: center;
        border-radius: 30px;
        z-index: 10;
    }
}

#g-filter {
    position: absolute;
    inset: 2px;
    border-radius: 30px;
    z-index: 5;
    overflow: hidden;
    
    &::before {
        content: "";
        position: absolute;
        inset: 0;
        background: url("../assets/08-.jpg");
        background-size: cover;
        filter: blur(20px);
    }
}

#g-img {
    position: absolute;
    // visibility: hidden;
    filter: brightness(1.5);
    inset: 0;
    z-index: 1;
    mask: radial-gradient(
        circle at var(--x) var(--y),
        #000,
        #000,
        transparent,
        transparent,
        transparent
    );

    &::before {
        content: "";
        position: absolute;
        inset: 2px;
        border-radius: 30px;
        background: conic-gradient(#03a9f4, #e91e63, #9c27b0, #ff5722, #03a9f4);
    }
    &::after {
        content: "";
        position: absolute;
        inset: 0;
        border-radius: 30px;
        background: conic-gradient(#03a9f4, #e91e63, #9c27b0, #ff5722, #03a9f4);
    }
}


</style>
