<template>
  <span style="word-break: break-all; position: relative; width: 100%">
    <template v-if="readonly">
      {{ selectedName ? selectedName : emptyText }}
    </template>
    <Select
      :transfer="transfer"
      :value="selectedVal"
      v-bind="$attrs"
      v-on="$listeners"
      :multiple="multiple"
      :disabled="disabled"
      :placeholder="disabled ? '' : placeholder"
      :label-in-value="labelInValue"
      :clearable="clearable"
      @on-change="clickChange"
    >
      <Option
        v-for="item in typeCodeList"
        hidden
        :value="item.value"
        :key="item.value"
        >{{ item.label }}</Option
      >
      <Tree :data="deptList" @on-select-change="clickNodeChange"></Tree>
    </Select>
  </span>
</template>

<script>
export default {
  name: "BaseSelectTree",
  props: {
    // 是否只读
    readonly: {
      type: Boolean,
      default: false,
    },
    // 空值时显示的内容
    emptyText: {
      type: String,
      default: "暂无数据",
    },
    //是否将弹层放置于 body 内
    transfer: {
      type: Boolean,
      default: false,
    },
    //是否多选
    multiple: {
      type: Boolean,
      default: false,
    },
    //是否禁用
    disabled: {
      type: Boolean,
      default: false,
    },
    //下拉框默认文字
    placeholder: {
      type: String,
      default: "请选择",
    },
    // 在返回选项时，是否将 label 和 value 一并返回，默认只返回 value
    labelInValue: {
      type: Boolean,
      default: false,
    },
    // 是否可删除
    clearable: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      selectedVal: null, //选中的值
      formData: {
        deptID: [],
      },
      deptList: [
        {
          title: "测试一",
          children: [
            {
              title: "测试一-1",
              children: [
                {
                  title: "测试一-1-1",
                },
                {
                  title: "测试一-1-2",
                },
              ],
            },
            {
              title: "测试一-2",
              children: [
                {
                  title: "测试一-2-1",
                },
                {
                  title: "测试一-2-2",
                },
              ],
            },
          ],
        },
      ],
    };
  },
  computed: {},
  methods: {
    clickChange(val) {
      console.log(val);
    },
    clickNodeChange(val) {
      console.log(val);
    },
  },
};
</script>

<style scoped lang="less"></style>
