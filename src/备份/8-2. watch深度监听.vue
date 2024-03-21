<template>
    <div class="person">
       <h2>监视ref定义的对象类型数据</h2>
       <h2>姓名: {{ person.name }}</h2>
       <h2>名称: {{ person.age }}</h2>
       <button @click="changeName">修改名字</button>
       <button @click="changeAge">修改年龄</button>
       <button @click="changeAll">全改</button>
    </div>
</template>

<script setup lang="ts" name="Person">
    import { ref, watch } from 'vue';

    const person = ref({
        name: '麻将',
        age: 3
    });

    function changeName() {
        person.value.name += '傻逼';
    }

    function changeAge() {
        person.value.age += 1;
    }

    function changeAll() {
        person.value = {
            name: '慢慢',
            age: 1.5
        }
    }

    /** 
     * 监视的是对象的地址值， 若想监视对象内部属性的变化，需要手动打开深度监视
     */
    watch(person, (newVal, oldVal) => {
        console.log(newVal, oldVal)
    }, {deep: true})

    
</script>

<style scoped>
    .person {
      background-color: skyblue;
      box-shadow: 0 0 10px;
      border-radius: 10px;
      padding: 20px;
    }
</style>
