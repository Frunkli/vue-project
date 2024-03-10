<template>
    <div class="person">
      <div>姓名： {{ name }}</div>
      <div>年龄：{{ age }}</div>
      <button @click.stop="showTel">查看联系方式</button>
      <button @click.stop="changeName">更改姓名</button>
      <div v-if="isShowTel">电话：{{ tel }}</div>
    </div>
  </template>
  
  <script setup lang="ts" name="otherPerson">
  let name: string = "frunkli";
  let age: number = 25;
  let tel: string = "123142";
  let isShowTel: boolean = false;
  
  function showTel(): void {
    isShowTel = !isShowTel;
  }
  function changeName(): void {
    name = "慢慢";
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
  