<template>
<div v-if="heartRate > 0">Heart Rate {{ heartRate}} and fear {{fear}} </div>
<div v-else> sorry for your hear rate</div>
<button @click="increaseHeartFear">increase</button>
<button @click="decreaseHeartFear">decrease</button>
</template>
 
 
 
<script setup>
 
import { ref, reactive, computed ,watch } from 'vue'
 const heartRate = ref(85)
 const fear = ref(0)

 watch([heartRate,fear],(newValue,oldValue)=>{
    console.log('newValue for hearRate ',newValue[0]);
    console.log('newValue for fear ',newValue[1]);
    console.log('oldValue for hearRate',oldValue[0]);
    console.log('newValue for hearRate',oldValue[1]);

    if( newValue[0] > oldValue[0] && newValue[0] >= 120){
        alert('so high breathe smoothly..')
    }
 })

 function increaseHeartFear(){
    heartRate.value += 5;
    fear.value +=  10
 }
  function decreaseHeartFear(){
    heartRate.value -= 5;
    fear.value -=  10
 }
</script>
 
<style scoped>
 
</style>