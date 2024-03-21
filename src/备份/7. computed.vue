<template>
    <div class="person">
        <div>姓： <input type="text" v-model="nameObj.firstName"></div>
        <div>名： <input type="text" v-model="nameObj.lastName"></div>
       <h2>姓名： {{ fullName }}</h2>
       <h2>年龄： {{}}</h2>
       <button @click="clearInfo">清除</button>
       <button @click="changeFullName">更改computed的值</button>
       <!-- <div @click="changeName">changeName</div> -->
       <!-- <div @click="changeAge">changeAge</div> -->
    </div>
</template>

<script setup lang="ts" name="Person">
    // 计算属性是有缓存的（脏值查询）， 方法是没有缓存的
    import {computed, ref} from 'vue';
    interface fullNameInter {
        firstName: string,
        lastName: string
    }
    const nameObj = ref<fullNameInter>({
        firstName: '',
        lastName: ''
    })

    // 这么定义的计算属性是只读的， 不可修改
    // const fullName = computed(() => {
    //     return nameObj.value.firstName + nameObj.value.lastName
    // })

    // 可读可写(业务不需要)
    const fullName = computed({
        get() {
            return nameObj.value.firstName + '-' + nameObj.value.lastName
        },

        set(v) {
            const [str1, str2] = v.split('-');
            nameObj.value.firstName = str1;
            nameObj.value.lastName = str2;
        }
        
    })

    function clearInfo(): void {
        nameObj.value.firstName = ''
        nameObj.value.lastName = ''
    }

    function changeFullName(): void {
        fullName.value = '慢-慢'
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
