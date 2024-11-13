<template>
    <div class="person">
        <h2>姓名:{{ name }}</h2>
        <h2>年龄:{{ age }}, {{ nl }}</h2>
        <button @click="changeName">修改姓名</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改人</button>
    </div>
</template>

<script lang="ts" setup name="testName">
   import { reactive,toRefs,toRef } from 'vue';
   
   let person = reactive({
    name:'tom',
    age:18
   })

   let x = toRefs(person)
   console.log(x)
   // toRef是把reactive定义的对象中某一个值改成ref定义的值
   let nl = toRef(person, "age")
   console.log(nl.value)

   // toRefs就是把一个reactive定义的对象改成一个ref定义的对象
   let {name,age} = toRefs(person)

   function changeName(){
    name.value += '~'
    console.log(name.value, person.name)
   }
   function changeAge(){
    age.value += 1
   }
   function changePerson(){
    let p = {name:'near', age: 22}
    Object.assign(person, p)
   }
   
</script>

<style>
    
</style>