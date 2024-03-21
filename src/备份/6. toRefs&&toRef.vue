<template>
    <div class="person">
       <h2>姓名： {{person.name}}</h2>{{name}}
       <h2>年龄： {{person.age}}</h2>{{age}}
       <div @click="changeName">changeName</div>
       <div @click="changeAge">changeAge</div>
    </div>
</template>

<script setup lang="ts" name="Person">
    // toRefs和toRef相当于更改引用指针
    import {reactive, toRefs, toRef} from 'vue';
    let person = reactive({
        name: 'zhangsan',
        age: 18
    })

    let { name, age } = toRefs(person);

    let nl = toRef(person, 'age');

    function changeName() {
        // person.name += '~';
        name.value += '~';        
    }

    function changeAge() {
        // person.age += 1;
        age.value += 1;
        console.log(nl.value)
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
