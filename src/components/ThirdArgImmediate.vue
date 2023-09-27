<template>
    <h1>Third Arg</h1>
    <div>{{count}}</div>
    <button @click="count++">increase</button>
</template>
 
 
<script setup>
 
import { ref, reactive, computed ,watch } from 'vue'
 const count = ref(0)
// immediate
 watch(count,async (newValue,oldValue)=>{
    try{
        const res = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        const data = await res.json();
        console.log("title : ", data.title);
        console.log("count new  :",newValue,"old  Count : ",oldValue );
    }
    catch(error){
        console.log(error);
    }
 },{immediate:true})
</script>
 
<style scoped>
 
</style>