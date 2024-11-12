<template>
    <div class="person">
        <h1>姓名：{{ name }}</h1>
        <h2>年龄: {{ age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="showTel">查看联系方式</button>
        <hr>
        <h2>测试data:{{ testName }}</h2>
        <button @click="showTest">查看测试联系方式</button>
    </div>
</template>

<script>
    export default {
        name:'Person',
        data(){
            return{
                testName: 'test_name',
                testTel: '144454545'
            }
        },
        methods:{
            showTest(){
                alert(this.testTel)
            }
        },
        setup(){
            // 数据
            let name = 'tom' // 不是响应式
            let age = 18
            let tel = '1655468498'
            // 方法
            function changeName(){
                
                name = 'jack'
                console.log(name)
            }
            function changeAge(){
                age += 1
            }
            function showTel(){
                alert(tel)
            }
            // 交出数据
            return {name, age, tel, changeName, changeAge, showTel}
            // return ()=> 'test'
        }
    }
</script>

<style>
    .person {
        background-color:blue;
    }
    button{
        margin: 0 10px;
    }
</style>