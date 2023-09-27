<template>
<div v-if="heartRate > 0">Heart Rate : {{heartRate}}</div>
<div v-else>sorry you are to late</div>
<button @click="heartRate += 5">increase</button>
<button @click="heartRate -= 5">decrease</button>
</template>
 
 
 
<script setup>
//  Flush what did : before component update watcher callback execute
// if you want to callback call after component update then its require to flush

// default : pre   1)watcher 2) onBeforeUpdate  3) onUpdated 
// default : post  1)onBeforeUpdate  2) watcher  3) onUpdated 


import { ref, reactive, computed, watch ,onBeforeUpdate ,onUpdated } from 'vue'
 
const heartRate = ref(85);

onBeforeUpdate(()=>{
    console.log("onBefore update call")
})
onUpdated(()=>{
    console.log("onUpdated call")
})
watch(heartRate,(newHeartRate,oldHeartRate)=>{
 console.log("watcher callback called")
  console.log('newHeartRate : ',newHeartRate)  
  console.log('oldHeartRate : ',oldHeartRate)  
  
})

</script>
 
<style scoped>
 
</style>