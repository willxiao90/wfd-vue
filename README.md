## Workflow Designer for Vue

[![NPM Version](http://img.shields.io/npm/v/wfd-vue.svg?style=flat)](https://www.npmjs.org/package/wfd-vue)
[![NPM Downloads](https://img.shields.io/npm/dm/wfd-vue.svg?style=flat)](https://www.npmjs.org/package/wfd-vue)
![](https://img.shields.io/badge/license-MIT-000000.svg)

![image](https://github.com/willxiao90/wfd-vue/raw/master/example/snapshots/2.png)

## Online Demo
https://guozhaolong.github.io/wfd-vue/

## Usage
```
<template>
  <div id="app">
    <wfd-vue ref="wfd" :data="demoData" :height="600" :jobs="jobList" :lang="lang" />
  </div>
</template>

<script>
import WfdVue from 'wfd-vue'
export default {
  name: 'app',
  components:{
    WfdVue
  },
  data () {
    return {
      lang: "zh",
       demoData: {
          "nodes": [
              {
                  "id": "555", 
                  "label": "testJava2", 
                  "jobId": "555", 
                  "clazz": "javaTask", 
                  "x": 191.5, 
                  "y": 181
              }, 
              {
                  "id": "dd7c15bd-b498-4068-8c7c-d5a2b8df24c6", 
                  "label": "testjava", 
                  "jobId": "dd7c15bd-b498-4068-8c7c-d5a2b8df24c6", 
                  "clazz": "javaTask", 
                  "x": 456.5, 
                  "y": 181
              }, 
              {
                  "id": "begin", 
                  "label": null, 
                  "jobId": "begin", 
                  "clazz": "start", 
                  "x": 330.5, 
                  "y": 75
              }, 
              {
                  "id": "end", 
                  "label": null, 
                  "jobId": "end", 
                  "clazz": "end", 
                  "x": 322.5, 
                  "y": 313
              }
          ], 
          "edges": [
              {
                  "source": "begin", 
                  "target": "555", 
                  "clazz": "flow"
              }, 
              {
                  "source": "begin", 
                  "target": "dd7c15bd-b498-4068-8c7c-d5a2b8df24c6", 
                  "clazz": "flow"
              }, 
              {
                  "source": "dd7c15bd-b498-4068-8c7c-d5a2b8df24c6", 
                  "target": "end", 
                  "clazz": "flow"
              }, 
              {
                  "source": "555", 
                  "target": "end", 
                  "clazz": "flow"
              }
          ]
      },
      jobList: [
          {
              "id": "acca803a-63ff-499e-a11e-a5240ccf1b7e", 
              "name": "test003", 
              "type": "java"
          }, 
          {
              "id": "555", 
              "name": "testJava2", 
              "type": "java"
          }, 
          {
              "id": "22a9d4cc-3f38-4f61-b006-529eb529f1d9", 
              "name": "test_hdfs", 
              "type": "spark"
          }, 
          {
              "id": "dd7c15bd-b498-4068-8c7c-d5a2b8df24c6", 
              "name": "testjava", 
              "type": "java"
          }
      ],
    }
  }
}
</script>
```

## API
###### 属性
* data: 初始化数据
* height: 画布高度
* mode: view为只读，edit为可编辑
* lang: zh为中文，en为英文
* isView: 是否为预览模式（隐藏工具栏和属性栏）
* jobs: 选择任务时对应的数据，数组内对象以id为键，name为值，type为类型

###### 方法
* save(): 调用this.$refs['wfd'].graph.save()生成json
* saveXML(): 调用this.$refs['wfd'].graph.saveXML(createFile)生成Flowable XML，createFile参数是否同时生成xml文件，默认为true


### Run Example
```
npm run serve
```
