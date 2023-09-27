<template>
 <div v-if="heartRate > 0">Heart Rate : {{heartRate}}</div>
<div v-else>sorry you are to late</div>
<button @click="heartRate += 5">increase</button>
<button @click="heartRate -= 5">decrease</button>

<button @click="changeUrl">change URL</button>
<br>
<button @click="stopWatch">stopWatch</button>
</template>
 
 
<script setup>
 
import { ref, reactive, computed ,watchEffect,onBeforeUpdate,onUpdated } from 'vue'


 const heartRate = ref(85);
 let url = ref("https://jsonplaceholder.typicode.com/posts/1")

// simple watchEffect
//  watchEffect(()=>{
//     console.log('count : ',heartRate.value)
//     })

// with flush:post 
//  watchEffect(()=>{
//     console.log('count : ',heartRate.value)

//  },{flush:'post'})

function changeUrl(){
    // let urlLenght = url.value.split('/').length
    // let lastValue = url.value.split('/')[urlLenght-1]
    // console.log(lastValue);
    url.value = "https://jsonplaceholder.typicode.com/posts/2"
}
 onBeforeUpdate(()=>{
    console.log("onBefore update call")
})
onUpdated(()=>{
    console.log("onUpdated call")
})

// watchEffect(async ()=>{
//     try{
//         const res = await fetch(url.value);
//         const data = await res.json();
//         console.log("title : ", data.title);
//     }
//     catch(error){
//         console.log(error);
//     }
//  })


// unWatch
const unWatch = watchEffect(async ()=>{
    try{
        const res = await fetch(url.value);
        const data = await res.json();
        console.log("title : ", data.title);
    }
    catch(error){
        console.log(error);
    }
 })

function stopWatch(){
    unWatch();
}




    
</script>
 
<style scoped>
 
</style>