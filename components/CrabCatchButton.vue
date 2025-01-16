<script setup lang="ts">
const crabs:Ref = useState('crabs')
const coolDownTime:number = 1000;
let canCatch:boolean = true;
let crabCatchMessage:Ref = ref("Go catch some crabs!")
const successValue:number = 1;
const criticalSuccessValue:number = 3;
const sucessMin:number = .3;
const criticalSuccessMin:number = .95;
let progressState:Ref = ref("initial");
function resetTimer(){
    canCatch = true;
    progressState.value = "initial";
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
function catchCrabs(){
    if(canCatch){
        canCatch = false;
        setTimeout(resetTimer, coolDownTime)
        progressState.value = "running";
    }
}
</script>

<template>
<button @click="catchCrabs">Catch Crabs</button>
<div><ProgressBar :animationState="progressState"/></div>
<p>{{ crabCatchMessage }}</p>
</template>

<style scoped>
div {
    width: 100px;
}
button {
    border-radius: 15px;
    margin-bottom: 5px;;
    border-width: 1px;
}
</style>