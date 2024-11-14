<!-- 作用：用于注册模板引用。

> * 用在普通`DOM`标签上，获取的是`DOM`节点。
>
> * 用在组件标签上，获取的是组件实例对象。 -->

<template>
    <div class="person">
        <h1>中国</h1>
        <h2 ref="title2">北京</h2>
        <h3>中关村</h3>

        <button @click="showH2">点我输出h2元素</button>
    </div>
</template>
<!-- 子组件Person.vue中要使用defineExpose暴露内容 -->
<script lang="ts" setup name="testName">
    import {ref, defineExpose} from 'vue'

    //  创建一个title2,用于存储ref标记的内容
    let title2 = ref()
    let a = ref(0)
    let b = ref(1)
    let c = ref(2)
    function showH2(){
        console.log(title2.value)
    }
   
    // 使用defineExpose将组件中的数据交给外部
    defineExpose({a,b})
  
</script>

<style scoped>
    .person{
        background-color: aqua;
    }
</style>