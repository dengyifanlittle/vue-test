<!-- 
    若需要一个基本类型的响应数据，必需使用ref
    若需要一个响应对象，层级不深，ref、reactive均可
    若需要一个响应对象，层级较深，推荐使用reactive 
-->

<template>
    <div class="person">
        <h2>一辆{{ car.name }}车，价值{{ car.price }}万</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changePrice">修改价格</button>
        <button @click="changeCar">修改整个汽车</button>
        <br>
        <h2>当前sum:{{ sum }}</h2>
        <button @click="changeSum">点击进行sum</button>
        <hr>

        <h2>一个{{ game.name }}游戏，价值{{ game.price }}</h2>
        <button @click="changeGameName">修改名字</button>
        <button @click="changeGamePrice">修改价格</button>
        <button @click="changeGame">修改整个游戏</button>

    </div>
</template>

<script lang="ts" setup name="testName">
    import {ref} from 'vue'
    import {reactive} from 'vue'
    // ref可以定义基本数据、对象式响应数据
    // 只能定义:对象式响应数据reactive
    // ref要获取值需要value，reactive获取值无需value
    let car = reactive({name:'玩具1', price:10})

    let game = ref({name: '塞尔达' , price: 10})
    let sum = ref(0)
    // 方法
    function changeName(){
        car.name = '玩具2'
    }
    function changePrice(){
        car.price += 1
        console.log(car)
    }
    function changeCar(){
        // 直接修改对象，会导致对象变成非响应式对象
        // car = {name:'玩具3', price: 1}
        // 加reactive也不会是响应式对象
        // car = reactive({name:'玩具3', price: 1})
        // 如果要整个替换对象，需要使用Object.assign()
        let car1 = {name:'玩具3', price: 1}
        Object.assign(car, car1)
        console.log(car)
    }
    function changeGameName(){
        game.value.name = '马里奥'
    }
    function changeGamePrice(){
        game.value.price += 1
        console.log(car)
    }
    function changeGame(){
        // 对于ref是可以直接这样修改整个对象
        game.value = {name: '路易吉' , price: 5}
        console.log(game.value)
    }
    function changeSum(){
        sum.value += 1
        console.log(sum.value)
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