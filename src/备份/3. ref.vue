<template>
    <div class="person">
      <div>姓名： {{ name }}</div>
      <div>年龄：{{ age }}</div>
      <button @click.stop="showTel">查看联系方式</button>
      <button @click.stop="changeName">更改姓名</button>
      <div v-if="isShowTel">电话：{{ tel }}</div>
    </div>
  </template>
  
  <!-- 基本类型 -->
  <!-- 
      ref: 定义响应式变量
      返回一个RefImpl对象， 简称ref对象， ref对象的value属性是响应式的
      js中操作数据需要 xxx.value ，模板中不需要.value，直接使用即可
      对于let name = ref('章三')，name不是响应式的，name.value为响应式。
  -->
  
  <script setup lang="ts" name="otherPerson">
  import { ref } from "vue";
  
  let name = ref("frunkli");
  let age = ref(25);
  let tel: string = "123142";
  let isShowTel = ref(false);
  
  function showTel(): void {
    isShowTel.value = !isShowTel.value;
  }
  function changeName(): void {
    name.value = "慢慢";
    // 无法更新
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
  