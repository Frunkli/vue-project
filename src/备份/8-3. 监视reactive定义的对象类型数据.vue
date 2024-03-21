<template>
    <div class="person">
       <h2>监视reactive定义的对象类型数据</h2>
       <h2>姓名: {{ person.name }}</h2>
       <h2>名称: {{ person.age }}</h2>
       <button @click="changeName">修改名字</button>
       <button @click="changeAge">修改年龄</button>
       <button @click="changeAll">全改</button>
    </div>
</template>

<script setup lang="ts" name="Person">
    import { reactive, watch } from 'vue';

    const person = reactive({
        name: '麻将',
        age: 3
    });

    function changeName() {
        person.name += '傻逼';
    }

    function changeAge() {
        person.age += 1;
    }

    function changeAll() {
        // reactive不能这么修改
        // person = {
        //     name: '慢慢',
        //     age: 1.5
        // }
        Object.assign(person, {name: '慢慢', age: 1.5})
    }

    /** 
     * 监视reactive定义的对象类型 是默认开启深度监视的
     * 隐式创建了深层监听
     */
    watch(person, (newVal, oldVal) => {
        console.log(newVal, oldVal)
    })

    
</script>

<style scoped>
    .person {
      background-color: skyblue;
      box-shadow: 0 0 10px;
      border-radius: 10px;
      padding: 20px;
    }
</style>
