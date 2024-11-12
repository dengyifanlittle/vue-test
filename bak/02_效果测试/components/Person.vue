<template>
    <div class="person">
        <h1>姓名：{{ name }}</h1>
        <h2>年龄: {{ age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="showTel">查看联系方式</button>
    </div>
</template>

<script>
    export default {
        name:'Person',
        data(){
            return{
                name:'tom',
                age: 18,
                tel: 115956564
            }
        },
        methods:{
            changeName(){
                this.name = 'jack'
            },
            changeAge(){
                this.age += 1
            },
            showTel(){
                alert(this.tel)
            }
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