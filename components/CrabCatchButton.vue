<script setup lang="ts">
const crabs:Ref = useState('crabs');
const catchingPower:Ref = useState('catchingPower');
const coolDownTime:number = 1000;
let canCatch:boolean = true;
let crabCatchMessage:Ref = ref("Go catch some crabs!")
const criticalPower = computed( () => {
    return catchingPower.value * 3;
});
const sucessMin:number = .3;
const criticalSuccessMin:number = .95;
let progressState:Ref = ref("initial");
function resetTimer(){
    canCatch = true;
    progressState.value = "initial";
    let crabPower:number = Math.random();
    if(crabPower >= criticalSuccessMin){
        crabs.value += criticalPower.value;
        crabCatchMessage.value = "You caught " + criticalPower.value + " crabs!"
    }
    else if(crabPower >= sucessMin){
        crabs.value += catchingPower.value;
        crabCatchMessage.value = "You caught " + catchingPower.value + " crabs"
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
<div><ProgressBar :animation-state="progressState" :animation-time="coolDownTime"/></div>
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