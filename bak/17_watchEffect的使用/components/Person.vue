<!-- ## 3.10. 【watchEffect】

* 官网：立即运行一个函数，同时响应式地追踪其依赖，并在依赖更改时重新执行该函数。

* `watch`对比`watchEffect`

  > 1. 都能监听响应式数据的变化，不同的是监听数据变化的方式不同
  >
  > 2. `watch`：要明确指出监视的数据
  >
  > 3. `watchEffect`：不用明确指出监视的数据（函数中用到哪些属性，那就监视哪些属性）。 -->

<template>
    <div class="person">
        <h2>需求：当水温达到60度，或水位达到80cm，给服务器发请求</h2>
       <h2>当前水温{{ temp }}</h2>
       <h2>当前水位{{ height }}</h2>
       <button @click="changeTemp">水温+10</button>
       <button @click="changeHeight">水位+10</button>
    </div>
</template>

<script lang="ts" setup name="testName">
    import {ref, watch, watchEffect} from 'vue'

    let temp = ref(10)
    let height = ref(0)
    function changeTemp(){
        temp.value += 10
    }
    function changeHeight(){
        height.value += 10
    }

    // 用watch实现，需要明确的指出要监视：temp、height
    // watch([temp, height],(newVal,oldVal)=>{
    //     let [newTemp,newHeight] = newVal
    //     if(newTemp >= 60 || newHeight >= 80){
    //         console.log("达到要求，给服务器发送消息",newVal, oldVal)
    //     }
    // })
    // watch([()=>temp.value,()=> height.value],(newVal,oldVal)=>{
    //     if(temp.value >= 60 || height.value >= 80){
    //         console.log("达到要求，给服务器发送消息",newVal, oldVal)
    //     }
    // })
    // 用watchEffect实现，不用
    watchEffect(()=>{
        if(temp.value >= 60 || height.value >= 80){
            console.log("达到要求，给服务器发送消息",temp.value, height.value)
        }
        
    })
  
</script>

<style>
    
</style>