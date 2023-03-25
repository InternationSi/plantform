<!--
 * @Author: sfy
 * @Date: 2023-03-25 13:57:08
 * @LastEditors: sfy
 * @LastEditTime: 2023-03-25 14:48:11
 * @FilePath: /vue-naive-admin/src/views/demo/base/index.vue
 * @Description: update here
-->
<template>
  <div id="3d-graph"></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import ForceGraph3D from '@/components/3d-force-graph'

onMounted(() => {
  const N = 300
  const gData = {
    nodes: [...Array(N).keys()].map((i) => ({ id: i })),
    links: [...Array(N).keys()]
      .filter((id) => id)
      .map((id) => ({
        source: id,
        target: Math.round(Math.random() * (id - 1)),
      })),
  }

  console.log(gData, 'gDatagData')
  // const myGraph = new ThreeForceGraph().graphData(gData)
  // console.log(myGraph, 'myGraph')
  const Graph = ForceGraph3D()(document.getElementById('3d-graph')).graphData(gData)
})
</script>
