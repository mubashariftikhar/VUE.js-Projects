<template>
<h1>Home Component</h1>
<!--  CALL OF METHODS AND DATA  ----1-->
<!-- <h1>Email :{{email}}</h1>
    <h1>Old data :{{ getData().name }}</h1>
    <h1>Name :{{ getName() }}</h1> -->
<!-- EVENTS --2-->
<!-- <h1  v-on:mousemove="getConsole()">Home Component</h1>
    <button v-on:click="getData()"> Click me</button>
    <button v-on:dblclick="getData('Button Double Click')">Double Click</button>
    <h2>{{ count }}</h2> -->
<!-- TWO WAY BINDING ----3
<input type="text" v-model="count">
<h2>{{ count }}</h2> -->
</template>

<script>
export default {
    name: 'Home-Page',

    // TWO WAY BINDING  ---------3
    // data() {
    //     return {
    //         count :10
    //     }
    // }

    // EVENTS PRACTICE--2
    // data(){
    //     return{
    //         email:'mohid@gmail.com',
    //         mobile:'+923309196774',
    //     }
    // },
    // METHODS ---1
    // methods:{
    //     getName(){
    //        return"Mohid" 
    //     },
    //     getData(){
    //         return{
    //             name:'Khan',
    //             email:this.email,
    //         }
    //     }
    // }
}
</script>

<style scoped>
h1 {
    color: orange;
}
</style>
