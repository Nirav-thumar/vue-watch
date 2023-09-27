<template>
<div>{{state.heartRate}}</div>
<button @click="state.heartRate += 5">increase</button>
<button @click="state.heartRate -= 5">decrease</button>
</template>
 
 
<script setup>
 
import { ref, reactive, computed, watch  } from 'vue'
 
 const state= reactive({heartRate:85})

watch(()=>{ return {...state}},(newHeartRate,oldHeartRate)=>{
    console.log("newHeartRate", newHeartRate.heartRate)
    console.log("oldHeartRate", oldHeartRate.heartRate)
    if(newHeartRate.heartRate > oldHeartRate.heartRate && newHeartRate.heartRate >= 120)
    {
        alert('your heart rate is so high brathe slow....')
    }
})
</script>
 
<style scoped>
 
</style>