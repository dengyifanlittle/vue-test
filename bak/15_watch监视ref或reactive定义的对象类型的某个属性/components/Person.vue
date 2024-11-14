<!-- ### * 情况四
监视`ref`或`reactive`定义的【对象类型】数据中的**某个属性**，注意点如下：

1. 若该属性值**不是**【对象类型】，需要写成函数形式。
2. 若该属性值是**依然**是【对象类型】，可直接编，也可写成函数，建议写成函数。

结论：监视的要是对象里的属性，那么最好写函数式，注意点：若是对象监视的是地址值，需要关注对象内部，需要手动开启深度监视。 -->

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

//    watch(()=>{return person.name},(newVal,oldVal)=>{
//     console.log("监视person的name变化", newVal, oldVal)
//    })

   watch(()=> person.name,(newVal,oldVal)=>{
    console.log("监视person的name变化", newVal, oldVal)
   })

// 监视，情况四：监视响应式对象中的某个属性，且该属性是基本类型的，要写成函数式
  /* watch(()=> person.name,(newValue,oldValue)=>{
    console.log('person.name变化了',newValue,oldValue)
  }) */

  // 监视，情况四：监视响应式对象中的某个属性，且该属性是对象类型的，可以直接写，也能写函数，更推荐写函数

   // 修改整体不行
//    watch(person.car,(newVal,oldVal)=>{
//     console.log("监视person的car变化:", newVal, oldVal)
//    })

   // 修改具体属性监视不到
    watch(() => person.car,(newVal,oldVal)=>{
        console.log("监视person的car变化:", newVal, oldVal)
    })

    // 加上deep，深度监听即可监视到具体属性和整个对象
   watch(() => person.car,(newVal,oldVal)=>{
    console.log("监视person的car变化:", newVal, oldVal)
   },{deep:true})

  
</script>

<style>
    
</style>