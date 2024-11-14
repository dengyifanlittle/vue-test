<template>
    <h2 a="1+1" :b="1+1" c="x" :d="x">测试</h2>
    <Person a="test" :list="personList"/>
</template>

<script lang="ts" setup name="App">
    import Person from './components/Person.vue'
    import { reactive } from 'vue';
    import { Persons } from './types';

    // let personList:Persons = reactive([
    //     {id:"1",name:"张三", age:18},
    //     {id:"2",name:"李四", age:19},
    //     {id:"3",name:"王五", age:20}
    // ])
    let x = 9

    let personList = reactive<Persons>([
        {id:"1",name:"张三", age:18},
        {id:"2",name:"李四", age:19},
        {id:"3",name:"王五", age:20, address:"中国"}
    ])
  
    // console.log(personList)
</script>

<style>
    .app {
        background-color: aquamarine;
    }
</style>