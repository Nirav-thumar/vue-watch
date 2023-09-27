<template>
<div>{{state.heartRate}}</div>
<button @click="state.heartRate += 5">increase</button>
<button @click="state.heartRate -= 5">decrease</button>
</template>
 
 
<script setup>
 
import { ref, reactive, computed, watch  } from 'vue'
 
 const state= reactive({heartRate:85})

watch(()=>state.heartRate,(newHeartRate,oldHeartRate)=>{
    if(newHeartRate > oldHeartRate && newHeartRate >= 120)
    {
        alert('your heart rate is so high brathe slow....')
    }
})
</script>
 
<style scoped>
 
</style>