<template>
    <div class="person">
        <!-- <h2>{{ a }}</h2> -->
        <h2>{{ list }}</h2>
        <ul>
            <li v-for="item in list" :key="item.id">
                {{ item.name }} -- {{ item.age }} -- {{ item.address }}
            </li>
        </ul>
    </div>
</template>


<script lang="ts" setup name="testName">
    import { defineProps,withDefaults } from 'vue'
    import { Persons } from '@/types';
    // 接收a
    // defineProps(['a'])

    // 接收a，同时将props保存起来
    // let x = defineProps(['a', 'list'])
    // console.log(x.a)
    // 接受list并限制类型
    // defineProps<{list:Persons}>()

    //接收list+限制类型+限制必要性+指定默认值
    // defineProps接<list:Persons>表示限制类型
    // list后面+?表示限制必要性
    // withDefaults指定默认值

    withDefaults(defineProps<{list?:Persons}>(),{
        // 需要函数式定义
        list:()=>[{id:"4",name:"赵六", age:21}]
    })
  
</script>

<style scoped>
    .person{
        background-color: aqua;
    }
</style>