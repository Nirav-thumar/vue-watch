<template>
<h1>Hospital charge : {{state.patient.bedCharge}}</h1>
 <button @click="state.patient.bedCharge  += 500">changeRoom</button>

</template>
 
 
<script setup>
 
import { ref, reactive, computed,watch } from 'vue'

// when using a getter source watching a reactive object ,it is require to manually enable deep mode
 const state = reactive({
    heartRate : 85,
    fear : 0,
    patient:{
        bedCharge : 500
    }
 })

// using getter need to manually on deep:true to track changes in raective object
// new value and old value are same
//  watch(()=>state,(newValue,oldValue)=>{
//     console.log("new value",newValue)
//     console.log("old value",oldValue)
//  },{deep:true})

// when directly watching a reactive object the watcher is automatically in deep mode
//old value and new value same
// watch(state,(newValue,oldValue)=>{
//     console.log("new value",newValue)
//     console.log("old value",oldValue)
//  })



</script>
 
<style scoped>
 
</style>