<template>
    <div class="person">
        <h2>一辆{{ car.brand }}车, 价值{{ car.price }}</h2>
        <button @click.stop="changeCarPrice">修改价格</button>

        <ul>
            <li v-for="item in games" :key="item.id">{{ item.name }}</li>
        </ul>
        <button @click.stop="addGames">添加游戏</button>
    </div>
</template>
<!-- 
    reactive 响应式对象 （只能定义对象类型的响应式数据）
 -->
<script setup lang="ts" name="Person">
    import { reactive } from 'vue'; 
    // 数据
    let car = reactive({
        brand: '奔驰',
        price: 100
    })

    let games = reactive([
        { id: 1, name: 'CSGO' },
        { id: 2, name: 'CF' },
        { id: 3, name: 'PUBG' }
    ])

    function changeCarPrice() {
        car.price += 10;
    }

    function addGames() {
        games.push({
            id: new Date().getTime(),
            name: 'gamesName'
        })
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
