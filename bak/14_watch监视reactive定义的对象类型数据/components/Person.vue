<!-- ### *  情况三
监视`reactive`定义的【对象类型】数据，且默认开启了深度监视。 -->
<template>
    <div class="person">
        <h1>情况三：监视reactive定义的对象型类型</h1>
        <h2>姓名:{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改人</button>
        <hr>
        <h1>测试数据:{{ obj.a.b.c }}</h1>
        <button @click="changeTest">点击修改测试数据</button>
    </div>
</template>

<script lang="ts" setup name="testName">
   import {reactive, watch} from 'vue'

   let person = reactive({name:'张三', age:18})

   let obj = reactive({
    a:{
        b:{
            c:666
        }
    }
   })
   function changeTest(){
    obj.a.b.c = 999
   }
   function changeName(){
    person.name += "~"
   }
   function changeAge(){
    person.age += 1
   }
   function changePerson(){
    Object.assign(person, {name:'李四', age:20})
   }
   // 监视，情况三：监视【reactive】定义的【对象类型】数据，且默认是开启深度监视的
   watch(person,(newPerson,oldPerson)=>{
    console.log("监视到person发生变化", newPerson, oldPerson)
   },{deep:true,immediate:true})
  
  watch(obj,(newVal, oldVal)=>{
    console.log("监视到测试数据发生变化：", newVal, oldVal)
  })
</script>

<style>
    
</style>