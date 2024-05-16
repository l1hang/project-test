<template>
  <div id="app">
    <timeFilp />
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

    };
  },
  methods: {

  },
};
</script>

<style>
#app{
  width: 500px;
  height: 500px;
  margin: 0 auto;
}
</style>
