<template>
    <div class="person">
        <h2>一辆{{ car.name }}车，价值{{ car.price }}万</h2>
        <button @click="changePrice">修改价格</button>
        <br>
        <h2>列表</h2>
        <ul>
            <li v-for="item in games" :key="item.id">{{ item.name }}</li>
        </ul>
        <button @click="changeGName">修改列表名字</button>
        <hr>
        <h2>测试{{ obj.a.b.c }}</h2>
        <button @click="changeObj">修改深层次</button>
    </div>
</template>

<script lang="ts" setup name="testName">
    import {reactive} from 'vue'
    // 对象式响应数据reactive
    let car = reactive({name:'玩具', price:10})
    let games = reactive([
        {id:1, name:'01'},
        {id:2, name:'02'}
    ])
    let obj = reactive(
        {a:{
            b:{
                c:666
            }
        }}
    )

    // 方法
    function changePrice(){
        car.price += 1
        console.log(car)
    }
    function changeGName(){
        games[0].name = '01改'
    }
    function changeObj(){
        obj.a.b.c = 999
    }
</script>

<style>
    .person {
        background-color:rgb(233, 233, 240);
    }
    button{
        margin: 0 10px;
    }
    li{
        color: #c02020;
    }
</style>