<template>
  <div class="find-you">
    <div class="scale-box">
      <div class="image">
        <img src="../assets/person.png" alt="" />
        <div class="circle circle1"></div>
        <div class="circle circle2"></div>
        <div class="circle circle3"></div>
        <div class="circle circle4"></div>
      </div>
      <div class="name">And1zzz</div>
      <div class="find">正在找你</div>
      <div class="true">✅</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FindYou",
  components: {},
  data() {
    return {};
  },
  created() {},
  mounted() {},
  methods: {},
};
</script>

<style lang="less" scoped>
.find-you {
  width: 180px;
  height: 225px;
  background-color: rgba(255, 255, 255, 0.8);
  margin: 0 auto;
  border-radius: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  .scale-box {
    width: 80px;
    height: 120px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    animation: scaleAnimation 20s infinite;
    .image {
      width: 50px;
      height: 50px;
      position: relative;
      img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
      }
      .circle {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 100%;
        height: 100%;
        border-radius: 50%;
        transform: translate(-50%, -50%);
        border: 1px solid rgba(106, 105, 105, 0.2);
        animation: pulse 2s infinite;
      }
      .circle1 {
        animation-delay: 0s;
      }
      .circle2 {
        width: 120%;
        height: 120%;
        animation-delay: 0.5s;
      }
      .circle3 {
        width: 140%;
        height: 140%;
        animation-delay: 1s;
      }
      .circle4 {
        width: 160%;
        height: 160%;
        animation-delay: 1.5s;
      }
    }
    .name {
      font-size: 12px;
      color: #7c7c7c;
    }
    .find {
      font-size: 16px;
      color: #000000;
    }
    .true {
      font-size: 18px;
    }
  }
}
@keyframes scaleAnimation {
  0% {
    transform: scale(1);
  }
  49.9% {
    transform: scale(3);
  }
  50% {
    transform: scale(1);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes pulse {
  0% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 1;
  }
  50% {
    transform: translate(-50%, -50%) scale(1.5);
    opacity: 0;
  }
  100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 1;
  }
}
</style>