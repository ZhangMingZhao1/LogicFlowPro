<template>
  <div id="app">
    <div id="container"></div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import LogicFlow from '@logicflow/core';
import { BpmnElement } from '@logicflow/extension';
import '@logicflow/core/dist/style/index.css';

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data() {
    return {
      myData: {
        // 节点
        nodes: [
          {
            id: 21,
            type: 'rect',
            x: 100,
            y: 200,
            text: {
              value: '矩形节点',
              x: 100,
              y: 200
            }
          },
          {
            id: 50,
            type: 'circle',
            x: 300,
            y: 400,
            text: {
              value: '圆形节点',
              x: 300,
              y: 400
            }
          }
        ],
        // 边
        edges: [
          {
            type: 'polyline',
            sourceNodeId: 50,
            targetNodeId: 21
          }
        ]
      }
    };
  },
  mounted(){
    this.$_init();
  },
  methods: {
    $_init() {
      // 渲染画布
      const lf = new LogicFlow({
        container: document.querySelector('#container'),
        stopScrollGraph: true,
        stopZoomGraph: true,
        width: 500,
        height: 500,
        grid: {
          type: 'dot',
          size: 20
        }
      });

      lf.render(this.myData);

      LogicFlow.use(BpmnElement);
    }
  },
 
};
</script>

<style>
/* #container {
  height: 100px;
  width: 100px;
} */
</style>
