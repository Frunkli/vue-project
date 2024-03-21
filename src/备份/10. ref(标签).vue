<template>
    <div class="person">
        <h1>China</h1>
        <h2 ref="title2">深圳</h2>
        <h3>tencent</h3>
        <button @click="showH2">输出h2元素</button>
    </div>
</template>

<script setup lang="ts" name="Person">
/** 
 * ref若写在组件上，父级调用ref查看子组件内的属性，
 * 需要在子组件内引入defineExpose，并把需要暴露的数据通过defineExpose传递出去
 * defineExpose({a, b, c})
 */
import {ref, defineExpose } from 'vue'

let title2 = ref()
function showH2() {
    console.log(title2.value)
}
</script>

<style scoped>
.person {
    background-color: skyblue;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
}
</style>
