<template>
  <div class="choose_box">
    <span v-for="item in chooseArr" :class="item.id === current ? 'active' : ''" :key="item.id" @click="chooseBtn(item.id)">{{ item.label }}</span>
  </div>
  <!-- <component :is="currentComp"></component> -->
  <div class="comp_box">
    <demo1 v-if="current === 1" />
    <demo2 v-if="current === 2" />
  </div>
</template>

<script lang="ts" setup>
import { ref, computed } from 'vue'
import demo1 from './quickStart/demo1.vue'
import demo2 from './quickStart/demo2.vue'


const current = ref(2)
let compObj = ref({
    1: 'demo1'
})
const chooseArr = [
    {label: 'demo1', id: 1},
    {label: 'demo2', id: 2}
]

const chooseBtn = (data: number) => {
    current.value = data
}

</script>

<style lang="scss" scoped>
.choose_box {
    display: flex;
    justify-content: left;
    span {
        border: 1px solid #000;
        margin-left: 20px;
        cursor: pointer;
        &.active {
            background: pink;
        }
    }
}
.comp_box {
    margin-top: 30px;
}
</style>