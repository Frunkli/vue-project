<template>
    <div class="person">
        <div>姓名： {{ name }}</div>
        <div>年龄：{{ age }}</div>
        <button @click.stop="showTel">查看联系方式</button>
        <button @click.stop="changeName">更改姓名</button>
        <div v-if="isShowTel">电话：{{ tel }}</div>
    </div>
</template>

<script lang="ts">
    // private const name = 'frunkli';
    export default {
        name: 'Person',
        // setup的this是undefined，vue3中已经弱化this了
        // 数据原来是写在data里面， 此时的name、age、tel、isShowTel都不是响应式数据
        setup() {
            // 数据
            let name = 'frunkli'; // 非响应式
            let age = 25;
            let tel = '123142';
            let isShowTel = false;

            // 方法
            function showTel() {
                // 非响应式，页面无变化
                isShowTel = !isShowTel
            } 
            function changeName() {
                // 非响应式，页面无变化
                name = '慢慢'
            }
            return {
                name,
                age,
                tel,
                isShowTel,
                showTel,
                changeName
            }

            // setup的返回值也可以是一个渲染函数
            // return () => '哈哈'
        }
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