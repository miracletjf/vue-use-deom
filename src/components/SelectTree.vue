<template>
  <div class="tree-root">
    <div class="tree-head">
      <el-checkbox v-model="isAllChecked">{{treeData.name}}</el-checkbox>
    </div>
    <ul class="tree-list" v-if="treeData && treeData.child">
      <li v-for="(item, index) in treeData.child" :key="index">
        <select-tree :treeData="item"></select-tree>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  components: {
    SelectTree: () => import("./SelectTree.vue")
  },
  props: {
    treeData: [Object]
  },
  computed: {
    isAllChecked: {
      get() {
        let countObj = getNumOfTree(this.treeData);
        return countObj.sum === countObj.selectedCount;
      },
      set(val) {
        setLeafStatus(this.treeData, val);
      }
    }
  },
  data() {
    return {
      checked: true
    };
  },
  methods: {}
};
// 计算所有叶子节点个数
function getNumOfTree(data) {
  let res = {};
  res.sum = 0;
  res.selectedCount = 0;
  if (data.child && data.child.length) {
    data.child.reduce((acc, cur) => {
      let subRes = getNumOfTree(cur);
      acc.sum += subRes.sum;
      acc.selectedCount += subRes.selectedCount;
      return acc;
    }, res);
  } else {
    res.sum += 1;
    if (data.checked) res.selectedCount += 1;
  }
  return res;
}

// 设置所有叶子节点状态
function setLeafStatus(data, status) {
  if (data.child && data.child.length) {
    data.child.forEach(itemData => {
      setLeafStatus(itemData, status);
    });
  } else {
    data.checked = status;
  }
}
</script>
<style lang="scss">
.tree {
  &-root {
    text-align: left;
    line-height: 24px;
  }
  /* &-head {} */
  &-list {
    margin: 0;
    padding-left: 20px;
    list-style: none;
  }
}
</style>

