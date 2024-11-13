<template>
    <div class="person">
        <!-- 姓：<input type="text" v-bind:value="32"> <br>
        名: <input type="text" :value="2"> <br> -->
        姓：<input type="text" v-model="firstName"> <br>
        名: <input type="text" v-model="lastName"> <br>
        <button @click="changeFullName">修改全名为李四</button><br>
        全名: <span>{{ fullName }}</span><br>
        全名: <span>{{ fullName }}</span><br>
        全名: <span>{{ fullName }}</span><br>
        全名: <span>{{ fullName2() }}</span><br>
        全名: <span>{{ fullName2() }}</span><br>
        全名: <span>{{ fullName2() }}</span><br>
    </div>
</template>

<script lang="ts" setup name="testName">
   import {ref, computed} from 'vue'

   let firstName = ref('张')
   let lastName = ref('三')

   function fullName2(){
    console.log(1)
    return firstName.value + lastName.value
   }
   // computed定义的属性是一个计算属性，且是只读的
//    let fullName = computed(() => {
//     console.log(2)
//     return firstName.value + lastName.value
//    })

   // 需要可读可写需要如下写法，需要设置get、set方法
   let fullName = computed({
    get(){
        return firstName.value + lastName.value
    },
    set(val){
        const [str1, str2] = val.split('-')
        firstName.value = str1
        lastName.value = str2
    }
   })

   function changeFullName(){
        fullName.value = "李-四"
   }
</script>

<style>
    
</style>