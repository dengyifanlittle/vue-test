<template>
    <div class="person">
        <h1>情况一：监视ref定义的基本类型数据</h1>
        <h2>当前求和为:{{ sum }}</h2>
        <button @click="changeSum">点我sum+1</button>
        <hr>


    </div>
</template>

<script lang="ts" setup name="testName">
   import {ref, watch} from 'vue'

   let sum = ref(0)
   function changeSum(){
    sum.value += 1
   }
   // 监视
   const stopWatch = watch(sum,(newVal, oldVal)=>{
    console.log('sum变化了', newVal, oldVal)
    if(newVal >= 10){
        stopWatch()
    }
   })
   console.log(stopWatch)
  
</script>

<style>
    
</style>