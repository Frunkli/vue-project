<template>
    <div class="person">
        <h2>姓名：{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}</h2>
        <h2>car：{{ person.car.c1 }} {{ person.car.c2 }}</h2>
        <button @click="changeName">修改姓名</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changeC1">修改car1</button>
        <button @click="changeC2">修改car2</button>
        <button @click="changeCar">修改整个车</button>
    </div>
</template>

<script setup lang="ts" name="Person">
import { reactive, watch } from "vue";

const person = reactive({
    name: "慢慢",
    age: 18,
    car: {
        c1: "benchi",
        c2: "baoma",
    },
});

// 监视响应式对象的某个属性， 且该属性为基本类型， 写成函数式
watch(() => person.name, (newVal, oldVal) => {
    console.log(newVal, oldVal);
});


// 此情况是监视对象的地址值
watch(() => person.car, (newVal, oldVal)=> {
    console.log(newVal, oldVal);
}, {deep: true})

// 情况五： 监视上述多个数据
watch([() => person.name, () => person.car.c1], (newVal, oldVal)=> {
    console.log(newVal, oldVal);
}, {deep: true})

function changeName() {
    person.name += "~";
}

function changeAge() {
    person.age += 1;
}

function changeC1() {
    person.car.c1 = "比亚迪";
}

function changeC2() {
    person.car.c2 = "吉利";
}

function changeCar() {
    person.car = {
        c1: "qq",
        c2: "微信",
    };
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
