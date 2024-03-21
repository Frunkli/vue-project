<template>
    <div class="person">
       <h2>监视ref定义的基本类型数据</h2>
       <h2>当前求和为： {{ sum }}</h2>
       <button @click="changeSum">add 1</button>
    </div>
</template>

<script setup lang="ts" name="Person">
    import { ref, watch } from 'vue';

    const sum = ref(0);

    /** 
     * @method changeSum
     * @description 方法+1
     */
    function changeSum(): void {
        sum.value += 1;
    }

    /**
     * watch(value, callback)
     * @param {value} 监视数据 
     * @param {callback} 回调函数 内含参数newVal， oldVal
     */
    // watch(sum, (newVal, oldVal) => {
    //     console.log(newVal, oldVal, 'sum变化')
    // })

    const stopWatch = watch(sum, (newVal, oldVal) => {
        console.log('变化', newVal)
        if (newVal >= 5) {
            stopWatch();
        }
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
