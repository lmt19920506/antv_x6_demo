<template>
    <!-- 第一步：创建容器 -->
    <div id="container">

    </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';
import { Graph } from '@antv/x6';

// 2. 准备数据
const data = {
    // 2.1 定义节点数据
    nodes: [
        {
            id: 'node1', // 节点的唯一标识
            x: 0,
            y: 0,
            width: 80,
            height: 40,
            label: 'hello'
        },
        {
            id: 'node2', // 节点的唯一标识
            x: 160,
            y: 180,
            width: 80,
            height: 40,
            label: 'world'
        }
    ],
    // 定义边的数据
    edges: [
        {
            source: 'node1',
            target: 'node2'
        }
    ]
}
export default defineComponent({
    setup() {
        let graph = {}
        // 第三步进行画布的渲染
        onMounted(() => {
            graph = new Graph({
                container: document.getElementById('container') as HTMLElement,
                width: 2000,
                height: 600,
                grid: true
            });
            (graph as Graph).fromJSON(data)
        })
    }
}) 
</script>

<style></style>