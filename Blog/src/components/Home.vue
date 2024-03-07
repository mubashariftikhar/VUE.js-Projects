<template>
    <h1>Email :{{email}}</h1>
    <h1>Old data :{{ getData().name }}</h1>
    <h1>Name :{{ getName() }}</h1>
</template>
<script>
export default {
    name:'Home-Page',
    data(){
        return{
            email:'mohid@gmail.com',
            mobile:'+923309196774',
        }
    },
    methods:{
        getName(){
           return"Mohid" 
        },
        getData(){
            return{
                name:'Khan',
                email:this.email,
            }
        }
    }
}
</script>
<style scoped>
h1{
    color: orange;
}
</style>