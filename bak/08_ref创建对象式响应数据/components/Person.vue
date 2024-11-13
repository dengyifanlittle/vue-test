<template>
    <div class="person">
        <h2>一辆{{ car.name }}车，价值{{ car.price }}万</h2>
        <button @click="changePrice">修改价格</button>
        
    </div>
</template>

<script lang="ts" setup name="testName">
    import {ref} from 'vue'
    // ref可以定义基本数据、对象式响应数据
    // 只能定义:对象式响应数据reactive
    let car = ref({name:'玩具', price:10})
   
  

    // 方法
    function changePrice(){
        car.value.price += 1
        console.log(car)
    }
  
</script>

<style>
    .person {
        background-color:rgb(233, 233, 240);
    }
    button{
        margin: 0 10px;
    }
   
</style>