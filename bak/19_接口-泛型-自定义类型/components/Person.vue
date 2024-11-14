<template>
    <div class="person">
        
    </div>
</template>


<script lang="ts" setup name="testName">
    
    import {type PersonInter,type Persons} from '@/types'

    // let person:PersonInter = {id:"1",name:"张三", age:18}
    
    // let personList:Array<PersonInter> = [
    //     {id:"1",name:"张三", age:18},
    //     {id:"2",name:"李四", age:19},
    //     {id:"3",name:"王五", age:20}
    // ]

    let personList:Persons = [
        {id:"1",name:"张三", age:18},
        {id:"2",name:"李四", age:19},
        {id:"3",name:"王五", age:20}
    ]


  
</script>

<style scoped>
    .person{
        background-color: aqua;
    }
</style>