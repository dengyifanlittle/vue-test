<!-- ### * 情况二
监视`ref`定义的【对象类型】数据：直接写数据名，监视的是对象的【地址值】，若想监视对象内部的数据，要手动开启深度监视。

> 注意：
>
> * 若修改的是`ref`定义的对象中的属性，`newValue` 和 `oldValue` 都是新值，因为它们是同一个对象。
>
> * 若修改整个`ref`定义的对象，`newValue` 是新值， `oldValue` 是旧值，因为不是同一个对象了。 -->

<template>
    <div class="person">
        <h1>情况二：监视ref定义的对象型类型</h1>
        <h2>姓名:{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改人</button>
    </div>
</template>

<script lang="ts" setup name="testName">
   import {ref, watch} from 'vue'

   let person = ref({name:'张三', age:18})

   function changeName(){
    person.value.name += "~"
   }
   function changeAge(){
    person.value.age += 1
   }
   function changePerson(){
    person.value = {name:'李四', age:20}
   }
    /* 
    监视，情况二：监视【ref】定义的【对象类型】数据，监视的是对象的地址值，若想监视对象内部属性的变化，需要手动开启深度监视
    watch的第一个参数是：被监视的数据
    watch的第二个参数是：监视的回调
    watch的第三个参数是：配置对象（deep、immediate等等.....） 
  */
   watch(person,(newPerson,oldPerson)=>{
    console.log("监视到person发生变化", newPerson, oldPerson)
   },{deep:true,immediate:true})
  
</script>

<style>
    
</style>