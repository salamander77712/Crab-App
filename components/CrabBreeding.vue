<script setup lang="ts">
const crabs:Ref = useState('crabs');
const growthRate:number = 0.01;
const growthPeriod:number = 1000;
let message:Ref = ref("Your crabs are breeding...");
let progressState:Ref = ref("running");
function breed(){
  if(crabs.value >= 2){
    let newCrabs:number = crabs.value * growthRate;
    let newCrabsRounded:number = Math.floor(newCrabs);
    let fractionalGrowth:number = newCrabs - newCrabsRounded;
    if(Math.random() <= fractionalGrowth){
      newCrabsRounded++;
    }
    crabs.value += newCrabsRounded;
    if(newCrabsRounded > 0){
      message.value = "Your crabs made " + newCrabsRounded + " new crabs";
    }
    else{
      message.value = "Your crabs failed to make any new crabs...";
    }
  }
}
onMounted(()=> setInterval(breed, growthPeriod));
</script>

<template>
  <ProgressBar :animation-state="progressState" :animation-time="growthPeriod" />
  <p>{{ message }}</p>
</template>

<style scoped>
button {
    border-radius: 15px;
    margin-bottom: 5px;;
    border-width: 1px;
}
</style>