<template>
    <div class="person">
        <h2>当水温达到60， 或水位达到80时，给服务器发送请求</h2>
        <h2>当前水温{{ temp }}</h2>
        <h2>当前水位{{ height }}</h2>
        <button @click="changeSum">+温</button>
        <button @click="changeHeight">+水位</button>
    </div>
</template>

<script setup lang="ts" name="Person">
/** 
 * watchEffect: 立即运行一个函数， 同时响应式的追踪其依赖， 并在依赖更改时重新执行该函数。
 * 
 * watch watchEffect对比
 * 1. 都可以监听响应式数据的变化，不同的是监听数据变化的方式不同。
 * 2. watch需要明确指出监听的对象。
 * 3. watchEffect不需要明确指出监听的对象（函数中用到了哪些属性，就监听哪些属性）
 */
import { ref, watch, watchEffect } from "vue";

let temp = ref(10);
let height = ref(0);

// watch([temp, height], (newValue)=> {
//     console.log(newValue)
//     let [newTemp , newHeight] = newValue;
//     if (newTemp >= 60 || newHeight >= 80) console.log('执行sendRequest， 用不了this，😭')
    
// })

watchEffect(() => {
    if (temp.value >= 60 || height.value >= 80) console.log('执行sendRequest， 用不了this，😭')
})

function sendRequest() {

}
function changeSum() {
    temp.value += 10;
}

function changeHeight() {
    height.value += 10;
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
