<template>
    <div class="app">
        <h1>test111</h1>
        <Person></Person>
    </div>
</template>

<script lang="ts">
    import Person from './components/Person.vue'
    export default {
        name:'App', //组件名
        components:{Person} // 注册组件
    }
</script>

<style>
    .app {
        background-color: aquamarine;
    }
</style>