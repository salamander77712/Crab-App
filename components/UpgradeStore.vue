<script setup lang="ts">
const money:Ref = useState('money');
const breedingUnlocked:Ref = useState('breedingUnlocked');
function unlockBreeding () {
    if(money.value >= 5){
        breedingUnlocked.value = true;
        money.value -= 5;
    }
}
</script>

<template>
    <button v-if="!breedingUnlocked" @click="unlockBreeding">Unlock Crab Breeding ($5)</button>
</template>

<style scoped>
button {
    border-radius: 15px;
    margin-bottom: 5px;;
    border-width: 1px;
}
</style>