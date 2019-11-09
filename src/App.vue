<template>
  <div id="app">
    <h2 :style="{textAlign: 'left'}">多级菜单树 DEMO</h2>
    <select-tree :tree-data="treeData"></select-tree>
  </div>
</template>

<script>
import SelectTree from "./components/SelectTree";

export default {
  name: "App",
  components: {
    SelectTree
  },
  data() {
    return {
      treeData: {
        name: "root",
        child: [
          {
            name: "node-1",
            child: [
              {
                name: "node-1-1",
                child: [
                  {
                    name: "node-1-1-1",
                    child: [
                      {
                        name: "node-1-1-1-1",
                        checked: false
                      },
                      {
                        name: "node-1-1-1-2",
                        checked: false
                      }
                    ]
                  },
                  {
                    name: "node-1-1-2",
                    child: [
                      {
                        name: "node-1-1-2-1",
                        checked: false
                      },
                      {
                        name: "node-1-1-2-2",
                        checked: false
                      }
                    ]
                  }
                ]
              },
              {
                name: "node-1-2",
                child: [
                  {
                    name: "node-1-2-1",
                    checked: false
                  },
                  {
                    name: "node-1-2-2",
                    checked: false
                  }
                ]
              }
            ]
          },
          {
            name: "node-2",
            child: [
              {
                name: "node-2-1",
                child: [
                  {
                    name: "node-2-1-1",
                    checked: false
                  },
                  {
                    name: "node-2-1-2",
                    checked: false
                  }
                ]
              },
              {
                name: "node-2-2",
                child: [
                  {
                    name: "node-2-2-1",
                    checked: false
                  },
                  {
                    name: "node-2-2-2",
                    checked: false
                  }
                ]
              }
            ]
          },
          {
            name: "node-3",
            child: [
              {
                name: "node-3-1",
                checked: false
              },
              {
                name: "node-3-2",
                checked: false
              }
            ]
          },
          {
            name: "node-4",
            child: [
              {
                name: "node-4-1",
                checked: false
              },
              {
                name: "node-4-2",
                checked: false
              }
            ]
          },
          {
            name: "node-5",
            checked: false
          },
          {
            name: "node-6",
            checked: false
          }
        ]
      }
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
