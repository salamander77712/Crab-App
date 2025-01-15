<script setup lang="ts">
const crabs:Ref = useState('crabs')
const coolDownTime:number = 1000;
let canCatch:Boolean = true;
let crabCatchMessage:Ref = ref("Go catch some crabs!")
const successValue:number = 1;
const criticalSuccessValue:number = 3;
const sucessMin:number = .3;
const criticalSuccessMin:number = .95;
function resetTimer(){
    canCatch = true;
}
function catchCrabs(){
    if(canCatch){
        canCatch = false;
        setTimeout(resetTimer, coolDownTime)
        let crabPower:number = Math.random();
        if(crabPower >= criticalSuccessMin){
            crabs.value += criticalSuccessValue;
            crabCatchMessage.value = "You caught " + criticalSuccessValue + " crabs"
        }
        else if(crabPower >= sucessMin){
            crabs.value += successValue;
            crabCatchMessage.value = "You caught " + successValue + " crabs"
        }
        else{
            crabCatchMessage.value = "You failed to catch any crabs..."
        }
    }
}
</script>

<template>
<button @click="catchCrabs">Catch Crabs</button>
<br>
<p>{{ crabCatchMessage }}</p>
</template>

<style scoped>

</style>