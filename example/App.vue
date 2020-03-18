<template>
  <div id="app">
    <el-button
      size="small"
      style="float:right;margin-top:6px;margin-right:6px;"
      @click="()=>{this.$refs['wfd'].graph.saveXML()}"
    >导出XML</el-button>
    <el-button
      size="small"
      style="float:right;margin-top:6px;margin-right:6px;"
      @click="()=>{this.modalVisible=true}"
    >查看流程图</el-button>
    <wfd-vue ref="wfd" :data="demoData" :height="600" :lang="lang" />
    <el-dialog title="查看流程图" :visible.sync="modalVisible" width="60%">
      <wfd-vue ref="wfd" :data="demoData" :height="300" isView />
    </el-dialog>
  </div>
</template>

<script>
import WfdVue from "../src/components/Wfd";
export default {
  name: "app",
  components: {
    WfdVue
  },
  data() {
    return {
      modalVisible: false,
      lang: "zh",
      demoData: {
        nodes: [
          { id: "startNode1", x: 400, y: 100, label: "", clazz: "start" },
          {
            id: "taskNode1",
            x: 300,
            y: 200,
            label: "task001.java",
            clazz: "javaTask"
          },
          {
            id: "taskNode2",
            x: 500,
            y: 200,
            label: "script001.sh",
            clazz: "scriptTask"
          },
          {
            id: "taskNode3",
            x: 400,
            y: 300,
            label: "compute001.spark",
            clazz: "mailTask"
          },
          { id: "endNode", x: 400, y: 400, label: "", clazz: "end" }
        ],
        edges: [
          {
            source: "startNode1",
            target: "taskNode1",
            sourceAnchor: 1,
            targetAnchor: 3,
            clazz: "flow"
          },
          {
            source: "startNode1",
            target: "taskNode2",
            sourceAnchor: 1,
            targetAnchor: 3,
            clazz: "flow"
          },
          {
            source: "taskNode1",
            target: "taskNode3",
            sourceAnchor: 2,
            targetAnchor: 2,
            clazz: "flow"
          },
          {
            source: "taskNode2",
            target: "taskNode3",
            sourceAnchor: 2,
            targetAnchor: 2,
            clazz: "flow"
          },
          {
            source: "taskNode3",
            target: "endNode",
            sourceAnchor: 1,
            targetAnchor: 1,
            clazz: "flow"
          }
        ]
      }
      // candidateUsers: [
      //   { id: "1", name: "Tom" },
      //   { id: "2", name: "Steven" },
      //   { id: "3", name: "Andy" }
      // ],
      // candidateGroups: [
      //   { id: "1", name: "Manager" },
      //   { id: "2", name: "Security" },
      //   { id: "3", name: "OA" }
      // ]
    };
  },
  mounted() {}
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
