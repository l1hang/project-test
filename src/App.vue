<template>
  <div id="app">
    <h1>测试下拉树状组件</h1>
    <Button>Default</Button>
    <Button type="primary">Primary</Button>
    <base-select-tree  />
  </div>
</template>

<script>
import baseSelectTree from "./components/base-select-tree.vue";
export default {
  components: {
    baseSelectTree,
  },
  name: "App",
  data() {
    return {

    };
  },
  methods: {
    clickChange(val) {
      console.log(val);
    },
    //点击执行科室树节点
    clickNodeChange(data) {
      this.typeCodeList.push({
        value: data[0].value,
        label: data[0].title,
      });
      this.formData.deptID.push(data[0].value);
    },
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
