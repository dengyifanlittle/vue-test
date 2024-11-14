<template>
    <div class="person">
        <h2 ref="title2">你好</h2>
    <button @click="showH2">点我输出h2</button>
   <Person ref="ren"></Person>
    </div>
   
</template>

<script lang="ts" setup name="App">
    import Person from './components/Person.vue'

    import {ref} from 'vue'

    let title2 = ref()
    let ren = ref()
    function showH2(){
        console.log(ren.value)
        // console.log(title2.value)
    }

    // export default {
    //     name:'App', //组件名
    //     components:{Person} // 注册组件
    // }
</script>

<style>
    .app {
        background-color: aquamarine;
    }
</style>