<!-- ### * 情况五
监视上述的多个数据 -->
<template>
    <div class="person">
       <h2>姓名：{{ person.name }}</h2>
       <h2>年龄:{{ person.age }}</h2>
       <h2>汽车:{{ person.car.c1 }}、{{ person.car.c2 }}</h2>
       <button  @click="changeName">修改名字</button>
       <button  @click="changeAge">修改年龄</button>
       <button  @click="changeFirst">修改第一台车</button>    
       <button  @click="changeSecond">修改第二台车</button>
       <button  @click="changeAll">修改整个车</button>
    </div>
</template>

<script lang="ts" setup name="testName">
   import {reactive, watch} from 'vue'

   let person = reactive({
    name:"张三",
    age:18,
    car:{
        c1:"01",
        c2:"02"
    }
   })

   function changeName(){
    person.name += "~"

   }
   function changeAge(){
    person.age += 1
   }
   function changeFirst(){
    person.car.c1 = "01改"
   }
   function changeSecond(){
    person.car.c2 = "02改"
    }
   function changeAll(){
    person.car = {c1:"01all",c2:"02all"}
    // Object.assign(person.car, {c1:"01all",c2:"02all"})
   }

   watch([()=>person.name,()=>person.car.c1],(newVal,oldVal)=>{
    console.log("监视到发生变化：", newVal, oldVal)
   })

  
</script>

<style>
    
</style>